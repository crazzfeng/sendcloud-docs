---
title: Authentication
excerpt: >-
  This documentation will guide you through setting up and managing API
  credentials to ensure your applications can securely access Aurora SendCloud
  services.
api:
  file: send.json
  operationId: get_new-endpoint
api_config: authentication
hidden: false
icon: icon-key1
link:
  new_tab: false
metadata:
  description: >-
    Set up the authentication for your API to help users manage their
    credentials.
---
## Email API Authentication

The Email API uses parameter-based authentication, requiring all requests to include your credentials as request parameters.

### Required Parameters

Every Email API request must include the following parameters:

| Parameter | Description                   | Example         |
| --------- | ----------------------------- | --------------- |
| apiUser   | Your [API_USER](doc:api-user) | mycompany_api   |
| apiKey    | Your API_KEY                  | abc123def456... |

> ⚠️ **Important**: These parameters must be included directly in the request parameters, not passed through HTTPS basic authentication or request headers.

### Request Examples

**GET request example:**

```bash
curl "https://api.aurorasendcloud.com/email/send?apiUser=mycompany_api&apiKey=abc123def456&from=noreply@yourcompany.com&to=user@example.com&subject=Hello"
```

**POST request example:**

```bash
curl -X POST "https://api.aurorasendcloud.com/email/send" \
  -d "apiUser=mycompany_api" \
  -d "apiKey=abc123def456" \
  -d "from=noreply@yourcompany.com" \
  -d "to=user@example.com" \
  -d "subject=Hello World"
```

### Managing Email API Credentials

**Where to find your credentials:**

1. Log into your Aurora SendCloud account dashboard
2. Navigate to **Email API** from the main menu
3. Select the **API_USER Management** section

**Available actions:**

* ✅ Create new  API_USER  (following platform naming conventions)
* 🔑 Generate associated API_KEY for users
* 🔄 Reset existing API_KEY

### Email API_KEY Reset Process

When resetting API_KEY for the Email API, Aurora SendCloud provides a secure 15-minute grace period:

* ⏰ **15-minute grace period**: After reset, the old key remains valid for 15 minutes
* 🔄 **Smooth transition**: Provides ample time to update integration configurations
* ⚡ **Automatic expiration**: The old key automatically expires after the grace period

**Best practices for key reset:**

1. Reset the key in your dashboard
2. Update your application configuration with the new key
3. Ensure the update is completed within 15 minutes
4. Monitor your application for successful authentication

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

## Troubleshooting Authentication Issues

### Authentication Failed (401 Unauthorized)

* Verify parameter names are correct (`apiUser`/`apiKey` vs `smsUser`/`smsKey`)
* Confirm credentials haven't expired or been reset
* Check parameter values don't have extra spaces or special characters
* Ensure you're using the correct Aurora SendCloud API endpoint

### Unable to Access After Key Reset

* **Email API**: Check if you're within the 15-minute grace period
* **SMS API**: Confirm immediate update to new key was successful

### Parameter Passing Issues

* Ensure parameters are in request body or query string, not request headers
* Verify URL encoding is correct for special characters
* Check POST request Content-Type is set to `application/x-www-form-urlencoded`
* **Email API**: Don't forget the required `from` parameter

### Network and Connectivity Issues

* Verify API endpoint URLs are correct (api.aurorasendcloud.com)
* Check firewall settings allow outbound HTTPS requests
* Test with different network connections if possible

***

<br />

<Callout icon="🌟" theme="default">
  **Pro Tip**: Use environment variables to store your API credentials and never commit them to version control. Consider using a secrets management service for production deployments.
</Callout>

<Callout icon="💡" theme="default">
  **Need Help?** If you encounter issues while setting up authentication, please check our <Anchor label="User Guide" target="_blank" href="https://docs.aurorasendcloud.com/">User Guide</Anchor> or <Anchor label="Contact Us" target="_blank" href="https://www.aurorasendcloud.com/contact">Contact Us</Anchor> . We're here to help you get up and running quickly with Aurora SendCloud!
</Callout>

<Callout icon="💡" theme="default">

</Callout>

<Callout icon="🌟" theme="default">
  **Pro Tip**: Use environment variables to store your API credentials and never commit them to version control. Consider using a secrets management service for production deployments.
</Callout>

<br />
