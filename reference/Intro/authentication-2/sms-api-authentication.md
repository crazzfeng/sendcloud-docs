---
title: SMS API Authentication
deprecated: false
hidden: false
metadata:
  robots: index
---
<br />

## SMS API Authentication

The SMS API also uses parameter-based authentication but with different parameter names and management processes.

### Required Parameters

Every SMS API request must include the following parameters:

| Parameter | Description   | Example         |
| --------- | ------------- | --------------- |
| smsUser   | Your SMS_USER | mycompany_sms   |
| smsKey    | Your SMS_KEY  | xyz789uvw123... |

> ⚠️ **Important**: Similar to the Email API, these parameters need to be included directly in the request parameters.

### Request Examples

**GET request example:**

```bash
curl "https://api.aurorasendcloud.com/smsapi/send?smsUser=mycompany_sms&smsKey=xyz789uvw123&to=+1234567890&message=Hello"
```

**POST request example:**

```bash
curl -X POST "https://api.aurorasendcloud.com/smsapi/send" \
  -d "smsUser=mycompany_sms" \
  -d "smsKey=xyz789uvw123" \
  -d "to=+1234567890" \
  -d "message=Hello World"
```

### Managing SMS API Credentials

**Where to find your credentials:**

1. Log into your Aurora SendCloud account dashboard
2. Navigate to **Integrations** from the main menu
3. Select **SMS Manage** in the integrations section
4. Access the **Send Settings** page

**Available actions:**

* ➕ Add new  SMS_USER
* 🔑 Generate associated  SMS_KEY for users
* 🔄 Reset existing SMS_KEY

### SMS_KEY Reset Process

When resetting SMS_KEY, the process is immediate:

* ⚡ **Immediate effect**: New SMS_KEY takes effect immediately after reset
* ❌ **Old key invalidated**: The old key is immediately invalidated with no grace period
* 🚨 **Immediate update required**: Integration configuration must be updated immediately to avoid service interruption

**Reset process recommendations:**

1. Prepare your application for key update
2. Reset the key in your dashboard
3. Immediately update your application configuration
4. Verify your application can authenticate successfully

## Security Best Practices

### Credential Security

* **Environment variable storage**: Store API keys in environment variables
* **Regular rotation**: Periodically change API keys
* **Least privilege**: Create different API users for different purposes
* **Usage monitoring**: Regularly check API usage logs

**Recommended environment variable setup:**

```bash
export EMAIL_API_USER="your_email_user"
export EMAIL_API_KEY="your_email_key"
export SMS_API_USER="your_sms_user"
export SMS_API_KEY="your_sms_key"
```

### Integration Best Practices

* **Error handling**: Implement proper authentication error handling
* **Retry mechanisms**: Add retry logic for authentication failures
* **Logging**: Log authentication-related events (without logging keys)
* **Testing environment**: Use separate credentials for testing

**Example error handling:**

```javascript
if (response.status === 401) {
  console.error('Authentication failed, please check API credentials');
  // Implement retry or alerting logic
}
```

##