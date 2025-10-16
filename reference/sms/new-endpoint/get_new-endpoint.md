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
https://api2.sendcloud.net/smsapi/send
```

**Format of returned data**

```
json
```

**HTTP Request Method**

```
POST    
```

| parameter     | type   | required or not | description                                                                                                                                                         |
| :------------ | :----- | :-------------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| smsUser       | string | yes             | sms user                                                                                                                                                            |
| smsKey        | string | yes             | sms key                                                                                                                                                             |
| templateId    | int    | yes             | template ID                                                                                                                                                         |
| phone         | string | yes             | phone numbers of recipients, separated by commas; the amount cannot be more 2,000 each time. Contact list will be suggested when the recipients are more than 2000. |
| vars          | string | no              | json string of substitution variable                                                                                                                                |
| senderID      | string | no              | Sender ID                                                                                                                                                           |
| sendRequestId | string | no              | supports up to 128 characters, multiple requests with the same sendRequestId within 1 hour will only be processed for the first time                                |
| timestamp     | string | no              | UNIX timestamp                                                                                                                                                      |
| customArgs    | string | no              | The value is in JSON format, and the maximum character length is 128, for example: `{"key1": "value1", "key2": "Value2"}`                                           |

_Sample of vars format:_

```
{"name": "lucy"} or {"%money%": "100"}
```

`Note`:

1. Variables in SMS template will be replaced by parameters in vars. All recipients users will receive the same replaced content. If the parameter content submitted by each mobile phone number is different, the interface needs to be called multiple times.Parameters in vars may contain special characters, marked with `urlencode`.

2. Value of the variable is formatted with string and cannot be longer than 32 characters. HTTP links are not allowed in variables.

3. `urlencode` is not required when generating signature but calling API.
