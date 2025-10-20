---
title: SMSHook
deprecated: false
hidden: false
metadata:
  robots: index
---
<br />

#### SMSHook mechanism

When users submit SMS or voice  request to SendCloud, 「request result」 will be simultaneously returned to users; SMS or voice 「sending result」 and 「results of other event」 will be asynchronously returned to users via SMSHook.

* SendCloud provides several events for users to choose
* When an event occurs, the URL set by SendCloud will be triggered to send data (POST)
* Users parse the event and data for follow-up processing after receiving the data

Supported events are as below:

| Events                            | Triggering Conditions                   |
| :-------------------------------- | :-------------------------------------- |
| request (request)                 | request was successful                  |
| deliver (deliver)                 | delivered                               |
| process failure(workererror)      | processing failed                       |
| delivery failure(delivererror)    | delivering failed                       |
| Template approval(templateVerify) | Approval result message of SMS template |

Usage Method:

* Users write HTTP service to process events, parse data and release URL
* Choose interested events in `【SMS and Voice SMS】-【Settings】-【SMSHook】` and configure URL

`Note: SendCloud will test users’ URL to ensure the HTTP service responds to get | post request, and the returned HTTP status code is 200`

<br />

#### Signature Verification

To ensure that the message is sent from SendCloud, you can choose to verify the source of the POST data. (You can also parse POST data without authentication).

Authentication method is as below:

* Acquire `APP KEY` in `【SMS and Voice SMS】- 【Delivery Settings】-【SMSHook】`.
* Parse `token`, `timestamp` and `signature` in POST data.
* Generate signature with `APP KEY`, `token` and `timestamp`; check it with `signature` in POST data (signature algorithm: [SHA256](http://en.wikipedia.org/wiki/SHA-2))

**Python code example**

```
import hashlib, hmac
def verify(appkey, token, timestamp, signature):
    return signature == hmac.new(
        key=appkey,
        msg='{}{}'.format(timestamp, token),
        digestmod=hashlib.sha256).hexdigest()
```

**Java code example** (dependent [apache codec](http://commons.apache.org/proper/commons-codec/download_codec.cgi))

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

#### Event Description

SMSHook now supports request, deliver, process failure, send failure and reply.

** Request ( request )**

Parameter Description

| parameter  | type   | description                    |
| :--------- | :----- | :----------------------------- |
| event      | string | event type: ”request”          |
| eventType  | int    | event type code:1              |
| message    | string | request                        |
| userId     | int    | user ID                        |
| smsUser    | string | smsUser                        |
| smsIds     | list   | SMS (Voice SMS) IDs            |
| templateId | int    | template ID                    |
| phones     | list   | phone numbers                  |
| msgCount   | int    | Number of SMS                  |
| timestamp  | long   | timestamp                      |
| token      | string | random string of 50 characters |
| signature  | string | signature string               |
| customArgs | string | User defined custom args       |

POST data example

```
{
"signature":"1ff237043487aeb4dc1b21c22b5ead9e4df94a31a3afa0ad53238eb38c2cbeea",
"phones":"[\"13888888888\"]",
"eventType":1,
"templateId":29999,
"message":"request",
"userId":19999,
"smsUser":"App",
"smsIds":"[\"1652150994014_9373_14466_36735_99drnc$13888888888\"]",
"token":"VDymF6ihuJkKZjHiJZkLKGmY6q9qAQ2WGopLh7mBsDeAO6GKV5",
"customArgs":{},
"event":"request",
"timestamp":1652150994087
}
```

** Deliver ( deliver )**

<br />

Parameter Description

| parameter    | type   | description                    |
| :----------- | :----- | :----------------------------- |
| event        | string | event type: ”deliver”          |
| eventType    | int    | event type code:2              |
| message      | string | Successfully delivered         |
| userId       | int    | user ID                        |
| smsUser      | string | smsUser                        |
| smsId        | string | SMS (Voice SMS) IDs            |
| templateId   | int    | template ID                    |
| phone        | string | phone numbers                  |
| timestamp    | long   | timestamp                      |
| token        | string | random string of 50 characters |
| signature    | string | signature string               |
| customArgs   | string | User defined custom args       |
| msgCount     | int    | Number of SMS                  |
| outboundTime | string | Channel time                   |
| receiptTime  | string | Receipt time                   |

POST data example

```
{
"msgType":0,
"signature":"9ca96fa072bfa048969aa0cb7bf7baf64100234640a1b9793cca1a419afb9cb8",
"eventType":2,
"templateId":29999,
"message":"Successfully delivered",
"userId":19999,
"smsUser":"APP",
"token":"4mRG9lGhVb3jZhOMnksFPBtX1OLDMNZMfXTFHkFd9eybfdRiHM",
"smsId":"1652117371408_19999_376_4631_qrwnpq$13888888888",
"receiptTime":"2022-05-10 01:29:50",
"phone":"13888888888",
"customArgs":{},
"event":"deliver",
"outboundTime":"2022-05-10 01:29:31",
"timestamp":1652117390000
}
```

** Process failure ( workererror)**

Parameter Description

| parameter     | type   | description                      |
| :------------ | :----- | :------------------------------- |
| event         | string | event type:"workererror"         |
| eventType     | int    | event type code:4                |
| message       | string | error message                    |
| encodeMessage | string | error message of base64 encoding |
| userId        | int    | user ID                          |
| statusCode    | int    | error code                       |
| smsUser       | string | smsUser                          |
| smsId         | string | SMS (Voice SMS) IDs              |
| templateId    | int    | template ID                      |
| phone         | string | phone numbers                    |
| timestamp     | long   | timestamp                        |
| token         | string | random string of 50 characters   |
| signature     | string | signature string                 |
| customArgs    | string | User defined custom args         |
| msgCount      | int    | Number of SMS                    |
| outboundTime  | string | Channel time                     |

POST data example

```
{
"outboundTime":"2022-05-10 00:00:54",
"msgType":0,
"signature":"8a3a030169decf0134010b8d7443cfbbf16b08a6aee524291706dacfb127be95",
"eventType":4,
"templateId":-3,
"message":"smsworker:address in unsubscribe list(取消订阅)",
"userId":19999,
"smsUser":"APP",
"token":"sGfR3yMheseXBxkPt3NnIuDQK5aYdzbfyUO8i0oz6IJI07pNHj",
"smsId":"1652112054796_19999_167_-3_ty8pqn$13888888888",
"encodeMessage":"c21zd29ya2VyOmFkZHJlc3MgaW4gdW5zdWJzY3JpYmUgbGlzdCjlj5bmtojorqLpmIUp",
"phone":"13888888888",
"customArgs":{},
"event":"workererror",
"timestamp":1652112054846,
"statusCode":430
}
```

** Send failure ( delivererror)**

Parameter Description

| parameter     | type   | description                      |
| :------------ | :----- | :------------------------------- |
| event         | string | event type:"delivererror"        |
| eventType     | int    | event type code:5                |
| message       | string | error message                    |
| encodeMessage | string | error message of base64 encoding |
| userId        | int    | user ID                          |
| statusCode    | int    | error code                       |
| smsUser       | string | smsUser                          |
| smsId         | string | SMS (Voice SMS) IDs              |
| templateId    | int    | template ID                      |
| phone         | string | phone numbers                    |
| timestamp     | long   | timestamp                        |
| token         | string | random string of 50 characters   |
| signature     | string | signature string                 |
| customArgs    | string | User defined custom args         |
| msgCount      | int    | Number of SMS                    |
| outboundTime  | string | Channel time                     |
| receiptTime   | string | Receipt time                     |

POST data example

```
{
"outboundTime":"2022-05-10 09:31:12",
"msgType":0,
"signature":"785370449703a5dfca4cb773a5a266f6be1db8bdbe713b8ce74ca572f9788a7a",
"eventType":5,
"templateId":29999,
"message":"REJECTD(其他)",
"userId":19999,
"smsUser":"APP",
"token":"MTha34FTrBRBmJXdZK4qVCqRxh8N4IlAJlM11sd1FSfCk9jmo3",
"smsId":"1652146271665_19999_8755_3883_37059m$13888888888",
"receiptTime":"2022-05-10 09:31:17",
"encodeMessage":"UkVKRUNURCjlhbbku5Yp",
"customArgs":{},
"event":"delivererror",
"timestamp":1652146277000,
"statusCode":590
}
```

** Template approval (templateVerify)**

| parameter     | type   | description                                                                         |
| :------------ | :----- | :---------------------------------------------------------------------------------- |
| event         | string | event type:"templateVerify"                                                         |
| eventType     | int    | event type code:8                                                                   |
| userId        | int    | user ID                                                                             |
| templateId    | int    | template ID                                                                         |
| name          | string | template name                                                                       |
| timestamp     | long   | timestamp                                                                           |
| token         | string | random string of 50 characters                                                      |
| signature     | string | signature string                                                                    |
| verfiyResult  | int    | Review Result: 0 under review, 1 approved, -1 rejected                              |
| verfiyComment | string | Review comments. Verification comments are provided when the review is not approved |

POST data example

```
{
    "msgType":0,
    "signature":"b80266d81f527c1ce870ba36c4c9e79fd9725c5a7c943577a25d8116aa67c927",
    "verfiyResult":1,
    "name":"Thank you for visiting the Shanghai Auto Show booth",
    "eventType":8,
    "templateId":6255,
    "event":"templateVerify",
    "userId":102,
    "token":"M1dgqmmOsM3BC9dCqBsMjtDh6I5jYwXngPEtcVV9v8XoplF1VQ",
    "timestamp":1646628597226
}

```
