---
title: Authentication
excerpt: >-
  Authentication overview and quick access to Email and SMS API authentication
  guides for Aurora SendCloud services
deprecated: false
hidden: false
link:
  new_tab: false
metadata:
  robots: index
---
# Authentication Overview

Aurora SendCloud provides secure parameter-based authentication for both Email and SMS APIs. This page serves as your starting point for understanding and implementing authentication across all services.

## Authentication Methods by Service

<Cards columns="2">
  <Card title="Email API Authentication" href="/authentication/email" icon="envelope">
    Complete guide to Email API authentication using `apiUser` and `apiKey` parameters, including domain verification and advanced security features.
  </Card>
  
  <Card title="SMS API Authentication" href="/authentication/sms" icon="sms">
    Comprehensive SMS API authentication guide covering `smsUser` and `smsKey` parameters, template management, and regional considerations.
  </Card>
</Cards>

## Quick Reference

### Parameter Types
- **Email API**: `apiUser` + `apiKey`
- **SMS API**: `smsUser` + `smsKey`

### Authentication Methods
Authentication parameters can be passed via:

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

## Common Authentication Issues

### Authentication Failed (401 Unauthorized)
- ✅ Verify correct parameter names (`apiUser`/`apiKey` vs `smsUser`/`smsKey`)
- ✅ Check credentials haven't expired or been reset
- ✅ Ensure no extra spaces or special characters in values
- ✅ Confirm you're using the correct regional endpoint

### Parameter Issues
- ✅ Use request body or query string, not headers
- ✅ Set `Content-Type: application/x-www-form-urlencoded` for POST
- ✅ URL-encode special characters properly
- ✅ Include all required parameters for your specific API

### Network Issues
- ✅ Verify API endpoint URLs are correct
- ✅ Check firewall allows outbound HTTPS requests
- ✅ Test with different network connections

## Get Started

<Tabs>
  <Tab title="Email Authentication">
    [Set up Email API authentication →](/authentication/email)
    
    Learn about Email API credentials, domain verification, and implementation examples.
  </Tab>
  
  <Tab title="SMS Authentication">
    [Set up SMS API authentication →](/authentication/sms)
    
    Explore SMS API credentials, template requirements, and regional setup.
  </Tab>
  
  <Tab title="Error Handling">
    [View error handling guide →](/error-handling)
    
    Understand common authentication errors and implement robust error handling.
  </Tab>
</Tabs>

## Need Help?

If you're experiencing authentication issues:

1. **Check the specific guide**: Visit the [Email](/authentication/email) or [SMS](/authentication/sms) authentication pages
2. **Verify account status**: Ensure your API limits and account status are active
3. **Contact support**: Reach out with specific request details for faster resolution
4. **Review examples**: Check our implementation examples in each service guide

---

*For detailed authentication instructions and code examples, please visit the specific service pages linked above.*