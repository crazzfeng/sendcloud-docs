---
title: SMSHook
excerpt: SMS event will be asynchronously returned to users via SMSHook.
deprecated: false
hidden: false
metadata:
  robots: index
---
## SMSHook

#### SMSHook mechanism

When users submit SMS or voice  request to SendCloud, 「request result」 will be simultaneously returned to users; SMS or voice 「sending result」 and 「results of other event」 will be asynchronously returned to users via SMSHook.

* SendCloud provides several events for users to choose
  * When an event occurs, the URL set by SendCloud will be triggered to send data (POST)
    * Users parse the event and data for follow-up processing after receiving the data

      Supported events are as below:

      | Events                            | Triggering Conditions                      |
      | :-------------------------------- | :----------------------------------------- |
      | request (request)                 | request was successful                     |
      | deliver (deliver)                 | delivered                                  |
      | process failure(workererror)      | processing failed                          |
      | delivery failure(delivererror)    | delivering failed                          |
      | click link(click)                 | User clicks the link                       |
      | reply(reply)                      | reply (SMS only)                           |
      | SMS uplink(sms_mo)                | Users actively submit SMS to the interface |
      | Template approval(templateVerify) | Approval result message of SMS template    |

      Usage Method:

      * Users write HTTP service to process events, parse data and release URL
        * Choose interested events in `【SMS and Voice SMS】-【Settings】-【SMSHook】` and configure URL

          `Note: SendCloud will test users’ URL to ensure the HTTP service responds to get | post request, and the returned HTTP status code is 200`

#### Signature Verification

To ensure that the message is sent from SendCloud, you can choose to verify the source of the POST data. (You can also parse POST data without authentication).

Authentication method is as below:

* Acquire `APP KEY` in `【SMS and Voice SMS】- 【Delivery Settings】-【SMSHook】`.
  * Parse `token`, `timestamp` and `signature` in POST data.
    * Generate signature with `APP KEY`, `token` and `timestamp`; check it with `signature` in POST data (signature algorithm: [SHA256](http://en.wikipedia.org/wiki/SHA-2) )

      **Python code example**

      ```
      import hashlib, hmac
      def verify(appkey, token, timestamp, signature):
          return signature == hmac.new(
              key=appkey,
              msg='{}{}'.format(timestamp, token),
              digestmod=hashlib.sha256).hexdigest()
      ```

      **Java code example** (dependent [apache codec](http://commons.apache.org/proper/commons-codec/download_codec.cgi) )

      ```
      import javax.crypto.Mac;
      import javax.crypto.spec.SecretKeySpec;

      import org.apache.commons.codec.binary.Hex;

      public boolean verify(String appkey, String token, long timestamp,
                  String signature) throws NoSuchAlgorithmException, InvalidKeyException {
          Mac sha256HMAC = Mac.getInstance("HmacSHA256");
          SecretKeySpec secretKey = new SecretKeySpec(appkey.getBytes(),"HmacSHA256");
          sha256HMAC.init(secretKey);
          StringBuffer buf = new StringBuffer();
          buf.append(timestamp).append(token);
          String signatureCal = new String(Hex.encodeHex(sha256HMAC.doFinal(buf
                  .toString().getBytes())));
          return signatureCal.equals(signature);
      }

      ```

      **php code example**

      ```
      function verify($appkey,$token,$timestamp,$signature){
              $hash="sha256";
                  $result=hash_hmac($hash,$timestamp.$token,$appkey);
                      return strcmp($result,$signature)==0?1:0;
      }
      ```

      **Retry mechanism**

      If encountering URL access errors or timeouts, SendCloud will retry up to 7 times The fastest time interval for each retry is 3 minutes, 10 minutes, 30 minutes, 1 hour, 6 hours, 12 hours, 24 hours. This means that you have enough time to fix the URL before the message is lost.

      If the retry count is exceeded, SendCloud will save the message for 15 days. If necessary, please contact us for a re push.

      You need to return HTTP Code 200 within 3 seconds for each event handling.

<br />

#### Event Description

SMSHook now supports request, deliver, process failure, send failure and reply.

** Request ( request )**

Parameter Description

| parameter  | type   | description                                                  |
| :--------- | :----- | :----------------------------------------------------------- |
| event      | string | event type: ”request”                                        |
| eventType  | int    | event type code:1                                            |
| message    | string | SMS content                                                  |
| smsUser    | string | smsUser                                                      |
| smsIds     | list   | SMS (Voice SMS) IDs                                          |
| templateId | int    | template ID                                                  |
| phones     | list   | phone numbers                                                |
| timestamp  | long   | timestamp                                                    |
| token      | string | random string of 50 characters                               |
| signature  | string | signature string                                             |
| userId     | int    | user ID                                                      |
| labelId    | int    | reserved, temporarily out of use                             |
| tag        | string | User defined tag                                             |
| msgCount   | int    | Number of SMS                                                |
| msgType    | int    | "0"SMS, "1"MMS, "2"International SMS, "3"International Voice |
| smsType    | int    | "0"Verification Code, "1"Notice, "2"Marketing                |

POST data example

```
{
"msgType":0,
"signature":"1ff237043487aeb4dc1b21c22b5ead9e4df94a31a3afa0ad53238eb38c2cbeea",
"phones":"[\"13888888888\"]",
"eventType":1,
"templateId":29999,
"message":"request",
"userId":19999,
"smsUser":"App",
"smsIds":"[\"1652150994014_9373_14466_36735_99drnc$13888888888\"]",
"token":"VDymF6ihuJkKZjHiJZkLKGmY6q9qAQ2WGopLh7mBsDeAO6GKV5",
"labelId":0,
"smsType":0,
"tag":0,
"event":"request",
"timestamp":1652150994087
}
```
