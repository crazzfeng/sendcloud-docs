---
title: Add Email Template
excerpt: >-
  Create a new email template with best practices for content handling and
  method selection
api:
  file: emailTemplate.yaml
  operationId: addTemplateGet
hidden: false
link:
  new_tab: false
---
## Overview

Create and configure new email templates for your application. Choose the appropriate HTTP method based on your content requirements.

## Method Selection

### When to Use GET
- Simple template creation with basic parameters
- Template names and IDs under 255 characters
- Standard ASCII characters only
- Quick template setup without complex formatting

### When to Use POST (Recommended)
- Templates with long content or descriptions
- Special characters, Unicode, or HTML entities
- Complex template structures with nested elements
- International characters or multilingual content
- Templates exceeding URL length limitations

## Best Practices

<Accordion title="Content Guidelines" icon="file-text">

### Template Naming
- Use descriptive, unique names (e.g., `welcome-email-v2`, `password-reset-notification`)
- Avoid special characters in template IDs
- Keep names under 100 characters for optimal compatibility

### Content Structure
- Use semantic HTML for better email client compatibility
- Test templates across different email clients
- Include fallback text for images
- Optimize for both desktop and mobile viewing

</Accordion>

<Accordion title="Security Considerations" icon="shield-alt">

### Data Validation
- Always validate input parameters before processing
- Sanitize HTML content to prevent XSS attacks
- Use proper encoding for special characters
- Implement rate limiting for template creation endpoints

### Access Control
- Verify user permissions before allowing template creation
- Log template creation activities for audit purposes
- Use HTTPS for all template-related API calls

</Accordion>

<Accordion title="Performance Tips" icon="tachometer-alt">

### Optimization
- Keep template content concise and focused
- Use external CSS files when possible
- Optimize images and use appropriate formats
- Consider template caching for frequently used templates

### Error Handling
- Provide clear error messages for validation failures
- Include specific guidance for fixing common issues
- Implement proper HTTP status codes (400, 401, 422, etc.)

</Accordion>

## Common Issues & Solutions

<Cards columns={2}>
  <Card title="Special Characters Not Displaying" icon="exclamation-triangle">
    **Solution:** Use POST method with proper UTF-8 encoding in Content-Type header
    ```
    Content-Type: application/json; charset=utf-8
    ```
  </Card>
  
  <Card title="Template Content Truncated" icon="cut">
    **Solution:** Switch from GET to POST method when content exceeds URL length limits (typically 2048 characters)
  </Card>
  
  <Card title="HTML Not Rendering" icon="code">
    **Solution:** Ensure proper HTML encoding and use appropriate email-safe HTML tags
  </Card>
  
  <Card title="Template Creation Fails" icon="times-circle">
    **Solution:** Check required fields, validate JSON structure, and verify authentication credentials
  </Card>
</Cards>

## Quick Start Example

```json
{
  "name": "welcome-email-template",
  "subject": "Welcome to Our Platform!",
  "content": "<html><body><h1>Welcome {{user_name}}!</h1><p>Thank you for joining us.</p></body></html>",
  "variables": ["user_name", "signup_date"],
  "type": "transactional"
}
```

> 📘 **Pro Tip:** Always use POST method for production templates to ensure maximum compatibility and prevent issues with special characters or long content.