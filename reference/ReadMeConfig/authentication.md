---
title: Authentication
excerpt: Set up the authentication for your API to help users manage their credentials.
api_config: authentication
hidden: true
icon: icon-key1
link:
  new_tab: false
---
# Authentication

This documentation will guide you through setting up and managing API credentials to ensure your applications can securely access our services.

<Cards columns="2">
  <Card title="Email API Authentication" href="#email-api-authentication" icon="envelope">
    Learn how to configure authentication parameters for Email API endpoints
  </Card>
  <Card title="SMS API Authentication" href="#sms-api-authentication" icon="sms">
    Learn how to configure authentication parameters for SMS API endpoints
  </Card>
</Cards>

## Email API Authentication

The Email API uses parameter-based authentication, requiring all requests to include your credentials as request parameters.

### Authentication Parameters

<Tabs>
  <Tab title="Required Parameters">
Every Email API request must include the following two parameters:

| Parameter | Description | Example |
|-----------|-------------|---------|
| `api_user` | Your API username | `mycompany_api` |
| `api_key` | Your API password/key | `abc123def456...` |

> ⚠️ **Important**: These parameters should be included directly in the request parameters, not passed through HTTPS basic authentication or request headers.
  </Tab>
  <Tab title="Request Examples">
```bash
# GET request example
curl "https://api.example.com/email/send?api_user=mycompany_api&api_key=abc123def456&to=user@example.com&subject=Hello"

# POST request example
curl -X POST "https://api.example.com/email/send" \
  -d "api_user=mycompany_api" \
  -d "api_key=abc123def456" \
  -d "to=user@example.com" \
  -d "subject=Hello World"
```
  </Tab>
</Tabs>

### Credential Management

<Accordion title="Obtaining and Creating Credentials" icon="key">
**Where to find your credentials:**

1. Log into your account dashboard
2. Navigate to **Email API** from the main menu
3. Select the **API Key Management** section

**Available actions:**
- ✅ Create new `API_USER` (following platform naming conventions)
- 🔑 Generate associated `API_KEY` for users
- 🔄 Reset existing `API_KEY`
</Accordion>

<Accordion title="Secure Reset Process" icon="shield-alt">
**Security mechanism when resetting API keys:**

- ⏰ **15-minute grace period**: After reset, the old key remains valid for 15 minutes
- 🔄 **Smooth transition**: Provides ample time to update integration configurations
- ⚡ **Automatic expiration**: Old key automatically expires after the grace period

**Best practices:**
```bash
# 1. Reset the key
# 2. Immediately test the new key
curl "https://api.example.com/test?api_user=youruser&api_key=NEW_KEY"
# 3. Update production environment configuration
# 4. Ensure switching is completed within 15 minutes
```
</Accordion>

## SMS API Authentication

The SMS API also uses parameter-based authentication but with different parameter names and management processes.

### Authentication Parameters

<Tabs>
  <Tab title="Required Parameters">
Every SMS API request must include the following two parameters:

| Parameter | Description | Example |
|-----------|-------------|---------|
| `sms_user` | Your SMS username | `mycompany_sms` |
| `sms_key` | Your SMS password/key | `xyz789uvw123...` |

> ⚠️ **Important**: Similar to the Email API, these parameters need to be included directly in the request parameters.
  </Tab>
  <Tab title="Request Examples">
```bash
# GET request example
curl "https://api.example.com/sms/send?sms_user=mycompany_sms&sms_key=xyz789uvw123&to=+1234567890&message=Hello"

# POST request example
curl -X POST "https://api.example.com/sms/send" \
  -d "sms_user=mycompany_sms" \
  -d "sms_key=xyz789uvw123" \
  -d "to=+1234567890" \
  -d "message=Hello World"
```
  </Tab>
</Tabs>

### Credential Management

<Accordion title="Obtaining and Creating Credentials" icon="mobile-alt">
**Where to find your credentials:**

1. Log into your account dashboard
2. Navigate to **Integrations** from the main menu
3. Select **SMS Manage** in the integrations section
4. Access the **Send Settings** page

**Available actions:**
- ➕ Add new `SMS_USER` (following platform naming conventions)
- 🔑 Generate associated `SMS_KEY` for users
- 🔄 Reset existing `SMS_KEY`
</Accordion>

<Accordion title="Instant Reset Mechanism" icon="bolt">
**Mechanism when resetting SMS keys:**

- ⚡ **Immediate effect**: New `SMS_KEY` takes effect immediately after reset
- ❌ **Old key invalidated**: Old key is immediately invalidated with no grace period
- 🚨 **Immediate update required**: Integration configuration must be updated immediately to avoid service interruption

**Reset process recommendations:**
```bash
# 1. Prepare update scripts
# 2. Reset the key
# 3. Immediately update configuration
# 4. Test the new key right away
curl "https://api.example.com/sms/test?sms_user=youruser&sms_key=NEW_SMS_KEY"
```
</Accordion>

## Security Best Practices

<Columns layout="auto">
  <Column>
### 🔐 Credential Security

- **Environment variable storage**: Store API keys in environment variables
- **Regular rotation**: Periodically change API keys
- **Least privilege**: Create different API users for different purposes
- **Usage monitoring**: Regularly check API usage logs

```bash
# Recommended environment variable setup
export EMAIL_API_USER="your_email_user"
export EMAIL_API_KEY="your_email_key"
export SMS_API_USER="your_sms_user"
export SMS_API_KEY="your_sms_key"
```
  </Column>
  <Column>
### 🛠️ Integration Best Practices

- **Error handling**: Implement proper authentication error handling
- **Retry mechanisms**: Add retry logic for authentication failures
- **Logging**: Log authentication-related events (without logging keys)
- **Testing environment**: Use separate test credentials

```javascript
// Example error handling
if (response.status === 401) {
  console.error('Authentication failed, please check API credentials');
  // Implement retry or alerting logic
}
```
  </Column>
</Columns>

## Troubleshooting

<Accordion title="Common Authentication Issues" icon="question-circle">
**🚫 Authentication Failed (401 Unauthorized)**
- Check parameter names are correct (`api_user`/`api_key` vs `sms_user`/`sms_key`)
- Confirm credentials haven't expired or been reset
- Verify parameter values don't have extra spaces or special characters

**⏱️ Unable to access after key reset**
- Email API: Check if within the 15-minute grace period
- SMS API: Confirm immediate update to new key

**📝 Parameter passing issues**
- Ensure parameters are in request body or query string, not request headers
- Check URL encoding is correct
- Verify POST request Content-Type settings
</Accordion>

<Accordion title="Testing Your Authentication Setup" icon="vial">
**Quick test script:**

```bash
#!/bin/bash
# Email API test
echo "Testing Email API authentication..."
curl -s "https://api.example.com/email/test?api_user=$EMAIL_API_USER&api_key=$EMAIL_API_KEY"

echo -e "\nTesting SMS API authentication..."
curl -s "https://api.example.com/sms/test?sms_user=$SMS_API_USER&sms_key=$SMS_API_KEY"
```

**Successful response example:**
```json
{
  "status": "success",
  "message": "Authentication successful",
  "user": "your_api_user"
}
```
</Accordion>

## Next Steps

After setting up authentication, you can:

<Cards columns="3">
  <Card title="API Reference" href="/api-reference" icon="book">
    View complete API endpoint documentation
  </Card>
  <Card title="Quick Start" href="/getting-started" icon="play-circle">
    Follow our quick start guide
  </Card>
  <Card title="SDK Documentation" href="/sdks" icon="code">
    Use our official SDK libraries
  </Card>
</Cards>

---

> 💡 **Need Help?** If you encounter issues while setting up authentication, please check our [support documentation](/support) or contact our technical support team.