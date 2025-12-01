---
title: Send Email via Template
excerpt: >-
  Send emails by calling preset templates through template call names,
  supporting dynamic parameter replacement.
api:
  file: sendEmail.yaml
  operationId: send-template-email
hidden: false
link:
  new_tab: false
---
## Important Guidelines

<Accordion title="Email Sender Configuration" icon="envelope">

**Default Sender**: All emails are sent from `IFAXIN support<support@ifaxin.com>` by default.

- If `fromName` is empty → automatically set to "IFAXIN support"
- If `fromName` is provided → use the provided value as-is

</Accordion>

<Accordion title="Address List vs Individual Recipients" icon="users">

### Using Address Lists (`useAddressList = true`)
- Specify recipients using the `to` parameter
- Each address receives an **individual email** (not visible to other recipients)  
- **Limit**: Maximum 5 addresses per request
- **Note**: `cc`, `bcc`, and `xsmtpapi` parameters are ignored

### Sending to Multiple Recipients (without address list)
Choose one of these methods:

**Method 1: Standard Multi-transmission**
- Use `to` for primary recipients (all recipients visible to each other)
- Use `cc` for carbon copy recipients  
- Use `bcc` for blind carbon copy recipients
- **Limit**: Maximum 100 recipients total across all fields

**Method 2: Individual Delivery via xsmtpapi**
- Specify recipients in `xsmtpapi` parameter
- Each recipient gets an **individual email** (not visible to others)
- **Limit**: Maximum 100 recipients in xsmtpapi
- **Note**: `to`, `cc`, and `bcc` parameters are ignored when using this method

</Accordion>

<Accordion title="Email Subject and Content" icon="edit">

### Subject Line
- **Default**: Uses the email template's subject
- **Fallback**: If both template subject and provided subject are empty, an error occurs
- **Variables**: Supports dynamic variables (e.g., `%variable_name%`)

### Email Body  
- Supports variables in both HTML (`html`) and plain text (`plain`) content
- **Special Character**: `%` must be properly encoded in HTTP requests

</Accordion>

<Accordion title="Advanced Features" icon="cog">

### Read Receipts
When enabled, recipients can choose to send reading confirmation back to the sender (`from` address).

### Custom Headers
- Headers starting with `"SC-Custom-"` will be returned via WebHook
- **Format**: Key:Value must be strings
- **Restriction**: Values cannot contain special characters like `.`
- **Required**: When a Key is provided, Value cannot be empty (error 40902 will occur)
- **Size Limit**: When using address lists, headers cannot exceed 1024 bytes

</Accordion>

## Quick Reference

| Feature | Limit | Notes |
|---------|-------|-------|
| Address List Recipients | 5 max | Individual delivery |
| Standard Recipients (to/cc/bcc) | 100 max total | Multi-transmission |
| xsmtpapi Recipients | 100 max | Individual delivery |
| Custom Headers | 1024 bytes | With address lists only |