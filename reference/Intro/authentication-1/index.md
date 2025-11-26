---
title: Authentication
excerpt: >-
  Complete guide to authenticating with Aurora SendCloud's Email and SMS APIs
  using parameter-based authentication methods
deprecated: false
hidden: false
link:
  new_tab: false
metadata:
  robots: index
---
# Authentication Overview

Aurora SendCloud uses parameter-based authentication to secure access to both Email and SMS APIs. This page provides an overview of authentication methods and requirements across all services.

## Authentication Methods

Aurora SendCloud supports different authentication parameters depending on the service:

### Email API Authentication
- **apiUser**: Your Email API username
- **apiKey**: Your Email API secret key

### SMS API Authentication  
- **smsUser**: Your SMS API username
- **smsKey**: Your SMS API secret key

## How Authentication Works

Authentication parameters can be passed in two ways:

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

Choose the appropriate endpoint based on your region:

- **Singapore Region**: `https://api.aurorasendcloud.com/`
- **US (Silicon Valley)**: `https://api-us.aurorasendcloud.com/`
- **Hong Kong SAR**: `https://api-hk.aurorasendcloud.com/`

## Security Best Practices

<Accordion title="API Key Management" icon="key">

- Store API keys securely and never expose them in client-side code
- Rotate API keys periodically for enhanced security
- Use environment variables or secure configuration management
- Implement proper access controls for API key storage

</Accordion>

<Accordion title="Request Security" icon="shield-alt">

- Always use HTTPS endpoints for API requests
- Validate SSL certificates in your HTTP client
- Implement request timeouts and retry logic
- Monitor API usage for unusual patterns

</Accordion>

## Common Authentication Scenarios

### Basic Email Sending
```bash
curl -X POST https://api.aurorasendcloud.com/api/mail/send \
  -d "apiUser=your_email_user" \
  -d "apiKey=your_email_key" \
  -d "from=sender@yourdomain.com" \
  -d "to=recipient@example.com" \
  -d "subject=Test Email" \
  -d "html=<h1>Hello World</h1>"
```

### Basic SMS Sending  
```bash
curl -X POST https://api.aurorasendcloud.com/smsapi/send \
  -d "smsUser=your_sms_user" \
  -d "smsKey=your_sms_key" \
  -d "templateId=12345" \
  -d "phone=+1234567890"
```

## Key Differences Between Services

<Cards columns="2">
  <Card title="Email API" icon="envelope">
    - Uses `apiUser` and `apiKey`
    - 15-minute grace period during key resets
    - Requires `from` parameter in requests
    - Supports template and regular sending
  </Card>
  
  <Card title="SMS API" icon="sms">
    - Uses `smsUser` and `smsKey`  
    - Immediate key updates (no grace period)
    - Requires approved template ID
    - Template-based sending only
  </Card>
</Cards>

## Quick Troubleshooting

### Authentication Failed (401 Unauthorized)
- ✅ Verify correct parameter names (`apiUser`/`apiKey` vs `smsUser`/`smsKey`)
- ✅ Check credentials haven't expired or been reset
- ✅ Ensure no extra spaces or special characters in values
- ✅ Confirm you're using the correct regional endpoint

### Parameter Issues
- ✅ Use request body or query string, not headers
- ✅ Set `Content-Type: application/x-www-form-urlencoded` for POST
- ✅ URL-encode special characters properly
- ✅ Include required `from` parameter for Email API

### Network Issues
- ✅ Verify API endpoint URLs are correct
- ✅ Check firewall allows outbound HTTPS requests
- ✅ Test with different network connections

## Next Steps

<Tabs>
  <Tab title="Email Authentication">
    Learn more about Email API authentication, including advanced security features and domain verification requirements.
  </Tab>
  
  <Tab title="SMS Authentication">
    Explore SMS API authentication details, template management, and regional considerations.
  </Tab>
  
  <Tab title="Error Handling">
    Understand common authentication errors and implement robust error handling in your applications.
  </Tab>
</Tabs>

## Getting Help

If you continue experiencing authentication issues:

1. Check the specific API documentation for your service
2. Verify your account status and API limits
3. Contact Aurora SendCloud support with request details
4. Review our comprehensive troubleshooting guides

---

*For detailed authentication guides specific to each service, please refer to the dedicated sections in the sidebar.*