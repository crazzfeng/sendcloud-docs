---
title: Regular Email Delivery
excerpt: >-
  Send regular emails with custom content using SendCloud API (supports
  attachments, CC/BCC, address lists, etc.)
api:
  file: deliverlies.yaml
  operationId: sendRegularEmail
hidden: false
link:
  new_tab: false
---
# Regular Email Delivery

Send regular emails with custom content using SendCloud's API. This endpoint supports attachments, CC/BCC, address lists, personalization, and more.

## Authentication Setup

This API uses `apiUser` and `apiKey` for authentication. For the best developer experience, you can configure these credentials once in ReadMe:

### Unified API Key Configuration

1. **Go to Configuration → Personalized Docs** in your ReadMe dashboard
2. **Set up Security Schemes** for SendCloud:
   - `apiUser`: Your SendCloud API User
   - `apiKey`: Your SendCloud API Key

3. **Enable Personalized Docs** so developers can:
   - Enter their credentials once
   - Have all code examples auto-populated
   - Test API calls directly from the docs

### Security Scheme Configuration

```yaml
components:
  securitySchemes:
    sendcloudAuth:
      type: apiKey
      in: query
      name: apiUser
      description: "SendCloud API User (get from SendCloud Console → API Settings)"
    sendcloudKey:
      type: apiKey
      in: query
      name: apiKey
      description: "SendCloud API Key (get from SendCloud Console → API Settings)"

security:
  - sendcloudAuth: []
    sendcloudKey: []
```

## Getting Your Credentials

To obtain your SendCloud API credentials:

1. **Log in to SendCloud Console**
2. **Navigate to**: API Settings → API_USER
3. **Copy your**:
   - `apiUser`: Your unique API user identifier
   - `apiKey`: Your secret API key

<Accordion title="⚠️ Security Best Practices" icon="shield-alt">

**Important Security Guidelines:**

- Never hardcode credentials in your application code
- Use environment variables or secure configuration management
- Rotate API keys regularly
- Monitor API usage for suspicious activity
- Restrict API permissions to minimum required scope

**For ReadMe Configuration:**
- Credentials are encrypted and stored securely
- Only visible to the authenticated user
- Can be easily updated or rotated
- Supports different environments (dev/staging/prod)

</Accordion>

## Basic Email Sending

### Required Parameters

- **apiUser**: Your SendCloud API user
- **apiKey**: Your SendCloud API key  
- **from**: Sender email address (must be from verified domain)
- **to**: Recipient email addresses (semicolon-separated)
- **subject**: Email subject line
- **html** or **plain**: Email content (at least one required)

### Simple Example

```python
import requests

url = "https://api2.sendcloud.net/api/mail/send"
data = {
    "apiUser": "YOUR_API_USER",  # Auto-filled with Personalized Docs
    "apiKey": "YOUR_API_KEY",    # Auto-filled with Personalized Docs
    "from": "noreply@example.com",
    "to": "recipient@example.com",
    "subject": "Welcome to Our Service",
    "html": "<h1>Welcome!</h1><p>Thank you for joining us.</p>"
}

response = requests.post(url, data=data)
print(response.json())
```

## Advanced Features

### Multiple Recipients with CC/BCC

```python
data = {
    "apiUser": "YOUR_API_USER",
    "apiKey": "YOUR_API_KEY",
    "from": "support@example.com",
    "to": "user1@example.com;user2@example.com",
    "cc": "manager@example.com",
    "bcc": "archive@example.com",
    "subject": "Team Update",
    "html": "<p>Important team announcement...</p>"
}
```

### With Attachments

```python
import requests

url = "https://api2.sendcloud.net/api/mail/send"
data = {
    "apiUser": "YOUR_API_USER",
    "apiKey": "YOUR_API_KEY", 
    "from": "billing@example.com",
    "to": "customer@example.com",
    "subject": "Your Invoice",
    "html": "<p>Please find your invoice attached.</p>"
}

files = {
    'attachments': open('invoice.pdf', 'rb')
}

response = requests.post(url, data=data, files=files)
```

### Using Address Lists

```python
data = {
    "apiUser": "YOUR_API_USER",
    "apiKey": "YOUR_API_KEY",
    "from": "newsletter@example.com", 
    "to": "subscribers@maillist.sendcloud.org",
    "subject": "Monthly Newsletter",
    "html": "<h2>This Month's Updates</h2><p>...</p>",
    "useAddressList": "true"
}
```

## Personalization with Variables

### Using X-SMTPAPI for Personalization

```python
import json

xsmtpapi = {
    "to": ["alice@example.com", "bob@example.com"],
    "sub": {
        "%name%": ["Alice", "Bob"],
        "%discount%": ["10%", "15%"]
    }
}

data = {
    "apiUser": "YOUR_API_USER",
    "apiKey": "YOUR_API_KEY",
    "from": "offers@example.com",
    "subject": "Special Offer for %name%",
    "html": "<p>Hi %name%!</p><p>Enjoy %discount% off your next order.</p>",
    "xsmtpapi": json.dumps(xsmtpapi)
}
```

## Response Handling

### Success Response

```json
{
    "statusCode": 200,
    "message": "request was successful", 
    "result": true,
    "info": {
        "emailIdList": [
            "1447054895514_15555555_32350_1350.sc-inbound0$recipient@example.com"
        ]
    }
}
```

### Error Response

```json
{
    "statusCode": 400,
    "message": "Invalid sender domain",
    "result": false
}
```

## Common Parameters

<Tabs>
<Tab title="Required Parameters">

| Parameter | Type | Description |
|-----------|------|-------------|
| `apiUser` | string | SendCloud API user (auto-filled) |
| `apiKey` | string | SendCloud API key (auto-filled) |
| `from` | string | Sender email (verified domain) |
| `to` | string | Recipients (semicolon-separated) |
| `subject` | string | Email subject line |
| `html` or `plain` | string | Email content |

</Tab>
<Tab title="Optional Parameters">

| Parameter | Type | Description |
|-----------|------|-------------|
| `fromName` | string | Sender display name |
| `cc` | string | CC recipients (semicolon-separated) |
| `bcc` | string | BCC recipients (semicolon-separated) |  
| `replyTo` | string | Reply-to address |
| `labelName` | string | Email label for tracking |
| `sendTags` | string | Custom tags (semicolon-separated) |
| `headers` | string | Custom headers (JSON format) |
| `attachments` | file | File attachments |

</Tab>
<Tab title="Advanced Options">

| Parameter | Type | Description |
|-----------|------|-------------|
| `xsmtpapi` | string | SMTP extension (JSON) |
| `sendRequestId` | string | Unique request ID |
| `respEmailId` | boolean | Return email IDs |
| `useNotification` | boolean | Enable notifications |
| `useAddressList` | boolean | Use address lists |

</Tab>
</Tabs>

## Error Codes

| Status Code | Description | Solution |
|-------------|-------------|----------|
| 200 | Success | Email queued for delivery |
| 400 | Bad Request | Check parameters and format |
| 401 | Authentication Failed | Verify apiUser/apiKey |
| 403 | Permission Denied | Check domain verification |
| 490 | Processing Error | Review email content |

## Rate Limits

- **Default**: 200 emails per minute
- **Burst**: Up to 500 emails in short periods
- **Daily**: Based on your account plan

## Best Practices

<Cards columns={2}>
<Card title="Domain Setup" icon="globe">
Verify your sending domain and configure SPF/DKIM records for better deliverability.
</Card>

<Card title="Content Quality" icon="edit">
Use proper HTML structure, avoid spam trigger words, and include unsubscribe links.
</Card>

<Card title="List Management" icon="users">
Maintain clean recipient lists and honor unsubscribe requests promptly.
</Card>

<Card title="Monitoring" icon="chart-line">
Track delivery rates, opens, clicks, and bounces to optimize performance.
</Card>
</Cards>

## Next Steps

- **[Email Templates](../templates)**: Use pre-approved templates for faster sending
- **[Address Lists](../address-lists)**: Manage recipient groups efficiently  
- **[Tracking & Analytics](../analytics)**: Monitor email performance
- **[Webhooks](../webhooks)**: Receive real-time event notifications