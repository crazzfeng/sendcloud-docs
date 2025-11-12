---
title: Getting Started
excerpt: >-
  Complete guide to setting up your API documentation dashboard and helping
  users make their first successful API call.
api:
  file: send.json
  operationId: get_new-endpoint
api_config: getting-started
hidden: true
icon: icon-book1
link:
  new_tab: false
---
# AuroraSendCloud API Quickstart

Get started with AuroraSendCloud's powerful APIs to send emails, manage contacts, track performance, and integrate seamlessly with your applications. Follow this step-by-step guide to make your first API call in minutes—with clear distinctions between multi-region email APIs and the single-region SMS API.

## Prerequisites

Before you begin, ensure you have:

* An active AuroraSendCloud account (sign up at [aurorasendcloud.com](https://www.aurorasendcloud.com/))
* Your **API Key** and **API User** (found in your account's [API Key Management](https://www.aurorasendcloud.com/web/#/api/apiuser) page)
* A supported HTTP client (e.g., cURL, Postman, Python's `requests` library)
* Confirm your account's **region** (Singapore, US, or Hong Kong) for email API access (not required for SMS API)

## 1. API Base URLs (By Service Type)

### Email & Core APIs (Multi-Region)

Choose the base URL that matches your account's region for email, contact management, templates, and other core services. All requests must use **HTTPS**, and responses are in **JSON** format.

| Region             | Base URL                              | Coverage                                  |
| ------------------ | ------------------------------------- | ----------------------------------------- |
| Singapore (SG)     | `https://api.aurorasendcloud.com/`    | Default region for APAC users             |
| United States (US) | `https://api-us.aurorasendcloud.com/` | For North American users and services     |
| Hong Kong (HK)     | `https://api-hk.aurorasendcloud.com/` | For Greater China and nearby APAC regions |

> ℹ️ **Note**: Your account is tied to a specific region during sign-up. Using a non-matching base URL for email/core APIs will cause authentication failures or data inconsistencies. Confirm your region in account settings.

### SMS API (Single Region)

The SMS API uses a **unified global base URL** (no regional endpoints required):

* **Base URL**: `https://api.aurorasendcloud.com/`
* All SMS requests must use this URL regardless of your account's region
* Authentication and response format are consistent with email/core APIs

## 2. Authentication

Authenticate all API requests (email, SMS, core services) by including your credentials as **request parameters**:

* `api_user`: Your AuroraSendCloud API username
* `api_key`: Your AuroraSendCloud API key

> ⚠️ **Critical Security Note**: Never expose your API credentials in client-side code (e.g., browsers, mobile apps). Restrict access to your API key, rotate it regularly via the API Key Management page, and avoid hardcoding credentials in source code.

## 3. Making Your First API Call

### Example: Send an Email

<Tabs>
  <Tab title="cURL">
    ```bash
    curl -X POST "https://api.aurorasendcloud.com/mail/send" \
      -d "api_user=YOUR_API_USER" \
      -d "api_key=YOUR_API_KEY" \
      -d "from=sender@yourdomain.com" \
      -d "fromName=Your Name" \
      -d "to=recipient@example.com" \
      -d "subject=Test Email" \
      -d "html=<h1>Hello from AuroraSendCloud!</h1>"
    ```
  </Tab>

  <Tab title="Python">
    ```python
    import requests

    url = "https://api.aurorasendcloud.com/mail/send"
    data = {
        "api_user": "YOUR_API_USER",
        "api_key": "YOUR_API_KEY",
        "from": "sender@yourdomain.com",
        "fromName": "Your Name",
        "to": "recipient@example.com",
        "subject": "Test Email",
        "html": "<h1>Hello from AuroraSendCloud!</h1>"
    }

    response = requests.post(url, data=data)
    print(response.json())
    ```
  </Tab>

  <Tab title="Node.js">
    ```javascript
    const axios = require('axios');

    const data = {
      api_user: 'YOUR_API_USER',
      api_key: 'YOUR_API_KEY',
      from: 'sender@yourdomain.com',
      fromName: 'Your Name',
      to: 'recipient@example.com',
      subject: 'Test Email',
      html: '<h1>Hello from AuroraSendCloud!</h1>'
    };

    axios.post('https://api.aurorasendcloud.com/mail/send', data)
      .then(response => console.log(response.data))
      .catch(error => console.error(error));
    ```
  </Tab>
</Tabs>

### Example: Send an SMS

<Tabs>
  <Tab title="cURL">
    ```bash
    curl -X POST "https://api.aurorasendcloud.com/smsapi/send" \
      -d "smsUser=YOUR_SMS_USER" \
      -d "smsKey=YOUR_SMS_KEY" \
      -d "templateId=123456" \
      -d "phone=+1234567890" \
      -d "vars={\"code\":\"123456\"}"
    ```
  </Tab>

  <Tab title="Python">
    ```python
    import requests

    url = "https://api.aurorasendcloud.com/smsapi/send"
    data = {
        "smsUser": "YOUR_SMS_USER",
        "smsKey": "YOUR_SMS_KEY",
        "templateId": "123456",
        "phone": "+1234567890",
        "vars": '{"code":"123456"}'
    }

    response = requests.post(url, data=data)
    print(response.json())
    ```
  </Tab>
</Tabs>

## 4. API Response Format

All API responses (email and SMS) follow a consistent JSON structure:

### Success Example (Request Successful)

```json
{
  "result": true,
  "statusCode": 200,
  "message": "request was successful",
  "info": {}
}
```

### Success Example (Data Acquisition)

```json
{
  "statusCode": 200,
  "info": {
    "data": {
      "gmtCreated": "2015-10-19 15:39:27",
      "gmtUpdated": "2015-10-19 15:39:27",
      "labelId": 123,
      "labelName": "test"
    }
  },
  "message": "request was successful",
  "result": true
}
```

### Error Example (Authentication Failed)

```json
{
  "result": false,
  "statusCode": 40005,
  "message": "authentication failed",
  "info": {}
}
```

#### Response Field Definitions:

* `result`: Boolean indicating if the request succeeded (`true`) or failed (`false`)
* `statusCode`: Numeric code representing the request status (see complete list below)
* `message`: Description of the status code (for debugging and user feedback)
* `info`: Contains response data (e.g., SMS/email IDs, retrieved records) on success; empty on failure

## 5. Complete API Return Codes

The following table lists all return codes and their meanings (applicable to both email and SMS APIs):

<Accordion title="General & Validation Errors" icon="exclamation-triangle">
  | Status Code | Meaning                                                        |
  | ----------- | -------------------------------------------------------------- |
  | 200         | Request was successful                                         |
  | 40001       | `start` cannot be empty                                        |
  | 40002       | Invalid `start` parameter                                      |
  | 40003       | `limit` cannot be empty                                        |
  | 40004       | Invalid `limit` parameter                                      |
  | 40005       | Authentication failed (check `api_user`/`api_key`)             |
  | 40006       | Invalid `days` format, it must be an integer greater than zero |
  | 40007       | Invalid `startDate` format (e.g. "2013-03-19")                 |
  | 40008       | Invalid `endDate` format (e.g. "2013-03-19")                   |
  | 40009       | `labelIdList` cannot be empty                                  |
  | 40010       | `apiUserList` cannot be empty                                  |
  | 40011       | Email cannot be empty                                          |
  | 40012       | Invalid email format                                           |
  | 40013       | `domainList` cannot be empty                                   |
  | 40014       | Label ID cannot be empty                                       |
  | 40015       | Invalid label ID format                                        |
  | 40016       | Invalid `apiUserList` format                                   |
  | 40017       | Invalid format of aggregation parameters                       |
</Accordion>

<Accordion title="Label Management" icon="tag">
  | Status Code | Meaning                                            |
  | ----------- | -------------------------------------------------- |
  | 40100       | Label was successfully created                     |
  | 40101       | Failed to create label                             |
  | 40102       | Label ID cannot be empty                           |
  | 40103       | Invalid label ID                                   |
  | 40104       | Label name cannot be empty                         |
  | 40105       | Label name should be 1-255 characters              |
  | 40106       | The label corresponding to label ID does not exist |
  | 40107       | Label was successfully deleted                     |
  | 40108       | Failed to delete label                             |
  | 40109       | Label was successfully updated                     |
  | 40110       | Failed to update label                             |
  | 40111       | Query cannot be empty                              |
  | 40112       | Query should be 1-255 characters                   |
  | 40113       | Label name already exists                          |
</Accordion>

<Accordion title="Template Management" icon="file-alt">
  | Status Code | Meaning                                                                  |
  | ----------- | ------------------------------------------------------------------------ |
  | 40201       | `invokeName` cannot be empty                                             |
  | 40202       | Invalid `invokeName` format                                              |
  | 40203       | Template type cannot be empty                                            |
  | 40204       | Invalid template type, it can only be 0 or 1                             |
  | 40205       | `templateStat` cannot be empty                                           |
  | 40206       | Invalid `templateStat`, it can only be one of -1, -2, 1, 0               |
  | 40207       | Name cannot be empty                                                     |
  | 40208       | Invalid name format                                                      |
  | 40209       | Subject cannot be empty                                                  |
  | 40210       | Invalid subject format                                                   |
  | 40211       | HTML cannot be empty                                                     |
  | 40212       | Invalid HTML format                                                      |
  | 40213       | Text cannot be empty                                                     |
  | 40214       | Invalid text format                                                      |
  | 40215       | Failed to create template                                                |
  | 40216       | The template corresponding to `invokeName` does not exist                |
  | 40217       | Failed to delete template                                                |
  | 40218       | Failed to update template                                                |
  | 40219       | User can have no more than 50 templates                                  |
  | 40220       | `invokeName` already exists                                              |
  | 40221       | `isSubmitAudit` cannot be empty                                          |
  | 40222       | Invalid `isSubmitAudit` format                                           |
  | 40223       | Template is pending approval and cannot be modified                      |
  | 40224       | Cancel cannot be empty                                                   |
  | 40225       | Invalid cancel format                                                    |
  | 40226       | Template is pending approval, do not submit again                        |
  | 40227       | Template has been approved, do not submit again                          |
  | 40228       | Template not approved, do not withdraw the approval request              |
  | 40229       | Template not submitted for approval, unable to withdraw approval request |
</Accordion>

<Accordion title="User & Address Management" icon="users">
  | Status Code | Meaning                                                       |
  | ----------- | ------------------------------------------------------------- |
  | 40301       | User does not exist                                           |
  | 40401       | Unsubscribe record was successfully created                   |
  | 40402       | Failed to create unsubscribe record                           |
  | 40403       | Unsubscribe record was successfully deleted                   |
  | 40404       | Failed to delete unsubscribe record                           |
  | 40501       | Name cannot be empty                                          |
  | 40502       | Address list name should be 1-48 characters                   |
  | 40503       | Address cannot be empty                                       |
  | 40504       | Address list alias should be 1-48 characters                  |
  | 40505       | Address list alias already exists                             |
  | 40506       | Desc cannot be empty                                          |
  | 40507       | Address list description should be 1-250 characters           |
  | 40508       | Failed to create address list                                 |
  | 40509       | `newAddress` cannot be empty                                  |
  | 40510       | New address list alias should be 1-48 characters              |
  | 40511       | Invalid address parameters                                    |
  | 40512       | Members cannot be empty                                       |
  | 40513       | Member address should be 1-48 characters                      |
  | 40514       | Number of member address should be more than 0                |
  | 40515       | Number of member address should be no more than 1000          |
  | 40516       | Failed to add member                                          |
  | 40517       | Address list does not belong to the user                      |
  | 40518       | Member address does not conform to the specification          |
  | 40519       | Failed to delete member                                       |
  | 40520       | Vars cannot be empty                                          |
  | 40521       | Variables in vars parameter are not equal to member addresses |
  | 40522       | Vars parameter does not adhere to JSON string syntax          |
</Accordion>

<Accordion title="Bounce & Webhook Management" icon="server">
  | Status Code | Meaning                                            |
  | ----------- | -------------------------------------------------- |
  | 40601       | Bounce record was successfully deleted             |
  | 40602       | Failed to delete bounce record                     |
  | 40603       | Email already exists                               |
  | 40604       | Date format eg: 2018-03-19                         |
  | 40701       | Group ID cannot be empty                           |
  | 40702       | Invalid format of group ID                         |
  | 40703       | Event type cannot be empty                         |
  | 40704       | Invalid event type format, no event type available |
  | 40705       | URL cannot be empty                                |
  | 40706       | Invalid URL format                                 |
  | 40707       | URL test failed                                    |
  | 40708       | URL already exists                                 |
  | 40709       | Webhook configuration not found                    |
  | 40710       | Failed to create webhook configuration             |
  | 40711       | Failed to delete webhook configuration             |
  | 40712       | Failed to modify webhook configuration             |
</Accordion>

<Accordion title="Email Sending Parameters" icon="envelope">
  | Status Code | Meaning                                                                        |
  | ----------- | ------------------------------------------------------------------------------ |
  | 40801       | `fromAddress` cannot be empty                                                  |
  | 40802       | Invalid `fromAddress` format                                                   |
  | 40803       | `fromName` cannot be empty                                                     |
  | 40804       | Invalid `fromName` format                                                      |
  | 40805       | Recipient address cannot be empty                                              |
  | 40806       | Illegal addresses in the recipient address list                                |
  | 40807       | Recipient addresses should be no more than 100                                 |
  | 40808       | Subject cannot be empty                                                        |
  | 40809       | Invalid subject format                                                         |
  | 40810       | `replyto` cannot be empty                                                      |
  | 40811       | Invalid `replyto` format                                                       |
  | 40812       | `xsmtpapi` cannot be empty                                                     |
  | 40813       | Invalid `xsmtpapi` format                                                      |
  | 40814       | `xsmtpapi` parse cannot be empty                                               |
  | 40815       | `xsmtpapi` must contain field "to"                                             |
  | 40816       | Parse of field "to" cannot be empty                                            |
  | 40817       | `xsmtpapi` parsing error                                                       |
  | 40818       | Attachments cannot be empty                                                    |
  | 40819       | Attachment should be no larger than 10485760 bytes                             |
  | 40820       | No permission to use address list                                              |
  | 40821       | Address list was successfully created                                          |
  | 40822       | Failed to create address list                                                  |
  | 40823       | Mail template does not exist                                                   |
  | 40824       | Template not approved                                                          |
  | 40825       | Mail template does not match API-USER type                                     |
  | 40826       | Template parameter and subject cannot be empty both                            |
  | 40827       | Array "to" should be no longer than 100                                        |
  | 40828       | Reply address cannot be empty                                                  |
  | 40829       | Invalid reply address format                                                   |
  | 40830       | Plain cannot be empty                                                          |
  | 40831       | Invalid plain format                                                           |
  | 40832       | `startTime` cannot be empty                                                    |
  | 40833       | Invalid `startTime` format                                                     |
  | 40834       | `endTime` cannot be empty                                                      |
  | 40835       | Invalid `endTime` format                                                       |
  | 40836       | Title cannot be empty                                                          |
  | 40837       | Invalid title format                                                           |
  | 40838       | Organizer cannot be empty                                                      |
  | 40839       | Invalid organizer format                                                       |
  | 40840       | Organizer email address cannot be empty                                        |
  | 40841       | Invalid format of organizer email address                                      |
  | 40842       | Location cannot be empty                                                       |
  | 40843       | Invalid location format                                                        |
  | 40844       | Description cannot be empty                                                    |
  | 40845       | Invalid description format                                                     |
  | 40846       | Participant cannot be empty                                                    |
  | 40847       | Invalid participant format                                                     |
  | 40848       | Participant email address cannot be empty                                      |
  | 40849       | Invalid format of participant email address                                    |
  | 40850       | The number of participants is not equal to the number of email addresses       |
  | 40851       | Failed to assemble emails                                                      |
  | 40852       | CC address cannot be empty                                                     |
  | 40853       | Invalid CC address format                                                      |
  | 40854       | CC addresses should be no more than 100                                        |
  | 40855       | BCC address cannot be empty                                                    |
  | 40856       | Invalid BCC address format                                                     |
  | 40857       | BCC addresses should be no more than 100                                       |
  | 40858       | `respEmailId` cannot be empty                                                  |
  | 40859       | Invalid `respEmailId` format                                                   |
  | 40860       | `gzipCompress` cannot be empty                                                 |
  | 40861       | Invalid `gzipCompress` format                                                  |
  | 40862       | Address lists with format error in "to"                                        |
  | 40863       | Nonexistent address lists in "to"                                              |
  | 40864       | Address lists should be no more than 5                                         |
  | 40865       | Failed to extract HTML files                                                   |
  | 40866       | Failed to extract plain files                                                  |
  | 40867       | Abnormal attachment processing                                                 |
  | 40868       | Headers cannot be empty                                                        |
  | 40869       | Invalid headers format                                                         |
  | 40870       | HTML and plain cannot be empty both                                            |
  | 40871       | HTML format error                                                              |
  | 40872       | Address list cannot be empty                                                   |
  | 40873       | `useAddressList` cannot be empty                                               |
  | 40874       | Invalid `useAddressList` format                                                |
  | 40875       | The length of embedded picture ID is not equal to the length of the attachment |
  | 40876       | Invalid format of `isCancel` parameter                                         |
  | 40877       | Abstract cannot be empty                                                       |
  | 40878       | Abstract cannot be longer than 200 bytes                                       |
  | 40879       | `replyto` cannot be more than 3                                                |
  | 40880       | Invalid email format in field "to" of `xsmtpapi`                               |
</Accordion>

<Accordion title="Email Sending Results" icon="paper-plane">
  | Status Code | Meaning                                                             |
  | ----------- | ------------------------------------------------------------------- |
  | 40901       | Email sending failed                                                |
  | 40902       | Unknown error when processing email                                 |
  | 40903       | Email sent successfully                                             |
  | 40904       | Quota check failed                                                  |
  | 40905       | Quota check passed                                                  |
  | 40906       | Quota check temporarily passed                                      |
  | 40907       | No need to match template for corresponding content of the API-USER |
  | 40908       | Email content does not match template                               |
  | 40909       | Email content matches template                                      |
  | 40910       | Email content temporarily matches template                          |
  | 40911       | Error occurred when matching email content and template             |
  | 40912       | Your account balance is not enough, please recharge soon            |
  | 40913       | Request quota exceeded                                              |
</Accordion>

<Accordion title="Domain & API User Management" icon="globe">
  | Status Code | Meaning                                                                                                           |
  | ----------- | ----------------------------------------------------------------------------------------------------------------- |
  | 41001       | Name cannot be empty                                                                                              |
  | 41002       | Name should be 1-250 characters                                                                                   |
  | 41003       | Name does not conform to domain specification                                                                     |
  | 41004       | `newName` cannot be empty                                                                                         |
  | 41005       | `newName` should be 1-250 characters                                                                              |
  | 41006       | `newName` does not conform to domain specification                                                                |
  | 41007       | Type cannot be empty                                                                                              |
  | 41008       | Type does not conform to specification                                                                            |
  | 41009       | Verify cannot be empty                                                                                            |
  | 41010       | Verify does not conform to specification                                                                          |
  | 41011       | Verify parsing error                                                                                              |
  | 41012       | User can create no more than 5 domains                                                                            |
  | 41013       | Name parameter error, multiple domains                                                                            |
  | 41014       | Domain does not exist                                                                                             |
  | 41015       | Failed to create domain                                                                                           |
  | 41016       | Failed to modify domain                                                                                           |
  | 41101       | `emailType` cannot be empty                                                                                       |
  | 41102       | `emailType` does not conform to specification                                                                     |
  | 41103       | `cType` cannot be empty                                                                                           |
  | 41104       | `cType` does not conform to specification                                                                         |
  | 41105       | `domainName` cannot be empty                                                                                      |
  | 41106       | `domainName` does not conform to specification                                                                    |
  | 41107       | `domainName` should be 1-250 characters                                                                           |
  | 41108       | Domain of `domainName` does not exist                                                                             |
  | 41109       | User information does not exist                                                                                   |
  | 41110       | Name cannot be empty                                                                                              |
  | 41111       | Name does not conform to specification (name should be 6-32 characters; only numbers and letters can be included) |
  | 41112       | `apiUser` should be no more than 10                                                                               |
  | 41113       | Open cannot be empty                                                                                              |
  | 41114       | Open does not conform to specification                                                                            |
  | 41115       | Click cannot be empty                                                                                             |
  | 41116       | Click does not conform to specification                                                                           |
  | 41117       | Unsubscribe cannot be empty                                                                                       |
  | 41118       | Unsubscribe does not conform to specification                                                                     |
  | 41119       | Failed to create `apiUser`                                                                                        |
</Accordion>

<Accordion title="System & Server Errors" icon="exclamation-circle">
  | Status Code | Meaning                                    |
  | ----------- | ------------------------------------------ |
  | 49901       | Invalid URL format                         |
  | 49902       | Abnormal HTTP request                      |
  | 49903       | HTTP request failed                        |
  | 49904       | HTTP request was successful                |
  | 49905       | HTTP result parsing error                  |
  | 49906       | Other errors                               |
  | 50000       | Interface frequency limited                |
  | 50001       | Mail sending failed. 536 frequency limited |
  | 501         | Server exception                           |
  | 6001        | You don't have permission to access        |
</Accordion>

## 6. Best Practices

<Cards>
  <Card title="Error Handling" icon="shield-alt">
    Always implement proper error handling by checking the `result` field and `statusCode` in responses. Use the comprehensive error codes above to provide meaningful feedback to users.
  </Card>

  <Card title="Rate Limiting" icon="clock">
    Be aware of rate limits (status codes 50000, 50001). Implement exponential backoff and respect the API's rate limiting to ensure reliable service.
  </Card>

  <Card title="Security" icon="lock">
    Never expose API credentials in client-side code. Use environment variables or secure credential storage solutions in production environments.
  </Card>

  <Card title="Regional Optimization" icon="globe-americas">
    Use the correct regional endpoint for email APIs to ensure optimal performance and compliance with local regulations.
  </Card>
</Cards>

## 7. Next Steps

Explore key API endpoints to extend your integration:

* **[Email APIs](https://www.aurorasendcloud.com/docs/API/index/)**: Send transactional/bulk emails, track deliveries (use region-specific base URL)
* **[SMS API](https://www.aurorasendcloud.com/docs/API/index/)**: Send transactional SMS (use unified `api.aurorasendcloud.com/v1/` URL)
* **[Contact Management](https://www.aurorasendcloud.com/docs/API/index/)**: Create/update contacts, manage lists (region-specific)
* **[Email Templates](https://www.aurorasendcloud.com/docs/API/index/)**: Use pre-built templates for consistent branding (region-specific)
* **[Suppression Lists](https://www.aurorasendcloud.com/docs/API/index/)**: Manage unsubscribes and bounces (region-specific)

## 8. Resources

* **[Full API Reference](https://www.aurorasendcloud.com/docs/API/index/)**: Detailed docs for all endpoints (includes SMS-specific parameters)
* **[SDKs & Libraries](https://www.aurorasendcloud.com/docs/API/index/)**: Official libraries for Python, Java, Node.js, and PHP (supports both multi-region and SMS APIs)
* **[Region-Specific Compliance](https://www.aurorasendcloud.com/docs/API/index/)**: Guidelines for GDPR (EU/US), PDPA (SG/HK), and SMS regulatory requirements
* **[Support](https://www.aurorasendcloud.com/support)**: Contact the team for region-specific or SMS API-related technical issues

***

**Ready to start building?** Use the code examples above to send your first email or SMS, and refer to the complete error code reference when debugging your integration.
