---
title: Basic Send
excerpt: >-
  Send regular emails with custom content (supports attachments, CC/BCC, address
  lists, etc.)
api:
  file: sendEmail.yaml
  operationId: basic-email
hidden: false
link:
  new_tab: false
---
## Email Sending Guidelines

<Accordion title="Sender Configuration" icon="user">

### Default Sender Settings
- **Default Format**: `IFAXIN support<support@ifaxin.com>`
- **FromName Handling**: If "fromName" is empty, "IFAXIN support" will be automatically set as the sender name
- **Custom FromName**: When specified, your custom fromName will be used without modification

</Accordion>

<Accordion title="Recipient Management" icon="envelope">

### Using Address Lists
- **Parameter**: Use `to` parameter to specify address lists
- **Delivery Method**: Each address receives an individual email
- **Limitation**: Maximum 5 address lists allowed
- **Note**: When using address lists, `cc`, `bcc`, and `xsmtpapi` parameters become invalid

### Standard Recipients (Without Address Lists)
- **Primary Recipients**: Use `to` parameter (all recipients visible to each other)
- **CC Recipients**: Use `cc` parameter for carbon copy
- **BCC Recipients**: Use `bcc` parameter for blind carbon copy
- **Limit**: Maximum 100 recipients combined across `to`, `cc`, and `bcc`

### Advanced Recipients (xsmtpapi)
- **Individual Delivery**: Each recipient receives a separate email
- **Usage**: Specify recipients in `xsmtpapi` parameter
- **Limit**: Maximum 100 recipients in `to` field
- **Note**: When using xsmtpapi, standard `to`, `cc`, and `bcc` parameters become invalid

</Accordion>

<Accordion title="Content Requirements" icon="file-text">

### Content Fields
- **Required**: Either `html` or `plain` content must be provided (cannot both be empty)
- **Priority**: When both are provided, `html` takes priority over `plain`
- **Coexistence**: Contact customer service to enable both HTML and plain text rendering

### Content Summary
- **Usage**: `contentSummary` can only be used with `html` content
- **Requirement**: Without `html` content, `contentSummary` value becomes invalid

### Variable Support
- **Supported Fields**: Variables are allowed in `subject`, `html`, and `plain` content
- **Special Characters**: The "%" character requires special processing in HTTP requests

</Accordion>

<Accordion title="Advanced Features" icon="cogs">

### Attachments
- **Size Limit**: 10MB by default
- **Custom Limits**: Contact customer service for special requirements

### Return Receipt
- **Functionality**: Recipients can choose to send reading receipts to the sender
- **Control**: Optional feature that recipients control

### Custom Headers
- **Format**: Headers starting with "SC-Custom-" are returned via WebHook
- **Requirements**: 
  - Key and Value must be strings
  - Value cannot contain special characters like '.'
  - Value cannot be empty when Key is provided
- **Size Limit**: When using address lists, headers cannot exceed 1024 bytes
- **Error Handling**: Empty values result in error 40902: "Unknown exception occurred in mail processing"

</Accordion>

<Cards columns={2}>
  <Card title="Quick Reference" href="#recipient-limits" icon="list">
    **Recipient Limits**
    - Address Lists: Max 5
    - Standard Recipients: Max 100 total
    - xsmtpapi Recipients: Max 100
  </Card>
  
  <Card title="Content Guidelines" href="#content-rules" icon="edit">
    **Content Rules**
    - HTML or Plain required (not both empty)
    - HTML takes priority when both exist
    - Variables supported in all text fields
  </Card>
</Cards>

## Additional Resources

For more detailed information about email rules and SMTP API usage, see our [comprehensive guide](../guide/rule.md#x-smtpapi).