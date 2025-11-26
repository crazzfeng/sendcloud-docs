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
<br />

```javascript
if (response.status === 401) {
  console.error('Authentication failed, please check API credentials');
  // Implement retry or alerting logic
}
```

## Troubleshooting Authentication Issues

### Authentication Failed (401 Unauthorized)

* Verify that parameter names are correct (`apiUser`/`apiKey` vs `smsUser`/`smsKey`)
* Confirm that credentials haven't expired or been reset
* Check that parameter values don't contain extra spaces or special characters
* Ensure you're using the correct Aurora SendCloud API endpoint

### Unable to Access After Key Reset

* **Email API**: Check if you're within the 15-minute grace period
* **SMS API**: Confirm that the immediate update to the new key was successful

### Parameter Passing Issues

* Ensure parameters are in the request body or query string, not in request headers
* Verify that URL encoding is correct for special characters
* Check that POST request Content-Type is set to `application/x-www-form-urlencoded`
* **Email API**: Don't forget the required `from` parameter

### Network and Connectivity Issues

* Verify that API endpoint URLs are correct
* Check that firewall settings allow outbound HTTPS requests
* Test with different network connections if possible
