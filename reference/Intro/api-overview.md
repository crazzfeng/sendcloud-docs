---
title: API Overview
excerpt: >-
  Get started with AuroraSendCloud's powerful APIs, SMTP services, and
  integration guides. Learn how to send emails, manage contacts, and track
  performance across multiple regions.
deprecated: false
hidden: true
link:
  new_tab: false
metadata:
  robots: index
---
## AuroraSendCloud API Quickstart

Get started with AuroraSendCloud's powerful APIs to send emails, manage contacts, track performance, and integrate seamlessly with your applications. Follow this step-by-step guide to make your first API call in minutes, with clear distinctions between multi-region email APIs and the single-region SMS API.

### Prerequisites

Before you begin, ensure you have:

* An active AuroraSendCloud account (sign up at [aurorasendcloud.com](https://www.aurorasendcloud.com/))
* Your **API Key** and **API User** (found in your account's [API Key Management](https://www.aurorasendcloud.com/web/#/api/apiuser) page)
* A supported HTTP client (e.g., cURL, Postman, Python's `requests` library)
* Confirmation of your account's **region** (Singapore, US, or Hong Kong) for email API access (not required for SMS API)

## API Base URLs & SMTP Servers (By Service Type)

### Email & Core APIs (Multi-Region)

Choose the base URL that matches your account's region for email, contact management, templates, and other core services. All requests must use **HTTPS**, and responses are returned in **JSON** format.

| Region             | Base URL                              | Coverage                                  |
| ------------------ | ------------------------------------- | ----------------------------------------- |
| Singapore (SG)     | `https://api.aurorasendcloud.com/`    | Default region for APAC users             |
| United States (US) | `https://api-us.aurorasendcloud.com/` | For North American users and services     |
| Hong Kong (HK)     | `https://api-hk.aurorasendcloud.com/` | For Greater China and nearby APAC regions |

> ℹ️ **Note**: Your account is tied to a specific region during sign-up. Using a non-matching base URL for email/core APIs will cause authentication failures or data inconsistencies. Confirm your region in your account settings.

### SMTP Servers (Multi-Region)

For applications that require SMTP integration, use the regional SMTP server that corresponds to your account's region. All SMTP connections require **authentication** and support both **SSL/TLS** encryption.

| Region             | SMTP Server                   | Port (SSL/TLS) | Port (STARTTLS) | Coverage                                  |
| ------------------ | ----------------------------- | -------------- | --------------- | ----------------------------------------- |
| Singapore (SG)     | `smtp.aurorasendcloud.com`    | 465            | 587             | Default region for APAC users             |
| United States (US) | `smtp-us.aurorasendcloud.com` | 465            | 587             | For North American users and services     |
| Hong Kong (HK)     | `smtp-hk.aurorasendcloud.com` | 465            | 587             | For Greater China and nearby APAC regions |

#### SMTP Authentication

* **Username**: Your AuroraSendCloud API username (same as `api_user`)
* **Password**: Your AuroraSendCloud API key (same as `api_key`)
* **Encryption**: SSL/TLS (recommended) or STARTTLS

#### SMTP Configuration Example

<Tabs>
  <Tab title="Python (smtplib)">
    ```python
    import smtplib
    from email.mime.text import MIMEText
    from email.mime.multipart import MIMEMultipart

    # Regional SMTP settings
    smtp_server = "smtp.aurorasendcloud.com"  # or smtp-us/smtp-hk
    smtp_port = 465  # SSL/TLS
    username = "YOUR_API_USER"
    password = "YOUR_API_KEY"

    # Create message
    msg = MIMEMultipart()
    msg['From'] = "sender@yourdomain.com"
    msg['To'] = "recipient@example.com"
    msg['Subject'] = "Test Email via SMTP"

    body = "Hello from AuroraSendCloud SMTP!"
    msg.attach(MIMEText(body, 'plain'))

    # Send email
    with smtplib.SMTP_SSL(smtp_server, smtp_port) as server:
        server.login(username, password)
        server.send_message(msg)
    ```
  </Tab>

  <Tab title="Node.js (Nodemailer)">
    ```javascript
    const nodemailer = require('nodemailer');

    const transporter = nodemailer.createTransporter({
      host: 'smtp.aurorasendcloud.com', // or smtp-us/smtp-hk
      port: 465,
      secure: true, // SSL/TLS
      auth: {
        user: 'YOUR_API_USER',
        pass: 'YOUR_API_KEY'
      }
    });

    const mailOptions = {
      from: 'sender@yourdomain.com',
      to: 'recipient@example.com',
      subject: 'Test Email via SMTP',
      text: 'Hello from AuroraSendCloud SMTP!',
      html: '<h1>Hello from AuroraSendCloud SMTP!</h1>'
    };

    transporter.sendMail(mailOptions, (error, info) => {
      if (error) {
        console.log('Error:', error);
      } else {
        console.log('Email sent:', info.response);
      }
    });
    ```
  </Tab>

  <Tab title="PHP (PHPMailer)">
    ```php
    <?php
    use PHPMailer\PHPMailer\PHPMailer;
    use PHPMailer\PHPMailer\SMTP;

    $mail = new PHPMailer(true);

    try {
        // Server settings
        $mail->isSMTP();
        $mail->Host       = 'smtp.aurorasendcloud.com'; // or smtp-us/smtp-hk
        $mail->SMTPAuth   = true;
        $mail->Username   = 'YOUR_API_USER';
        $mail->Password   = 'YOUR_API_KEY';
        $mail->SMTPSecure = PHPMailer::ENCRYPTION_SMTPS;
        $mail->Port       = 465;

        // Recipients
        $mail->setFrom('sender@yourdomain.com', 'Your Name');
        $mail->addAddress('recipient@example.com');

        // Content
        $mail->isHTML(true);
        $mail->Subject = 'Test Email via SMTP';
        $mail->Body    = '<h1>Hello from AuroraSendCloud SMTP!</h1>';

        $mail->send();
        echo 'Message has been sent';
    } catch (Exception $e) {
        echo "Message could not be sent. Mailer Error: {$mail->ErrorInfo}";
    }
    ?>
    ```
  </Tab>
</Tabs>

### SMS API (Single Region)

The SMS API uses a **unified global base URL** (no regional endpoints required):

* **Base URL**: `https://api.aurorasendcloud.com/`
* All SMS requests must use this URL regardless of your account's region
* Authentication and response format are consistent with email/core APIs

## &#x20;Authentication

Authenticate all API requests (email, SMS, and core services) by including your credentials as **request parameters**:

* `api_user`: Your AuroraSendCloud API username
* `api_key`: Your AuroraSendCloud API key

> ⚠️ **Critical Security Note**: Never expose your API credentials in client-side code (e.g., browsers, mobile apps). Restrict access to your API key, rotate it regularly via the API Key Management page, and avoid hardcoding credentials in your source code.

## Making Your First API Call

### Example: Send an Email via REST API

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

## API Response Format

All API responses (email and SMS) follow a consistent JSON structure:

### Success Response (Request Successful)

```json
{
  "result": true,
  "statusCode": 200,
  "message": "request was successful",
  "info": {}
}
```

### Success Response (Data Acquisition)

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

### Error Response (Authentication Failed)

```json
{
  "result": false,
  "statusCode": 40005,
  "message": "authentication failed",
  "info": {}
}
```

#### Response Field Definitions:

* `result`: Boolean indicating whether the request succeeded (`true`) or failed (`false`)
* `statusCode`: Numeric code representing the request status (see complete list below)
* `message`: Description of the status code (for debugging and user feedback)
* `info`: Contains response data (e.g., SMS/email IDs, retrieved records) on success; empty on failure

## API Return Codes Reference

### Common Status Codes

| Status Code | Meaning                                            |
| ----------- | -------------------------------------------------- |
| 200         | Request was successful                             |
| 40005       | Authentication failed (check `api_user`/`api_key`) |
| 40903       | Email sent successfully                            |
| 40901       | Email sending failed                               |
| 50000       | Interface frequency limited                        |
| 501         | Server exception                                   |
| 6001        | You don't have permission to access                |

### General & Validation Errors (40001-40017)

| Status Code | Meaning                                                     |
| ----------- | ----------------------------------------------------------- |
| 40001       | `start` cannot be empty                                     |
| 40002       | Invalid `start` parameter                                   |
| 40003       | `limit` cannot be empty                                     |
| 40004       | Invalid `limit` parameter                                   |
| 40006       | Invalid `days` format; must be an integer greater than zero |
| 40007       | Invalid `startDate` format (e.g., "2013-03-19")             |
| 40008       | Invalid `endDate` format (e.g., "2013-03-19")               |
| 40009       | `labelIdList` cannot be empty                               |
| 40010       | `apiUserList` cannot be empty                               |
| 40011       | Email cannot be empty                                       |
| 40012       | Invalid email format                                        |
| 40013       | `domainList` cannot be empty                                |
| 40014       | Label ID cannot be empty                                    |
| 40015       | Invalid label ID format                                     |
| 40016       | Invalid `apiUserList` format                                |
| 40017       | Invalid format of aggregation parameters                    |

### Label Management (40100-40113)

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

### Template Management (40201-40229)

| Status Code | Meaning                                                                  |
| ----------- | ------------------------------------------------------------------------ |
| 40201       | `invokeName` cannot be empty                                             |
| 40202       | Invalid `invokeName` format                                              |
| 40203       | Template type cannot be empty                                            |
| 40204       | Invalid template type; can only be 0 or 1                                |
| 40205       | `templateStat` cannot be empty                                           |
| 40206       | Invalid `templateStat`; can only be -1, -2, 1, or 0                      |
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
| 40226       | Template is pending approval; do not submit again                        |
| 40227       | Template has been approved; do not submit again                          |
| 40228       | Template not approved; do not withdraw the approval request              |
| 40229       | Template not submitted for approval; unable to withdraw approval request |

### Email Sending Parameters (40801-40880)

| Status Code | Meaning                                          |
| ----------- | ------------------------------------------------ |
| 40801       | `fromAddress` cannot be empty                    |
| 40802       | Invalid `fromAddress` format                     |
| 40803       | `fromName` cannot be empty                       |
| 40804       | Invalid `fromName` format                        |
| 40805       | Recipient address cannot be empty                |
| 40806       | Illegal addresses in the recipient address list  |
| 40807       | Recipient addresses should be no more than 100   |
| 40808       | Subject cannot be empty                          |
| 40809       | Invalid subject format                           |
| 40810       | `replyto` cannot be empty                        |
| 40811       | Invalid `replyto` format                         |
| 40870       | HTML and plain cannot both be empty              |
| 40871       | HTML format error                                |
| 40879       | `replyto` cannot be more than 3                  |
| 40880       | Invalid email format in field "to" of `xsmtpapi` |

### Email Sending Results (40901-40913)

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
| 40912       | Your account balance is insufficient; please recharge soon          |
| 40913       | Request quota exceeded                                              |

### Address List Management (40501-40522)

| Status Code | Meaning                                                   |
| ----------- | --------------------------------------------------------- |
| 40501       | Name cannot be empty                                      |
| 40502       | Address list name should be 1-48 characters               |
| 40503       | Address cannot be empty                                   |
| 40504       | Address list alias should be 1-48 characters              |
| 40505       | Address list alias already exists                         |
| 40506       | Description cannot be empty                               |
| 40507       | Address list description should be 1-250 characters       |
| 40508       | Failed to create address list                             |
| 40514       | Number of member addresses should be more than 0          |
| 40515       | Number of member addresses should be no more than 1000    |
| 40516       | Failed to add member                                      |
| 40517       | Address list does not belong to the user                  |
| 40518       | Member address does not conform to the specification      |
| 40519       | Failed to delete member                                   |
| 40522       | Variables parameter does not adhere to JSON string syntax |

### Domain & API User Management (41001-41119)

| Status Code | Meaning                                                                                              |
| ----------- | ---------------------------------------------------------------------------------------------------- |
| 41001       | Name cannot be empty                                                                                 |
| 41002       | Name should be 1-250 characters                                                                      |
| 41003       | Name does not conform to domain specification                                                        |
| 41008       | Type does not conform to specification                                                               |
| 41012       | User can create no more than 5 domains                                                               |
| 41014       | Domain does not exist                                                                                |
| 41015       | Failed to create domain                                                                              |
| 41016       | Failed to modify domain                                                                              |
| 41109       | User information does not exist                                                                      |
| 41111       | Name does not conform to specification (should be 6-32 characters; only numbers and letters allowed) |
| 41112       | `apiUser` should be no more than 10                                                                  |
| 41119       | Failed to create `apiUser`                                                                           |

### System & Server Errors (49901-50001)

| Status Code | Meaning                                    |
| ----------- | ------------------------------------------ |
| 49901       | Invalid URL format                         |
| 49902       | Abnormal HTTP request                      |
| 49903       | HTTP request failed                        |
| 49904       | HTTP request was successful                |
| 49905       | HTTP result parsing error                  |
| 49906       | Other errors                               |
| 50000       | Interface frequency limited                |
| 50001       | Mail sending failed; 536 frequency limited |

## Best Practices

<Cards>
  <Card title="Error Handling" icon="shield-alt">
    Always implement proper error handling by checking the `result` field and `statusCode` in responses. Use the comprehensive error codes above to provide meaningful feedback to users.
  </Card>

  <Card title="Rate Limiting" icon="clock">
    Be aware of rate limits (status codes 50000, 50001). Implement exponential backoff and respect the API's rate limiting to ensure reliable service.
  </Card>

  <Card title="Security" icon="lock">
    Never expose API credentials in client-side code. Use environment variables or secure credential storage solutions in production environments. The same credentials work for both REST API and SMTP authentication.
  </Card>

  <Card title="Regional Optimization" icon="globe-americas">
    Use the correct regional endpoint for both REST APIs and SMTP servers to ensure optimal performance and compliance with local regulations. Match your account region consistently across all services.
  </Card>

  <Card title="SMTP vs REST API" icon="code">
    Choose SMTP for simple email sending integrations with existing email libraries. Use REST API for advanced features like templates, tracking, and bulk operations with detailed response handling.
  </Card>
</Cards>

**Ready to start building?** Use the REST API examples for advanced integrations or configure SMTP settings for simple email sending. Both methods support the same regional optimization and authentication credentials.
