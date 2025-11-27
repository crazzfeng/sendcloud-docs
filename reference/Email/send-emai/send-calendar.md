---
title: Send Calendar Email
excerpt: >-
  Send calendar invitations with meeting information, supporting cancellation
  and updates. Learn about email configuration, recipient management, and best
  practices.
api:
  file: sendEmail.yaml
  operationId: send-calendar
hidden: false
link:
  new_tab: false
---
## Overview

Send calendar invitations containing meeting information with support for cancellation and updates of calendar events.

> **Important:** Please contact customer service for relevant permissions before using this interface.

## Key Configuration Guidelines

### Email Setup

<Accordion title="From Address Configuration" icon="envelope">

The system automatically handles the "from" field configuration:
- **Default**: `IFAXIN support<support@ifaxin.com>`
- **Custom Name**: If you provide a `fromName`, it will be used; otherwise defaults to "IFAXIN support"

</Accordion>

### Content Requirements

<Accordion title="Email Content Rules" icon="file-text">

**Content Priority:**
- Both `html` and `plain` cannot be empty
- If both are provided, `html` takes priority over `plain`
- Variables are supported in `subject`, `html`, and `plain` fields
- Special character `%` requires proper encoding in HTTP requests

</Accordion>

## Recipient Management

<Tabs>
<Tab title="Address Lists">

**Using Address Lists (with "to" parameter):**
- Maximum **5 addresses** per request
- Each email sent individually to recipients
- Parameters `cc`, `bcc`, and `xsmtpapi` are **disabled** when using address lists

</Tab>
<Tab title="XSMTPAPI">

**Using XSMTPAPI (without address lists):**
- Multiple recipients sent individually
- Parameters `to`, `cc`, and `bcc` are **disabled** when using XSMTPAPI
- Maximum **100 recipients** in `to` field of XSMTPAPI

</Tab>
</Tabs>

## Participant Configuration

<Cards columns="2">
<Card title="Participant Names" icon="users">

Use `participatorNames` to specify all meeting participants by name.

</Card>
<Card title="Participant Emails" icon="at">

Use `participatorEmails` to specify all participant email addresses. Generally, recipients should be included.

</Card>
</Cards>

## Advanced Features

### Custom Headers

<Accordion title="SC-Custom Headers" icon="cog">

Custom headers starting with `SC-Custom-` will be returned via WebHook:

**Requirements:**
- Both Key and Value must be strings
- Value cannot contain special character `.`
- When a Key is provided, the corresponding Value cannot be empty
- **Error 40902** will be returned if Value is empty

**Example:**
```
SC-Custom-EventType: meeting-invitation
SC-Custom-Priority: high
```

</Accordion>

### Recipient Limits

| Method | Field | Maximum Recipients |
|--------|-------|-------------------|
| Address Lists | `to` | 5 |
| Standard Email | `to`, `cc`, `bcc` | 100 each |
| XSMTPAPI | `to` | 100 |

## Best Practices

- ✅ Always include recipients in participant lists for calendar consistency
- ✅ Test variable substitution before sending to large groups
- ✅ Use meaningful custom headers for tracking and webhook processing
- ✅ Verify participant email addresses are valid before sending
- ⚠️ Contact customer service to ensure proper API permissions are configured