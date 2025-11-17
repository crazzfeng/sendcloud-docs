---
title: SMS Integration & Management
excerpt: >-
  Complete guide for SMS integration with Aurora SendCloud, including setup,
  template creation, pricing, piece calculation, testing, and campaign
  management with detailed instructions and examples.
deprecated: false
hidden: true
link:
  new_tab: false
metadata:
  robots: index
---
## SMS Overview

Short Message Service (SMS) is a fundamental text messaging component in mobile communication systems. As one of the most critical messaging channels, SMS has been providing reliable services for decades across various use cases:

- **Personal Communication**: Direct messaging between individuals
- **Authentication**: Two-factor authentication and verification codes
- **Marketing**: Promotional campaigns and customer engagement
- **Notifications**: System alerts, reminders, and status updates

<Callout icon="💰" theme="default">
### SMS Pricing Structure

Aurora SendCloud charges for SMS based on:

1. **Geographic Location**: Costs vary by country/region of the recipient
2. **SMS Pieces**: Billing is calculated per SMS piece sent to recipients
3. **Payment Method**: All SMS costs are deducted from your [S-Wallet](doc:s-wallet) balance

**Important**: Ensure sufficient balance in your [S-Wallet](doc:s-wallet) before sending SMS campaigns.
</Callout>

## SMS Piece Calculation

Understanding how SMS pieces are calculated is crucial for cost estimation and message planning. The number of SMS pieces depends on the character encoding standard used:

### GSM-7 Encoding (Standard)

This is the default encoding for most SMS messages:

- **Single Piece**: Up to 160 characters
- **Multiple Pieces**: Messages exceeding 160 characters are automatically split
  - First piece: 160 characters maximum
  - Subsequent pieces: 153 characters maximum (due to concatenation overhead)

**Special Characters**: The following characters consume 2 character positions each:
```
| € ^ { } [ ] ~ \
```

### Unicode/UCS-2 Encoding (Non-GSM-7)

Used for messages containing special characters, emojis, or non-Latin scripts:

- **Single Piece**: Up to 70 characters
- **Multiple Pieces**: Messages exceeding 70 characters are split
  - First piece: 70 characters maximum
  - Subsequent pieces: 67 characters maximum (due to concatenation overhead)

## SMS Service Integration

### Step 1: Access Integration Module

1. Log into your Aurora SendCloud dashboard
2. Navigate to the Overview page
3. Locate the left-side navigation menu
4. Click the **Integrations** icon (fourth icon)

### Step 2: Connect SMS Service

1. On the Integration page, find the SMS service option
2. Click the blue **[Connect]** button next to SMS

<Image border={false} src="https://files.readme.io/7f4ec1b709d7c8d4e2c1131bb08ffe7519ff164b29dd27449c3d272077864c71-image.png" />

### Step 3: Complete Connection Setup

1. Confirm your intention to connect the SMS service
2. The system will automatically generate your credentials:
   - **SMS_USER**: Your unique SMS user identifier
   - **SMS_KEY**: Your authentication key for API access

3. Save these credentials securely - you'll need them to send SMS via the [Send SMS API](ref:send_sms_message)

## SMS Template Management

### Creating SMS Templates

1. **Navigate to Templates**
   - Go to **Content → SMS** in the left navigation
   - Click **+ New Template** in the upper-left corner

   <Image border={false} src="https://files.readme.io/0f981ea7d352265c50309516326da98d96afbefacdb071aa0d216dd976e28f2f-image.png" />

2. **Configure Template Settings**

   Complete the following required fields:

   **Content Type**: Select the appropriate category for better approval rates:
   - **Verification Code**: For OTP and authentication messages
   - **Industry Notice**: For transactional and informational messages  
   - **Marketing**: For promotional and marketing campaigns

   **Template Name**: Provide a descriptive name for easy identification

   **Content**: Create your SMS message with these guidelines:
   - Use clear, concise language
   - Include one space before and after any links
   - All links must begin with `http://` or `https://`
   - Variables must use English names with `%` symbols (e.g., `%name%`, `%code%`)
   - Provide example values for all variables used

   **Applicant Country/Region**: Select target countries (for review reference only)

3. **Save Your Template**
   - **Save**: Keeps template as draft for later editing
   - **Save and Submit for Review**: Submits template for official approval

   **Note**: Only approved templates can be used for actual SMS sending.

### Template Testing

Once your template is **approved**, you can test it:

1. **Access Test Function**
   - Locate your approved template in the template list
   - Click **[Test]** in the actions column

   <Image border={false} src="https://files.readme.io/35ac581275f100b5e594c6a24544bcf49f61d87d482819063147c1d6c918ce0b-image.png" />

2. **Configure Test Message**
   - Enter the recipient's mobile number
   - Select your SMS_USER from the dropdown
   - Fill in any required variable values

   <Image border={false} src="https://files.readme.io/028f6b29b77ecf47397513b756b0b221ab9297f987f440e46f5f15bd23c010e7-image.png" />

3. **Send Test**
   - Click **[Send]** to deliver the test message
   - Verify message receipt and formatting

## Sending SMS Messages

Use your generated **SMS_USER** and **SMS_KEY** credentials with the [Send SMS API](ref:send_sms_message) to send messages programmatically.

## SMS Message Status Tracking

Monitor your SMS campaigns with these status indicators:

- **Requested**: Aurora SendCloud has received your sending request and is processing it to the carrier
- **Delivered**: Message successfully sent and carrier reports successful delivery
- **Waiting Result**: Message sent but awaiting carrier delivery report
- **Failed**: Message sent but carrier reports delivery failure. Common reasons include:
  - **Device Issues**: Phone turned off or no signal coverage
  - **Content Issues**: Inappropriate message content flagged by carrier
  - **Timing Issues**: Message sent during restricted hours
- **Suppressed**: Aurora SendCloud blocked the message due to system or custom filtering rules

## SMS Sender ID Management

Sender ID allows you to customize who appears as the message sender, displaying your brand name or website name instead of a random number string.

### Default Behavior
If no custom Sender ID is registered, Aurora SendCloud automatically assigns a random ID for message delivery. You can send messages immediately without registration.

### Creating Custom Sender IDs

1. **Access Sender ID Settings**
   - Navigate to **Integration → SMS → Sender ID**

2. **Provide Registration Information**
   - **Sender ID**: Your desired sender name/identifier
   - **Applicant Country/Region**: Target regions for the Sender ID

3. **Complete Registration Process**
   - Aurora SendCloud staff will contact you
   - Submit any required registration materials as requested
   - Wait for approval (timing varies by region)

### Important Considerations

- **Geographic Variations**: Sender ID rules differ significantly between countries
- **Availability**: Not all countries support custom Sender ID registration
- **Costs**: Some regions may charge fees for Sender ID registration
- **Carrier Policies**: All registrations are subject to local carrier requirements and approval

<Callout icon="📋" theme="info">
### Best Practices for SMS Success

- Keep messages concise and under single-piece limits when possible
- Test templates thoroughly before launching campaigns
- Monitor delivery status and adjust strategies accordingly
- Ensure [S-Wallet](doc:s-wallet) has sufficient balance before sending
- Choose appropriate content types for better approval rates
- Use clear, professional language in all communications
</Callout>