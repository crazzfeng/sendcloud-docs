---
title: Email API Authentication
deprecated: false
hidden: false
metadata:
  robots: index
---
<br />

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
