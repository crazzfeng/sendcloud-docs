---
title: Authentication
excerpt: >-
  Set up authentication for your API to help users manage their credentials
  securely.
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
# Authentication

This documentation will guide you through setting up and managing API credentials to ensure your applications can securely access Aurora SendCloud services.

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
    Every Email API request must include the following three parameters:

    | Parameter | Description           | Example                   |
    | --------- | --------------------- | ------------------------- |
    | `apiUser` | Your API username     | `mycompany_api`           |
    | `apiKey`  | Your API password/key | `abc123def456...`         |

    > ⚠️ **Important**: These parameters should be included directly in the request parameters, not passed through HTTPS basic authentication or request headers.
  </Tab>

  <Tab title="Request Examples">
    ```bash
    # GET request example
    curl "https://api.aurorasendcloud.com/email/send?apiUser=mycompany_api&apiKey=abc123def456&from=noreply@yourcompany.com&to=user@example.com&subject=Hello"

    # POST request example
    curl -X POST "https://api.aurorasendcloud.com/email/send" \
      -d "apiUser=mycompany_api" \
      -d "apiKey=abc123def456" \
      -d "from=noreply@yourcompany.com" \
      -d "to=user@example.com" \
      -d "subject=Hello World"
    ```
  </Tab>
</Tabs>

### Credential Management

<Accordion title="Obtaining and Creating Credentials" icon="key">
  **Where to find your credentials:**

  1. Log into your Aurora SendCloud account dashboard
  2. Navigate to **Email API** from the main menu
  3. Select the **API Key Management** section

  **Available actions:**

  * ✅ Create new `apiUser` (following platform naming conventions)
  * 🔑 Generate associated `apiKey` for users
  * 🔄 Reset existing `apiKey`
</Accordion>

<Accordion title="Secure Reset Process" icon="shield-alt">
  **Security mechanism when resetting API keys:**

  * ⏰ **15-minute grace period**: After reset, the old key remains valid for 15 minutes
  * 🔄 **Smooth transition**: Provides ample time to update integration configurations
  * ⚡ **Automatic expiration**: Old key automatically expires after the grace period

  **Best practices for key reset:**

  ```bash
  # 1. Reset the key in your dashboard
  # 2. Update your application configuration with the new key
  # 3. Ensure the update is completed within 15 minutes
  # 4. Monitor your application for successful authentication
  ```
</Accordion>

## SMS API Authentication

The SMS API also uses parameter-based authentication but with different parameter names and management processes.

### Authentication Parameters

<Tabs>
  <Tab title="Required Parameters">
    Every SMS API request must include the following two parameters:

    | Parameter | Description           | Example           |
    | --------- | --------------------- | ----------------- |
    | `smsUser` | Your SMS username     | `mycompany_sms`   |
    | `smsKey`  | Your SMS password/key | `xyz789uvw123...` |

    > ⚠️ **Important**: Similar to the Email API, these parameters need to be included directly in the request parameters.
  </Tab>

  <Tab title="Request Examples">
    ```bash
    # GET request example
    curl "https://api.aurorasendcloud.com/smsapi/send?smsUser=mycompany_sms&smsKey=xyz789uvw123&to=+1234567890&message=Hello"

    # POST request example
    curl -X POST "https://api.aurorasendcloud.com/smsapi/send" \
      -d "smsUser=mycompany_sms" \
      -d "smsKey=xyz789uvw123" \
      -d "to=+1234567890" \
      -d "message=Hello World"
    ```
  </Tab>
</Tabs>

### Credential Management

<Accordion title="Obtaining and Creating Credentials" icon="mobile-alt">
  **Where to find your credentials:**

  1. Log into your Aurora SendCloud account dashboard
  2. Navigate to **Integrations** from the main menu
  3. Select **SMS Manage** in the integrations section
  4. Access the **Send Settings** page

  **Available actions:**

  * ➕ Add new `smsUser` (following platform naming conventions)
  * 🔑 Generate associated `smsKey` for users
  * 🔄 Reset existing `smsKey`
</Accordion>

<Accordion title="Instant Reset Mechanism" icon="bolt">
  **Mechanism when resetting SMS keys:**

  * ⚡ **Immediate effect**: New `smsKey` takes effect immediately after reset
  * ❌ **Old key invalidated**: Old key is immediately invalidated with no grace period
  * 🚨 **Immediate update required**: Integration configuration must be updated immediately to avoid service interruption

  **Reset process recommendations:**

  ```bash
  # 1. Prepare your application for key update
  # 2. Reset the key in your dashboard
  # 3. Immediately update your application configuration
  # 4. Verify your application can authenticate successfully
  ```
</Accordion>

## Security Best Practices

<Columns layout="auto">
  <Column>
    ### 🔐 Credential Security

    * **Environment variable storage**: Store API keys in environment variables
    * **Regular rotation**: Periodically change API keys
    * **Least privilege**: Create different API users for different purposes
    * **Usage monitoring**: Regularly check API usage logs

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

    * **Error handling**: Implement proper authentication error handling
    * **Retry mechanisms**: Add retry logic for authentication failures
    * **Logging**: Log authentication-related events (without logging keys)
    * **Testing environment**: Use separate credentials for testing

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

  * Verify parameter names are correct (`apiUser`/`apiKey` vs `smsUser`/`smsKey`)
  * Confirm credentials haven't expired or been reset
  * Check parameter values don't have extra spaces or special characters
  * Ensure you're using the correct Aurora SendCloud API endpoint

  **⏱️ Unable to access after key reset**

  * **Email API**: Check if within the 15-minute grace period
  * **SMS API**: Confirm immediate update to new key was successful

  **📝 Parameter passing issues**

  * Ensure parameters are in request body or query string, not request headers
  * Verify URL encoding is correct for special characters
  * Check POST request Content-Type is set to `application/x-www-form-urlencoded`
  * **Email API**: Don't forget the required `from` parameter

  **🔗 Network and connectivity issues**

  * Verify API endpoint URLs are correct (api.aurorasendcloud.com)
  * Check firewall settings allow outbound HTTPS requests
  * Test with different network connections if possible
</Accordion>

***

<Callout icon="💡" theme="default">
  ### **Need Help?** If you encounter issues while setting up authentication, please check our [support documentation](/support) or contact our technical support team. We're here to help you get up and running quickly with Aurora SendCloud!
</Callout>

<Callout icon="🌟" theme="default">
  ### **Pro Tip**: Use environment variables to store your API credentials and never commit them to version control. Consider using a secrets management service for production deployments.
</Callout>