---
title: API Overview
excerpt: >-
  Complete guide to AuroraSendCloud's APIs, SMTP services, and integration.
  Learn authentication, regional endpoints, email/SMS sending, and comprehensive
  error handling.
deprecated: false
hidden: false
link:
  new_tab: false
metadata:
  robots: index
---
# AuroraSendCloud API Overview

Get started with AuroraSendCloud's powerful APIs to send emails, manage contacts, track performance, and integrate seamlessly with your applications. This comprehensive guide will help you make your first API call in minutes.

## Quick Start Checklist

Before you begin, ensure you have:

* ✅ An active AuroraSendCloud account ([Sign up here](https://www.aurorasendcloud.com/))
* ✅ Your **API Key** and **API User** from [API Key Management](https://www.aurorasendcloud.com/web/#/api/apiuser)
* ✅ A supported HTTP client (cURL, Postman, Python, Node.js, etc.)
* ✅ Your account **region** (Singapore, US, or CN) for optimal performance

## Regional Base URLs & Endpoints

### Email APIs & SMTP Servers (Multi-Region)

Choose the base URL and SMTP server that matches your account's region for email services, contact management, templates, and other core services. All REST API requests must use **HTTPS**, and responses are returned in **JSON** format.

#### REST API Endpoints

| Region              | Base URL                              |
| ------------------- | ------------------------------------- |
| Singapore           | `https://api.aurorasendcloud.com/`    |
| US (Silicon Valley) | `https://api-us.aurorasendcloud.com/` |
| CN (Hong Kong SAR)  | `https://api-hk.aurorasendcloud.com/` |

#### SMTP Servers

| Region              | SMTP Server                   | SSL Port | STARTTLS Port |
| ------------------- | ----------------------------- | -------- | ------------- |
| Singapore           | `smtp.aurorasendcloud.com`    | 465      | 587           |
| US (Silicon Valley) | `smtp-us.aurorasendcloud.com` | 465      | 587           |
| CN (Hong Kong SAR)  | `smtp-hk.aurorasendcloud.com` | 465      | 587           |

> ⚠️ **Important**: Your account is tied to a specific region. Using a non-matching base URL or SMTP server will cause authentication failures. Verify your region in account settings.

### SMS API (Single Global Endpoint)

The SMS API uses a unified global endpoint regardless of your account region:

* **Base URL**: `https://api.aurorasendcloud.com/`

## Authentication

All API and SMTP requests require authentication using these parameters:

* `api_user`: Your AuroraSendCloud API username
* `api_key`: Your AuroraSendCloud API key

<Callout icon="🔐" theme="default">
  ### **Security Best Practice**: Never expose API credentials in client-side code. Use server-side implementations and rotate keys regularly.
</Callout>

## Email Integration Options

AuroraSendCloud offers two methods for sending emails: **REST API** for advanced features and programmatic control, and **SMTP** for simple integration with existing email clients and applications.

### REST API - Send an Email

<Tabs>
  <Tab title="cURL">
    ```bash
    curl -X POST "https://api.aurorasendcloud.com/api/mail/send" \
      -d "api_user=YOUR_API_USER" \
      -d "api_key=YOUR_API_KEY" \
      -d "from=sender@yourdomain.com" \
      -d "fromName=Your Name" \
      -d "to=recipient@example.com" \
      -d "subject=Welcome to AuroraSendCloud" \
      -d "html=<h1>Hello World!</h1><p>Your first email via AuroraSendCloud API</p>"
    ```
  </Tab>

  <Tab title="Python">
    ```python
    import requests

    url = "https://api.aurorasendcloud.com/api/mail/send"
    data = {
        "api_user": "YOUR_API_USER",
        "api_key": "YOUR_API_KEY",
        "from": "sender@yourdomain.com",
        "fromName": "Your Name",
        "to": "recipient@example.com",
        "subject": "Welcome to AuroraSendCloud",
        "html": "<h1>Hello World!</h1><p>Your first email via AuroraSendCloud API</p>"
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
      subject: 'Welcome to AuroraSendCloud',
      html: '<h1>Hello World!</h1><p>Your first email via AuroraSendCloud API</p>'
    };

    axios.post('https://api.aurorasendcloud.com/api/mail/send', data)
      .then(response => console.log(response.data))
      .catch(error => console.error(error));
    ```
  </Tab>
</Tabs>

### SMTP Integration

For applications requiring SMTP integration, use our regional SMTP servers with SSL/TLS encryption:

#### SMTP Configuration

* **Username**: Your API username (`api_user`)
* **Password**: Your API key (`api_key`)
* **Encryption**: SSL/TLS (port 465) or STARTTLS (port 587)
* **Authentication**: Required for all connections

#### SMTP Code Examples

<Tabs>
  <Tab title="Python (smtplib)">
    ```python
    import smtplib
    from email.mime.text import MIMEText
    from email.mime.multipart import MIMEMultipart

    # Configuration - Use regional SMTP server
    smtp_server = "smtp.aurorasendcloud.com"  # Singapore
    # smtp_server = "smtp-us.aurorasendcloud.com"  # US
    # smtp_server = "smtp-hk.aurorasendcloud.com"  # CN
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
        print("Email sent successfully!")
    ```
  </Tab>

  <Tab title="Node.js (Nodemailer)">
    ```javascript
    const nodemailer = require('nodemailer');

    const transporter = nodemailer.createTransporter({
      host: 'smtp.aurorasendcloud.com', // Use regional server
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
        // Server settings - Use regional SMTP server
        $mail->isSMTP();
        $mail->Host       = 'smtp.aurorasendcloud.com'; // Singapore
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

  <Tab title="Java (JavaMail)">
    ```java
    import java.util.Properties;
    import javax.mail.*;
    import javax.mail.internet.*;

    public class SMTPExample {
        public static void main(String[] args) {
            String host = "smtp.aurorasendcloud.com"; // Use regional server
            String username = "YOUR_API_USER";
            String password = "YOUR_API_KEY";

            Properties props = new Properties();
            props.put("mail.smtp.host", host);
            props.put("mail.smtp.port", "465");
            props.put("mail.smtp.ssl.enable", "true");
            props.put("mail.smtp.auth", "true");

            Session session = Session.getInstance(props, new Authenticator() {
                protected PasswordAuthentication getPasswordAuthentication() {
                    return new PasswordAuthentication(username, password);
                }
            });

            try {
                Message message = new MimeMessage(session);
                message.setFrom(new InternetAddress("sender@yourdomain.com"));
                message.setRecipients(Message.RecipientType.TO,
                    InternetAddress.parse("recipient@example.com"));
                message.setSubject("Test Email via SMTP");
                message.setText("Hello from AuroraSendCloud SMTP!");

                Transport.send(message);
                System.out.println("Email sent successfully!");

            } catch (MessagingException e) {
                throw new RuntimeException(e);
            }
        }
    }
    ```
  </Tab>
</Tabs>

### SMTP vs REST API Comparison

| Feature                    | SMTP                | REST API           |
| -------------------------- | ------------------- | ------------------ |
| **Setup Complexity**      | Simple              | Moderate           |
| **Advanced Features**      | Limited             | Full access        |
| **Template Support**       | Basic               | Advanced           |
| **Tracking & Analytics**   | Basic               | Comprehensive      |
| **Bulk Sending**           | Good                | Optimized          |
| **Real-time Status**       | Basic               | Detailed           |
| **Integration Effort**     | Minimal             | Moderate           |

## SMS Integration

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

All API responses follow a consistent JSON structure:

### Success Response

```json
{
  "result": true,
  "statusCode": 200,
  "message": "request was successful",
  "info": {
    "emailIdList": ["email_id_123"]
  }
}
```

### Error Response

```json
{
  "result": false,
  "statusCode": 40005,
  "message": "authentication failed",
  "info": {}
}
```

### Response Fields

* `result`: Boolean indicating success (`true`) or failure (`false`)
* `statusCode`: Numeric status code (see complete reference below)
* `message`: Human-readable description of the result
* `info`: Contains response data on success, empty object on failure

## Complete Status Code Reference

### Common Status Codes

| Status Code | Meaning                                                 |
| ----------- | ------------------------------------------------------- |
| **200**     | Request was successful                                  |
| **40005**   | Authentication failed - verify `api_user` and `api_key` |
| **40903**   | Email sent successfully                                 |
| **40901**   | Email sending failed                                    |
| **50000**   | Rate limit exceeded - implement retry logic             |
| **501**     | Server exception                                        |
| **6001**    | Access permission denied                                |

### Parameter Validation Errors (40001-40017)

| Status Code | Meaning                                     |
| ----------- | ------------------------------------------- |
| **40001**   | `start` parameter cannot be empty           |
| **40002**   | Invalid `start` parameter format            |
| **40003**   | `limit` parameter cannot be empty           |
| **40004**   | Invalid `limit` parameter format            |
| **40006**   | Invalid `days` format - must be integer > 0 |
| **40007**   | Invalid `startDate` format - use yyyy-MM-dd |
| **40008**   | Invalid `endDate` format - use yyyy-MM-dd   |
| **40009**   | `labelIdList` cannot be empty               |
| **40010**   | `apiUserList` cannot be empty               |
| **40011**   | Email address cannot be empty               |
| **40012**   | Invalid email address format                |
| **40013**   | `domainList` cannot be empty                |
| **40014**   | Label ID cannot be empty                    |
| **40015**   | Invalid label ID format                     |
| **40016**   | Invalid `apiUserList` format                |
| **40017**   | Invalid aggregation parameter format        |

### Label Management (40100-40113)

| Status Code | Meaning                             |
| ----------- | ----------------------------------- |
| **40100**   | Label created successfully          |
| **40101**   | Label creation failed               |
| **40102**   | Label ID cannot be empty            |
| **40103**   | Invalid label ID                    |
| **40104**   | Label name cannot be empty          |
| **40105**   | Label name must be 1-255 characters |
| **40106**   | Label ID does not exist             |
| **40107**   | Label deleted successfully          |
| **40108**   | Label deletion failed               |
| **40109**   | Label updated successfully          |
| **40110**   | Label update failed                 |
| **40111**   | Query parameter cannot be empty     |
| **40112**   | Query must be 1-255 characters      |
| **40113**   | Label name already exists           |

### Template Management (40201-40229)

| Status Code | Meaning                                          |
| ----------- | ------------------------------------------------ |
| **40201**   | `invokeName` cannot be empty                     |
| **40202**   | Invalid `invokeName` format                      |
| **40203**   | Template type cannot be empty                    |
| **40204**   | Invalid template type - must be 0 or 1           |
| **40205**   | `templateStat` cannot be empty                   |
| **40206**   | Invalid `templateStat` - must be -1, -2, 1, or 0 |
| **40207**   | Template name cannot be empty                    |
| **40208**   | Invalid template name format                     |
| **40209**   | Template subject cannot be empty                 |
| **40210**   | Invalid template subject format                  |
| **40211**   | Template HTML cannot be empty                    |
| **40212**   | Invalid template HTML format                     |
| **40213**   | Template text cannot be empty                    |
| **40214**   | Invalid template text format                     |
| **40215**   | Template creation failed                         |
| **40216**   | Template with `invokeName` does not exist        |
| **40217**   | Template deletion failed                         |
| **40218**   | Template update failed                           |
| **40219**   | Maximum 50 templates per user exceeded           |
| **40220**   | `invokeName` already exists                      |
| **40221**   | `isSubmitAudit` cannot be empty                  |
| **40222**   | Invalid `isSubmitAudit` format                   |
| **40223**   | Template pending approval - cannot modify        |
| **40224**   | Cancel parameter cannot be empty                 |
| **40225**   | Invalid cancel parameter format                  |
| **40226**   | Template already pending approval                |
| **40227**   | Template already approved                        |
| **40228**   | Template not approved - cannot withdraw          |
| **40229**   | Template not submitted - cannot withdraw         |

### Address List Management (40501-40522)

| Status Code | Meaning                                           |
| ----------- | ------------------------------------------------- |
| **40501**   | Address list name cannot be empty                 |
| **40502**   | Address list name must be 1-48 characters         |
| **40503**   | Address list addresses cannot be empty            |
| **40504**   | Address list alias must be 1-48 characters        |
| **40505**   | Address list alias already exists                 |
| **40506**   | Address list description cannot be empty          |
| **40507**   | Address list description must be 1-250 characters |
| **40508**   | Address list creation failed                      |
| **40514**   | Address list must have > 0 members                |
| **40515**   | Address list cannot exceed 1000 members           |
| **40516**   | Failed to add member to address list              |
| **40517**   | Address list does not belong to user              |
| **40518**   | Invalid member address format                     |
| **40519**   | Failed to delete member from address list         |
| **40522**   | Variables parameter is not valid JSON             |

### Email Sending Parameters (40801-40880)

| Status Code | Meaning                                      |
| ----------- | -------------------------------------------- |
| **40801**   | Sender address (`from`) cannot be empty      |
| **40802**   | Invalid sender address format                |
| **40803**   | Sender name (`fromName`) cannot be empty     |
| **40804**   | Invalid sender name format                   |
| **40805**   | Recipient address cannot be empty            |
| **40806**   | Invalid recipient addresses in list          |
| **40807**   | Maximum 100 recipient addresses per request  |
| **40808**   | Email subject cannot be empty                |
| **40809**   | Invalid email subject format                 |
| **40810**   | Reply-to address cannot be empty             |
| **40811**   | Invalid reply-to address format              |
| **40870**   | Both HTML and plain text cannot be empty     |
| **40871**   | Invalid HTML format                          |
| **40879**   | Maximum 3 reply-to addresses allowed         |
| **40880**   | Invalid email format in X-SMTPAPI "to" field |

### Email Sending Results (40901-40913)

| Status Code | Meaning                                        |
| ----------- | ---------------------------------------------- |
| **40901**   | Email sending failed                           |
| **40902**   | Unknown error processing email                 |
| **40903**   | Email sent successfully                        |
| **40904**   | Quota check failed                             |
| **40905**   | Quota check passed                             |
| **40906**   | Quota check temporarily passed                 |
| **40907**   | No template matching required for API_USER     |
| **40908**   | Email content does not match template          |
| **40909**   | Email content matches template                 |
| **40910**   | Email content temporarily matches template     |
| **40911**   | Error matching email content with template     |
| **40912**   | Insufficient account balance - please recharge |
| **40913**   | Request quota exceeded                         |

### Domain & API User Management (41001-41119)

| Status Code | Meaning                                                  |
| ----------- | -------------------------------------------------------- |
| **41001**   | Domain name cannot be empty                              |
| **41002**   | Domain name must be 1-250 characters                     |
| **41003**   | Invalid domain name format                               |
| **41008**   | Invalid domain type                                      |
| **41012**   | Maximum 5 domains per user                               |
| **41014**   | Domain does not exist                                    |
| **41015**   | Domain creation failed                                   |
| **41016**   | Domain modification failed                               |
| **41109**   | User information does not exist                          |
| **41111**   | Invalid API user name (6-32 chars, letters/numbers only) |
| **41112**   | Maximum 10 API users per account                         |
| **41119**   | API user creation failed                                 |

### System & Server Errors (49901-50001)

| Status Code | Meaning                                  |
| ----------- | ---------------------------------------- |
| **49901**   | Invalid URL format                       |
| **49902**   | Abnormal HTTP request                    |
| **49903**   | HTTP request failed                      |
| **49904**   | HTTP request successful                  |
| **49905**   | HTTP response parsing error              |
| **49906**   | Other system errors                      |
| **50000**   | Rate limit exceeded                      |
| **50001**   | Email sending failed - frequency limited |

## Best Practices

<Cards>
  <Card title="Error Handling" icon="exclamation-triangle">
    Always check the `result` field and implement proper error handling based on `statusCode`. Use the comprehensive status code reference above for specific error responses.
  </Card>

  <Card title="Rate Limiting" icon="clock">
    Implement exponential backoff for rate limit errors (50000, 50001). Monitor your sending patterns and distribute requests over time.
  </Card>

  <Card title="Security" icon="shield-alt">
    Never expose API credentials in client-side code. Use environment variables, rotate keys regularly, and implement server-side proxy endpoints for frontend applications.
  </Card>

  <Card title="Regional Optimization" icon="globe">
    Use the correct regional endpoint for both REST APIs and SMTP servers. This ensures optimal performance, compliance, and reduces latency.
  </Card>

  <Card title="Monitoring & Analytics" icon="chart-line">
    Track email delivery rates, open rates, and bounce rates. Use webhooks for real-time event notifications and implement proper logging for debugging.
  </Card>
</Cards>

## Account Management & Quotas

### Daily Request Quota

Your account has a daily request quota that varies based on account type and reputation:

* **Free users**: 50 emails/day after email verification
* **Paid users**: Base quota of 3,000 emails/day, automatically adjusted based on reputation

### Reputation System

AuroraSendCloud uses a reputation scoring system that affects your daily quota:

* **Positive factors**: High delivery rates, open rates, click rates
* **Negative factors**: Invalid addresses, spam reports, unsubscribes
* **Critical**: Rapid increases in invalid addresses or spam reports can suspend sending

### Variables in Email Content

Use variables in your email content for personalization:

```html
Hi %name%,
Welcome to AuroraSendCloud! Your verification code is: %active_code%
```

Variables can be used in:

* Email subject lines
* HTML and plain text content
* Template content with X-SMTPAPI substitution

## Next Steps

Now that you understand the basics:

1. **Set up your domain** - Configure SPF, DKIM, and DMARC records
2. **Create templates** - Build reusable email templates for common scenarios
3. **Implement webhooks** - Get real-time notifications for email events
4. **Monitor performance** - Track delivery rates and optimize your sending

<Cards>
  <Card title="Email Templates" href="/docs/email-templates" icon="file-alt">
    Create and manage reusable email templates with dynamic content
  </Card>

  <Card title="Webhook Integration" href="/docs/webhooks" icon="webhook">
    Set up real-time event notifications for email tracking
  </Card>

  <Card title="Domain Configuration" href="/docs/domains" icon="globe">
    Configure sending domains for better deliverability
  </Card>

  <Card title="Statistics & Analytics" href="/docs/statistics" icon="chart-bar">
    Monitor email performance and delivery metrics
  </Card>
</Cards>

Ready to start building? Choose between REST API for advanced features or SMTP for simple integrations - both use the same authentication credentials and regional optimization!