---
title: Authentication
excerpt: >-
  Aurora SendCloud authentication overview with quick access to Email and SMS
  API authentication guides
deprecated: false
hidden: false
link:
  new_tab: false
metadata:
  robots: index
---
# Authentication Overview

Aurora SendCloud provides secure parameter-based authentication for both Email and SMS APIs. Choose your service below to get started with implementation.

## Authentication by Service

<Cards columns="2">
  <Card title="Email API Authentication" href="email-api-authentication" icon="envelope">
    Complete guide to Email API authentication, including `apiUser` and `apiKey` parameters, domain verification, and regional endpoints.
  </Card>

  <Card title="SMS API Authentication" href="sms-api-authentication" icon="sms">
    Comprehensive SMS API authentication guide covering `smsUser` and `smsKey` parameters, template management, and implementation.
  </Card>
</Cards>

## Quick Reference

### Credential Types

* **Email API**: `apiUser` + `apiKey`
* **SMS API**: `smsUser` + `smsKey`

### How to Pass Parameters

Authentication credentials can be sent via:

1. **Query Parameters** (GET requests)
   ```
   https://api.aurorasendcloud.com/api/endpoint?apiUser=your_user&apiKey=your_key
   ```

2. **Request Body** (POST requests)
   ```
   Content-Type: application/x-www-form-urlencoded

   apiUser=your_user&apiKey=your_key&other_params=values
   ```

## Regional Endpoints

### Email API

Choose the appropriate endpoint based on your region:

* **Singapore**: `https://api.aurorasendcloud.com/`
* **US (Silicon Valley)**: `https://api-us.aurorasendcloud.com/`
* **Hong Kong SAR**: `https://api-hk.aurorasendcloud.com/`

### SMS API

* **Global**: `https://api.aurorasendcloud.com/`

## Security Best Practices

<Accordion title="Credential Management" icon="key">
  * Store credentials securely and never expose them in client-side code
  * Use environment variables or secure configuration management
  * Rotate credentials periodically for enhanced security
  * Implement proper access controls for credential storage
</Accordion>

<Accordion title="Request Security" icon="shield-alt">
  * Always use HTTPS endpoints for API requests
  * Validate SSL certificates in your HTTP client
  * Implement request timeouts and retry logic
  * Monitor API usage for unusual patterns
</Accordion>

## Common Issues & Solutions

### Authentication Failed (401 Unauthorized)

* ✅ Verify correct parameter names for your service
* ✅ Check credentials haven't expired or been reset
* ✅ Ensure no extra spaces or special characters
* ✅ Confirm you're using the correct regional endpoint (Email API only)

### Parameter Format Issues

* ✅ Use request body or query string, not headers
* ✅ Set proper `Content-Type` for POST requests
* ✅ URL-encode special characters correctly
* ✅ Include all required parameters

## Get Started

<Tabs>
  <Tab title="Email Authentication">
    [→ Email API Authentication Guide](email-api-authentication)

    Learn about Email API credentials, domain verification, and multi-region setup.
  </Tab>

  <Tab title="SMS Authentication">
    [→ SMS API Authentication Guide](sms-api-authentication)

    Explore SMS API credentials, template requirements, and implementation examples.
  </Tab>


</Tabs>

## Need Help?

For detailed implementation instructions:

1. **Email API**: Visit the [Email Authentication](email-api-authentication) guide
2. **SMS API**: Visit the [SMS Authentication](sms-api-authentication) guide
3. **Support**: Contact our team with specific request details for faster resolution

***

_Choose your service above to access detailed authentication instructions and code examples._