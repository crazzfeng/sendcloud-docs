---
title: Send SMS Message
excerpt: Send a SMS template to one or more users
api:
  file: send.json
  operationId: get_new-endpoint
hidden: false
link:
  new_tab: false
---
# Send SMS Message

Send an SMS template to one or more users.

## API Endpoint

**URL**
```
https://api2.sendcloud.net/smsapi/send
```

**Response Format**
```
json
```

**HTTP Request Method**
```
POST    
```

## Parameters

| Parameter     | Type   | Required | Description                                                                                                                                                         |
| :------------ | :----- | :------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| smsUser       | string | Yes      | SMS user                                                                                                                                                            |
| smsKey        | string | Yes      | SMS key                                                                                                                                                             |
| templateId    | int    | Yes      | Template ID                                                                                                                                                         |
| phone         | string | Yes      | Phone numbers of recipients, separated by commas. Maximum of 2,000 recipients per request. For more than 2,000 recipients, consider using a contact list instead. |
| vars          | string | No       | JSON string containing substitution variables                                                                                                                       |
| senderID      | string | No       | Sender ID                                                                                                                                                           |
| sendRequestId | string | No       | Unique identifier (up to 128 characters). Multiple requests with the same sendRequestId within 1 hour will only process the first request                         |
| timestamp     | string | No       | UNIX timestamp                                                                                                                                                      |
| customArgs    | string | No       | Custom arguments in JSON format with a maximum length of 128 characters. Example: `{"key1": "value1", "key2": "value2"}`                                          |

## Variable Format Examples

**Sample vars format:**
```json
{"name": "lucy"}
```

**Or with percentage placeholders:**
```json
{"%money%": "100"}
```

## Important Notes

1. **Variable Replacement**: Variables in the SMS template will be replaced by parameters in the `vars` field. All recipients will receive the same replaced content. If different content is needed for each phone number, make separate API calls for each recipient. Parameters in `vars` may contain special characters and should be URL-encoded.

2. **Variable Constraints**: Variable values must be strings with a maximum length of 32 characters. HTTP links are not allowed in variables.

3. **URL Encoding**: URL encoding (`urlencode`) is not required when generating the signature, but it is required when calling the API.