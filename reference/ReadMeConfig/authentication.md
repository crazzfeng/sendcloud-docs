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
    Every Email API request must include the following two parameters:

    | Parameter | Description           | Example           |
    | --------- | --------------------- | ----------------- |
    | `apiUser` | Your API username     | `mycompany_api`   |
    | `apiKey`  | Your API password/key | `abc123def456...` |

    > ⚠️ **Important**: These parameters should be included directly in the request parameters, not passed through HTTPS basic authentication or request headers.
  </Tab>

  <Tab title="Request Examples">
    ```bash
    # GET request example
    curl "https://api.aurorasendcloud.com/email/send?apiUser=mycompany_api&apiKey=abc123def456&to=user@example.com&subject=Hello"

    # POST request example
    curl -X POST "https://api.aurorasendcloud.com/email/send" \
      -d "apiUser=mycompany_api" \
      -d "apiKey=abc123def456" \
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

  **Best practices:**

  ```bash
  # 1. Reset the key
  # 2. Immediately test the new key
  curl "https://api.aurorasendcloud.com/test?apiUser=youruser&apiKey=NEW_KEY"
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
    curl -X POST "https://api.aurorasendcloud.com/sms/send" \
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
  # 1. Prepare update scripts
  # 2. Reset the key
  # 3. Immediately update configuration
  # 4. Test the new key right away
  curl "https://api.aurorasendcloud.com/sms/test?smsUser=youruser&smsKey=NEW_SMS_KEY"
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
    * **Testing environment**: Use separate test credentials

    ```javascript
    // Example error handling
    if (response.status === 401) {
      console.error('Authentication failed, please check API credentials');
      // Implement retry or alerting logic
    }
    ```
  </Column>
</Columns>

## Code Examples

### JavaScript/Node.js Integration

<Accordion title="Email API Integration" icon="js-square">
  ```javascript
  // Email API example with proper authentication
  const axios = require('axios');

  class EmailAPIClient {
    constructor(apiUser, apiKey) {
      this.apiUser = apiUser;
      this.apiKey = apiKey;
      this.baseURL = 'https://api.aurorasendcloud.com/email';
    }

    async sendEmail(to, subject, message) {
      try {
        const response = await axios.post(`${this.baseURL}/send`, {
          apiUser: this.apiUser,
          apiKey: this.apiKey,
          to: to,
          subject: subject,
          message: message
        });
        
        return response.data;
      } catch (error) {
        if (error.response?.status === 401) {
          throw new Error('Authentication failed. Check your API credentials.');
        }
        throw error;
      }
    }
  }

  // Usage
  const client = new EmailAPIClient(
    process.env.EMAIL_API_USER,
    process.env.EMAIL_API_KEY
  );

  client.sendEmail('user@example.com', 'Hello', 'Test message')
    .then(result => console.log('Email sent:', result))
    .catch(error => console.error('Failed to send email:', error));
  ```
</Accordion>

<Accordion title="SMS API Integration" icon="mobile">
  ```javascript
  // SMS API example with proper authentication
  const axios = require('axios');

  class SMSAPIClient {
    constructor(smsUser, smsKey) {
      this.smsUser = smsUser;
      this.smsKey = smsKey;
      this.baseURL = 'https://api.aurorasendcloud.com/smsapi';
    }

    async sendSMS(to, message) {
      try {
        const response = await axios.post(`${this.baseURL}/send`, {
          smsUser: this.smsUser,
          smsKey: this.smsKey,
          to: to,
          message: message
        });
        
        return response.data;
      } catch (error) {
        if (error.response?.status === 401) {
          throw new Error('SMS authentication failed. Check your credentials.');
        }
        throw error;
      }
    }
  }

  // Usage
  const smsClient = new SMSAPIClient(
    process.env.SMS_API_USER,
    process.env.SMS_API_KEY
  );

  smsClient.sendSMS('+1234567890', 'Hello from SMS API')
    .then(result => console.log('SMS sent:', result))
    .catch(error => console.error('Failed to send SMS:', error));
  ```
</Accordion>

### Python Integration

<Accordion title="Python Example" icon="python">
  ```python
  import requests
  import os
  from typing import Optional, Dict, Any

  class APIClient:
      def __init__(self, base_url: str):
          self.base_url = base_url
          self.session = requests.Session()
      
      def _make_request(self, endpoint: str, params: Dict[str, Any]) -> Dict[str, Any]:
          """Make authenticated request to API"""
          try:
              response = self.session.post(f"{self.base_url}/{endpoint}", data=params)
              response.raise_for_status()
              return response.json()
          except requests.exceptions.HTTPError as e:
              if response.status_code == 401:
                  raise Exception("Authentication failed. Check your API credentials.")
              raise e

  class EmailAPI(APIClient):
      def __init__(self, api_user: str, api_key: str):
          super().__init__("https://api.aurorasendcloud.com/email")
          self.api_user = api_user
          self.api_key = api_key
      
      def send_email(self, to: str, subject: str, message: str) -> Dict[str, Any]:
          """Send email via Email API"""
          params = {
              'apiUser': self.api_user,
              'apiKey': self.api_key,
              'to': to,
              'subject': subject,
              'message': message
          }
          return self._make_request('send', params)

  class SMSAPI(APIClient):
      def __init__(self, sms_user: str, sms_key: str):
          super().__init__("https://api.aurorasendcloud.com/smsapi")
          self.sms_user = sms_user
          self.sms_key = sms_key
      
      def send_sms(self, to: str, message: str) -> Dict[str, Any]:
          """Send SMS via SMS API"""
          params = {
              'smsUser': self.sms_user,
              'smsKey': self.sms_key,
              'to': to,
              'message': message
          }
          return self._make_request('send', params)

  # Usage example
  if __name__ == "__main__":
      # Email API usage
      email_client = EmailAPI(
          os.getenv('EMAIL_API_USER'),
          os.getenv('EMAIL_API_KEY')
      )
      
      try:
          result = email_client.send_email(
              'user@example.com',
              'Test Subject',
              'Test message'
          )
          print(f"Email sent successfully: {result}")
      except Exception as e:
          print(f"Failed to send email: {e}")
      
      # SMS API usage
      sms_client = SMSAPI(
          os.getenv('SMS_API_USER'),
          os.getenv('SMS_API_KEY')
      )
      
      try:
          result = sms_client.send_sms('+1234567890', 'Hello from SMS API')
          print(f"SMS sent successfully: {result}")
      except Exception as e:
          print(f"Failed to send SMS: {e}")
  ```
</Accordion>

### PHP Integration

<Accordion title="PHP Example" icon="php">
  ```php
  <?php

  class AuroraSendCloudClient {
      private $baseUrl;
      
      public function __construct($baseUrl) {
          $this->baseUrl = rtrim($baseUrl, '/');
      }
      
      protected function makeRequest($endpoint, $params) {
          $url = $this->baseUrl . '/' . ltrim($endpoint, '/');
          
          $ch = curl_init();
          curl_setopt($ch, CURLOPT_URL, $url);
          curl_setopt($ch, CURLOPT_POST, true);
          curl_setopt($ch, CURLOPT_POSTFIELDS, http_build_query($params));
          curl_setopt($ch, CURLOPT_RETURNTRANSFER, true);
          curl_setopt($ch, CURLOPT_HTTPHEADER, [
              'Content-Type: application/x-www-form-urlencoded'
          ]);
          
          $response = curl_exec($ch);
          $httpCode = curl_getinfo($ch, CURLINFO_HTTP_CODE);
          curl_close($ch);
          
          if ($httpCode === 401) {
              throw new Exception('Authentication failed. Check your API credentials.');
          }
          
          if ($httpCode >= 400) {
              throw new Exception('API request failed with status code: ' . $httpCode);
          }
          
          return json_decode($response, true);
      }
  }

  class EmailAPI extends AuroraSendCloudClient {
      private $apiUser;
      private $apiKey;
      
      public function __construct($apiUser, $apiKey) {
          parent::__construct('https://api.aurorasendcloud.com/email');
          $this->apiUser = $apiUser;
          $this->apiKey = $apiKey;
      }
      
      public function sendEmail($to, $subject, $message) {
          $params = [
              'apiUser' => $this->apiUser,
              'apiKey' => $this->apiKey,
              'to' => $to,
              'subject' => $subject,
              'message' => $message
          ];
          
          return $this->makeRequest('send', $params);
      }
  }

  class SMSAPI extends AuroraSendCloudClient {
      private $smsUser;
      private $smsKey;
      
      public function __construct($smsUser, $smsKey) {
          parent::__construct('https://api.aurorasendcloud.com/sms');
          $this->smsUser = $smsUser;
          $this->smsKey = $smsKey;
      }
      
      public function sendSMS($to, $message) {
          $params = [
              'smsUser' => $this->smsUser,
              'smsKey' => $this->smsKey,
              'to' => $to,
              'message' => $message
          ];
          
          return $this->makeRequest('send', $params);
      }
  }

  // Usage example
  try {
      // Email API usage
      $emailClient = new EmailAPI(
          $_ENV['EMAIL_API_USER'],
          $_ENV['EMAIL_API_KEY']
      );
      
      $result = $emailClient->sendEmail(
          'user@example.com',
          'Test Subject',
          'Test message'
      );
      echo "Email sent successfully: " . json_encode($result) . "\n";
      
      // SMS API usage
      $smsClient = new SMSAPI(
          $_ENV['SMS_API_USER'],
          $_ENV['SMS_API_KEY']
      );
      
      $result = $smsClient->sendSMS('+1234567890', 'Hello from SMS API');
      echo "SMS sent successfully: " . json_encode($result) . "\n";
      
  } catch (Exception $e) {
      echo "Error: " . $e->getMessage() . "\n";
  }
  ?>
  ```
</Accordion>

## Testing Your Authentication Setup

<Accordion title="Authentication Test Scripts" icon="vial">
  **Quick test script for bash/shell:**

  ```bash
  #!/bin/bash

  # Configuration
  EMAIL_API_USER="your_email_user"
  EMAIL_API_KEY="your_email_key"
  SMS_API_USER="your_sms_user"
  SMS_API_KEY="your_sms_key"

  echo "🧪 Testing Email API authentication..."
  EMAIL_RESPONSE=$(curl -s -w "%{http_code}" \
    "https://api.aurorasendcloud.com/email/test?apiUser=$EMAIL_API_USER&apiKey=$EMAIL_API_KEY")

  EMAIL_STATUS="${EMAIL_RESPONSE: -3}"
  if [ "$EMAIL_STATUS" = "200" ]; then
    echo "✅ Email API authentication successful"
  else
    echo "❌ Email API authentication failed (HTTP $EMAIL_STATUS)"
  fi

  echo "🧪 Testing SMS API authentication..."
  SMS_RESPONSE=$(curl -s -w "%{http_code}" \
    "https://api.aurorasendcloud.com/sms/test?smsUser=$SMS_API_USER&smsKey=$SMS_API_KEY")

  SMS_STATUS="${SMS_RESPONSE: -3}"
  if [ "$SMS_STATUS" = "200" ]; then
    echo "✅ SMS API authentication successful"
  else
    echo "❌ SMS API authentication failed (HTTP $SMS_STATUS)"
  fi
  ```

  **Node.js test script:**

  ```javascript
  const axios = require('axios');

  async function testAuthentication() {
    const tests = [
      {
        name: 'Email API',
        url: 'https://api.aurorasendcloud.com/email/test',
        params: {
          apiUser: process.env.EMAIL_API_USER,
          apiKey: process.env.EMAIL_API_KEY
        }
      },
      {
        name: 'SMS API',
        url: 'https://api.aurorasendcloud.com/sms/test',
        params: {
          smsUser: process.env.SMS_API_USER,
          smsKey: process.env.SMS_API_KEY
        }
      }
    ];

    for (const test of tests) {
      try {
        console.log(`🧪 Testing ${test.name} authentication...`);
        const response = await axios.get(test.url, { params: test.params });
        console.log(`✅ ${test.name} authentication successful`);
        console.log(`   Response:`, response.data);
      } catch (error) {
        if (error.response?.status === 401) {
          console.log(`❌ ${test.name} authentication failed: Invalid credentials`);
        } else {
          console.log(`❌ ${test.name} test failed:`, error.message);
        }
      }
    }
  }

  testAuthentication();
  ```
</Accordion>

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

  **🔗 Network and connectivity issues**

  * Verify API endpoint URLs are correct (api.aurorasendcloud.com)
  * Check firewall settings allow outbound HTTPS requests
  * Test with different network connections if possible

  **🔄 Rate limiting errors**

  * Check if you've exceeded API rate limits
  * Implement exponential backoff for retry logic
  * Monitor your API usage patterns
</Accordion>

<Accordion title="Debug Mode and Logging" icon="bug">
  **Enable debug logging in your applications:**

  ```javascript
  // JavaScript debug example
  const debug = require('debug')('api:auth');

  async function makeAuthenticatedRequest(url, params) {
    debug('Making authenticated request to:', url);
    debug('Parameters (excluding sensitive data):', {
      ...params,
      apiKey: '[REDACTED]',
      smsKey: '[REDACTED]'
    });
    
    try {
      const response = await axios.post(url, params);
      debug('Request successful, status:', response.status);
      return response.data;
    } catch (error) {
      debug('Request failed:', error.message);
      if (error.response) {
        debug('Response status:', error.response.status);
        debug('Response headers:', error.response.headers);
      }
      throw error;
    }
  }
  ```

  **Python logging example:**

  ```python
  import logging

  # Configure logging
  logging.basicConfig(level=logging.DEBUG)
  logger = logging.getLogger(__name__)

  def make_authenticated_request(url, params):
      # Log request (without sensitive data)
      safe_params = {k: '[REDACTED]' if 'key' in k.lower() else v 
                     for k, v in params.items()}
      logger.debug(f"Making request to {url} with params: {safe_params}")
      
      try:
          response = requests.post(url, data=params)
          logger.debug(f"Request successful, status: {response.status_code}")
          return response.json()
      except requests.exceptions.RequestException as e:
          logger.error(f"Request failed: {e}")
          raise
  ```
</Accordion>

## Migration and Updates

<Accordion title="Updating Parameter Names in Legacy Code" icon="sync-alt">
  If you're migrating from older versions that used different parameter naming conventions:

  **Migration checklist:**

  * [ ] Update all instances of `api_user` to `apiUser`
  * [ ] Update all instances of `api_key` to `apiKey`
  * [ ] Update all instances of `sms_user` to `smsUser`
  * [ ] Update all instances of `sms_key` to `smsKey`
  * [ ] Update all API base URLs to `api.aurorasendcloud.com`
  * [ ] Test all API endpoints with new parameter names
  * [ ] Update environment variables and configuration files
  * [ ] Update documentation and code comments

  **Automated migration script:**

  ```bash
  #!/bin/bash
  # Script to update parameter names in source code

  echo "🔄 Migrating API parameter names and URLs..."

  # Find and replace parameter names in all relevant files
  find . -type f \( -name "*.js" -o -name "*.py" -o -name "*.java" -o -name "*.php" \) \
    -exec sed -i 's/api_user/apiUser/g' {} \; \
    -exec sed -i 's/api_key/apiKey/g' {} \; \
    -exec sed -i 's/sms_user/smsUser/g' {} \; \
    -exec sed -i 's/sms_key/smsKey/g' {} \; \
    -exec sed -i 's/api\.example\.com/api.aurorasendcloud.com/g' {} \;

  echo "✅ Parameter name and URL migration completed"
  echo "⚠️  Please review changes and test thoroughly before deploying"
  ```
</Accordion>

<br />

<br />



***

<Callout icon="💡" theme="default">
  ### **Need Help?** If you encounter issues while setting up authentication, please check our [support documentation](/support) or contact our technical support team. We're here to help you get up and running quickly with Aurora SendCloud!
</Callout>

<Callout icon="🌟" theme="default">
  ### **Pro Tip**: Use environment variables to store your API credentials and never commit them to version control. Consider using a secrets management service for production deployments.
</Callout>
