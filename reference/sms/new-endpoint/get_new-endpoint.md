---
title: send sms
excerpt: Send a SMS template to one or more users
api:
  file: send.json
  operationId: get_new-endpoint
hidden: false
---
<br />

**URL**

```
https://api2.sendcloud.net/api/sms/send
```

**Format of returned data**

```
json
```

**HTTP Request Method**

```bash
POST    
```

| parameter     | type   | required or not | description                                                                                                                                                         |
| :------------ | :----- | :-------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| smsUser       | string | yes             | smsUser                                                                                                                                                             |
| templateId    | int    | yes             | template ID                                                                                                                                                         |
| phone         | string | yes             | phone numbers of recipients, separated by commas; the amount cannot be more 2,000 each time. Contact list will be suggested when the recipients are more than 2000. |
| vars          | string | no              | json string of substitution variable                                                                                                                                |
| sendRequestId | string | no              | supports up to 128 characters, multiple requests with the same sendRequestId within 1 hour will only be processed for the first time                                |
| signature     | string | yes             | signature, validity verification                                                                                                                                    |
| timestamp     | string | no              | UNIX timestamp                                                                                                                                                      |
| tag           | string | no              | The value is in JSON format, and the maximum character length is 128, for example: `{"key1": "value1", "key2": "Value2"}`                                           |

<br />
