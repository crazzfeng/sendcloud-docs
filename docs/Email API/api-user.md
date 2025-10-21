---
title: API_USER
deprecated: false
hidden: false
link:
  new_tab: false
metadata:
  title: ' ​​Create API User for Email API & SMTP Authentication | Aurora SendCloud'
  description: >-
    Learn how to create and manage your ​​API_USER​​ and ​​API_KEY​​ for
    authenticating requests to the YourPlatformName ​​Email Delivery API​​ and
    ​​SMTP​​ service. This guide covers setting trigger/batch types, binding
    sending domains, and securely resetting your ​​API_KEY​​. Secure your
    integration and start sending today.
  robots: index
---
# API_USER Management Guide

This comprehensive guide covers everything you need to know about API_USER credentials, which serve as your primary authentication method for accessing our Email Delivery API and SMTP services.

## What is an API_USER?

An **API_USER** is a specialized credential system designed exclusively for programmatic email sending. Unlike your platform login account, API_USERs are purpose-built for:

- **Automated email sending** via API calls or SMTP
- **Secure authentication** without exposing your main account credentials  
- **Granular access control** with specific permissions and limitations
- **Isolated credential management** for different applications or environments

<Callout icon="💡" theme="info">
**Think of API_USERs as service accounts** - each one is tailored for a specific email sending purpose and can be managed independently.
</Callout>

## Creating Your First API_USER

When setting up an API_USER, you'll configure three essential properties that determine its capabilities and behavior.

### 1. Email Type Classification

Choose the appropriate type based on your sending needs:

<Cards columns="2">
  <Card title="Trigger Type" icon="zap">
    **Best for:** Transactional emails
    
    • Password resets
    • Order confirmations  
    • Account notifications
    • System alerts
    
    **Restrictions:** Cannot send marketing emails
  </Card>

  <Card title="Batch Type" icon="mail-bulk">
    **Best for:** Marketing campaigns
    
    • Newsletters
    • Promotional emails
    • Announcements
    • Marketing automation
    
    **Restrictions:** Cannot send transactional emails
  </Card>
</Cards>

<Callout icon="⚠️" theme="warn">
**Important:** Email type cannot be changed after creation. Plan carefully based on your intended use case.
</Callout>

### 2. Sending Domain Configuration

Every API_USER must be bound to an **authenticated sending domain**:

- **Domain Authentication Required:** The domain must be verified and have proper DNS records configured
- **Sender Reputation:** All emails will originate from this domain, affecting your sender reputation
- **Deliverability Impact:** Proper domain setup is crucial for inbox placement

<Accordion title="Domain Setup Checklist" icon="list-check">
Before binding a domain to your API_USER:

1. ✅ Domain is verified in your account
2. ✅ SPF record is properly configured
3. ✅ DKIM signing is enabled
4. ✅ DMARC policy is set (recommended)
5. ✅ Domain has positive sending reputation
</Accordion>

### 3. Tracking and Analytics

Enable tracking to monitor email performance:

**When Tracking is Enabled:**
- Open rate tracking
- Click-through tracking  
- Unsubscribe monitoring
- Spam complaint tracking
- Real-time delivery status

**Privacy Considerations:**
- Tracking uses invisible pixels and link redirects
- Consider privacy regulations in your jurisdiction
- Provide clear opt-out mechanisms for recipients

## API_KEY Management

The API_KEY functions as the "password" for your API_USER and requires careful handling.

<Tabs>
  <Tab title="Initial Setup">
    ### Generating Your First API_KEY

    1. **Navigate** to your API_USER management dashboard
    2. **Select** the API_USER you want to generate a key for
    3. **Click** "Generate API_KEY"
    4. **Copy and store** the key immediately - it's shown only once!

    ```bash
    # Example API_KEY format (do not use this actual key)
    api_key_1234567890abcdef1234567890abcdef
    ```

    <Callout icon="🔒" theme="danger">
    **Security Critical:** The API_KEY is displayed only once upon generation. If you lose it, you must reset to get a new one.
    </Callout>
  </Tab>

  <Tab title="Key Rotation">
    ### Resetting API_KEYs

    **Individual Reset:**
    - Generates a unique new key for one API_USER
    - Ideal for compromised credentials or routine rotation

    **Batch Reset:**
    - Assigns the **same new key** to multiple selected API_USERs
    - Useful for simplifying key management across similar services

    ### Grace Period Protection

    When you reset an API_KEY:
    - **New key:** Active immediately
    - **Old key:** Remains valid for 15 minutes
    - **Your applications:** Continue working during the transition

    This grace period prevents service disruption while you update your applications.
  </Tab>

  <Tab title="Best Practices">
    ### Key Management Best Practices

    **Storage:**
    - Use environment variables in production
    - Leverage secure credential management systems
    - Never commit keys to version control

    **Rotation Schedule:**
    - Rotate keys every 90-180 days minimum
    - Rotate immediately if compromise is suspected
    - Document rotation procedures for your team

    **Access Control:**
    - Limit who can generate/reset keys
    - Use separate API_USERs for different environments
    - Monitor key usage patterns for anomalies

    ```bash
    # Good: Using environment variables
    SENDCLOUD_API_USER=your_api_user
    SENDCLOUD_API_KEY=$SENDCLOUD_API_KEY

    # Bad: Hard-coding in source code
    api_key = "api_key_1234567890abcdef1234567890abcdef"
    ```
  </Tab>
</Tabs>

## Integration Examples

### API Integration

```bash
# Example API call using your API_USER credentials
curl -X POST "https://api.sendcloud.net/v3/mail/send" \
  -H "Content-Type: application/json" \
  -d '{
    "api_user": "your_api_user_name",
    "api_key": "your_api_key",
    "to": ["recipient@example.com"],
    "from": "sender@yourdomain.com",
    "subject": "Test Email",
    "html": "<p>Hello from SendCloud!</p>"
  }'
```

### SMTP Integration

```python
import smtplib
from email.mime.text import MIMEText
from email.mime.multipart import MIMEMultipart

# SMTP configuration using API_USER credentials
smtp_server = "smtp.sendcloud.net"
smtp_port = 587
api_user = "your_api_user_name"  
api_key = "your_api_key"

# Create and send email
msg = MIMEMultipart()
msg['From'] = "sender@yourdomain.com"
msg['To'] = "recipient@example.com"
msg['Subject'] = "Test Email via SMTP"

body = "Hello from SendCloud SMTP!"
msg.attach(MIMEText(body, 'plain'))

server = smtplib.SMTP(smtp_server, smtp_port)
server.starttls()
server.login(api_user, api_key)
server.send_message(msg)
server.quit()
```

## Troubleshooting Common Issues

<Accordion title="Authentication Failures" icon="exclamation-triangle">
**Symptoms:** 401 Unauthorized errors, authentication failures

**Common Causes:**
- Incorrect API_USER name or API_KEY
- Using expired credentials after reset
- API_USER not properly configured

**Solutions:**
1. Verify API_USER name matches exactly (case-sensitive)
2. Ensure API_KEY is current and not expired
3. Check if API_USER is active and not suspended
4. Regenerate API_KEY if in doubt
</Accordion>

<Accordion title="Domain-Related Errors" icon="globe">
**Symptoms:** Domain verification errors, sending failures

**Common Causes:**
- Sending domain not bound to API_USER
- Domain not properly authenticated
- DNS configuration issues

**Solutions:**
1. Verify domain is bound to the API_USER
2. Check domain authentication status
3. Validate DNS records (SPF, DKIM, DMARC)
4. Contact support for domain-specific issues
</Accordion>

<Accordion title="Email Type Restrictions" icon="ban">
**Symptoms:** Emails rejected due to type mismatch

**Common Causes:**
- Trigger API_USER trying to send marketing emails
- Batch API_USER trying to send transactional emails
- Incorrect email classification

**Solutions:**
1. Review your API_USER type configuration
2. Create separate API_USERs for different email types
3. Ensure email content matches API_USER type
4. Update your application logic accordingly
</Accordion>

## Security and Compliance

### Security Framework

<Cards columns="3">
  <Card title="Credential Protection" icon="shield-alt">
    • Secure storage practices
    • Regular key rotation
    • Access logging and monitoring
    • Immediate compromise response
  </Card>
  
  <Card title="Network Security" icon="network-wired">
    • HTTPS/TLS encryption required
    • IP allowlisting available
    • Rate limiting protection
    • DDoS mitigation
  </Card>
  
  <Card title="Compliance Ready" icon="check-circle">
    • GDPR compliance features
    • CAN-SPAM compliance tools
    • Audit trail maintenance
    • Data retention controls
  </Card>
</Cards>

### Compliance Considerations

- **Data Protection:** Ensure recipient data is handled according to applicable privacy laws
- **Consent Management:** Maintain proper opt-in/opt-out mechanisms
- **Audit Trails:** Keep records of email sending activities
- **Geographic Restrictions:** Understand regional sending limitations

## Advanced Configuration

### Multi-Environment Setup

For production applications, consider this API_USER structure:

```
Production Environment:
├── prod-transactional-api-user (Trigger Type)
├── prod-marketing-api-user (Batch Type)

Staging Environment:
├── staging-transactional-api-user (Trigger Type)
├── staging-marketing-api-user (Batch Type)

Development Environment:
├── dev-api-user (Trigger Type for testing)
```

### Monitoring and Alerting

Set up monitoring for:
- API_KEY usage patterns
- Authentication failure rates  
- Sending volume anomalies
- Domain reputation changes

## Next Steps

<Cards columns="2">
  <Card title="Create Your First API_USER" href="/getting-started/create-api-user" icon="plus-circle">
    Follow our step-by-step guide to create and configure your first API_USER
  </Card>
  
  <Card title="API Integration Guide" href="/api/integration-guide" icon="code">
    Learn how to integrate your API_USER with your application
  </Card>
  
  <Card title="SMTP Setup Guide" href="/smtp/configuration" icon="server">
    Configure SMTP sending using your API_USER credentials
  </Card>
  
  <Card title="Security Best Practices" href="/security/best-practices" icon="lock">
    Comprehensive security guidelines for production deployments
  </Card>
</Cards>

---

<Callout icon="🆘" theme="info">
**Need Help?** If you encounter issues not covered in this guide, our support team is ready to assist with API_USER configuration and troubleshooting.
</Callout>