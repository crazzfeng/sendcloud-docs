---
title: SMSHook
excerpt: SMS event will be asynchronously returned to users via SMSHook.
deprecated: false
hidden: false
metadata:
  robots: index
---
<br />

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
