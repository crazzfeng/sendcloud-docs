---
title: SMS Integration Guide
excerpt: >-
  Complete guide to integrating SMS with Aurora SendCloud, covering setup,
  template creation, testing, and campaign management with detailed instructions
  and examples.
deprecated: false
hidden: true
link:
  new_tab: false
metadata:
  robots: index
---
## What is SMS?

Short Message Service (SMS) is a text messaging system used on mobile phones and other mobile devices. As one of the most widely adopted communication channels, SMS has served various purposes for decades, including personal communication, two-factor authentication, marketing campaigns, and system notifications.

<Callout icon="💰" theme="default">
  ### SMS Pricing with Aurora SendCloud

  1. SMS charges are calculated based on the destination country/region and the number of **SMS segments** sent to recipients.
  2. All SMS costs are deducted from your [S-Wallet](doc:s-wallet) balance. Please ensure sufficient funds are available in your [S-Wallet](doc:s-wallet) account before sending messages.
</Callout>

### How SMS Segments Are Calculated

The number of SMS segments depends on the character encoding standard used. There are two main scenarios:

**GSM-7 Encoding (Standard)**
* 1 segment = up to 160 characters
* Messages exceeding 160 characters are automatically split into multiple segments
* Each additional segment supports up to 153 characters (due to concatenation overhead)
* These special characters count as 2 characters each: `|€^{}[]~\`

**Unicode/UCS-2 Encoding (Non-GSM characters)**
* 1 segment = up to 70 characters
* Messages exceeding 70 characters are split into multiple segments
* Each additional segment supports up to 67 characters (due to concatenation overhead)

## Setting Up SMS Integration

### Step 1: Access the Integration Module

1. Log into your Aurora SendCloud dashboard
2. Navigate to the Overview page
3. In the left sidebar, click the fourth icon labeled **Integrations**

### Step 2: Connect SMS Service

1. On the Integration page, locate the SMS service option
2. Click the blue **Connect** button next to SMS

<Image border={false} src="https://files.readme.io/7f4ec1b709d7c8d4e2c1131bb08ffe7519ff164b29dd27449c3d272077864c71-image.png" />

### Step 3: Complete Connection Setup

1. Confirm that you want to connect the SMS service
2. The system will generate your unique **SMS_USER** and **SMS_KEY** credentials
3. Use these credentials to send SMS messages via the [Send SMS API](ref:send_sms_message)

## Creating SMS Templates

### Template Creation Process

1. **Navigate to Templates**
   - Go to **Content → SMS** in the left navigation bar
   - Click the **+ New Template** button in the upper-left corner

   <Image border={false} src="https://files.readme.io/0f981ea7d352265c50309516326da98d96afbefacdb071aa0d216dd976e28f2f-image.png" />

2. **Configure Your Template**
   
   Complete the following required fields:

   **Content Type**: Select from three options:
   - **Verification Code**: For OTP and authentication messages
   - **Industry Notice**: For transactional notifications
   - **Marketing**: For promotional campaigns
   
   *Choosing the correct type improves template approval rates.*

   **Template Name**: Enter a descriptive name for your SMS template

   **Content**: Write your SMS message with these guidelines:
   - Include custom variables using the format `%variable_name%` (e.g., `%name%`)
   - Variable names must be in English only
   - Use proper English formatting for the % symbol
   - Provide example values for each variable used
   - Add links with spaces before and after (e.g., ` https://example.com `)
   - All links must start with `http://` or `https://`

   **Applicant Country/Region**: Select target countries for sending
   *This is for review purposes only and doesn't restrict actual usage*

3. **Save Your Template**
   
   Choose one of these options:
   - **Save Template**: Saves as a draft for later editing
   - **Save and Submit for Review**: Submits template for Aurora SendCloud approval
   
   *Only approved templates can be used for sending SMS messages.*

### Testing Approved Templates

Once your template is **approved**, you can test it:

1. **Locate Your Template**
   - Find the approved template in your template list
   - Click **Test** in the actions column

   <Image border={false} src="https://files.readme.io/35ac581275f100b5e594c6a24544bcf49f61d87d482819063147c1d6c918ce0b-image.png" />

2. **Configure Test Settings**
   - Enter the recipient's mobile number
   - Select your **SMS_USER** from the dropdown

   <Image border={false} src="https://files.readme.io/028f6b29b77ecf47397513b756b0b221ab9297f987f440e46f5f15bd23c010e7-image.png" />

3. **Send Test Message**
   - Click **Send** to deliver the test message

## Sending SMS Messages

Use your **SMS_USER** and **SMS_KEY** credentials to send SMS messages through the [Send SMS API](ref:send_sms_message).

## Understanding SMS Message Status

Monitor your message delivery with these status indicators:

- **Requested**: Aurora SendCloud has received your request and is processing it with the carrier
- **Delivered**: Message successfully sent and confirmed delivered by the carrier
- **Waiting Result**: Message sent, awaiting delivery confirmation from the carrier
- **Failed**: Message sent but delivery failed according to carrier report

  Common failure reasons:
  - Device issues (powered off, no signal coverage)
  - Inappropriate message content
  - Restricted sending times
  
- **Suppressed**: Message blocked by Aurora SendCloud due to system or custom filters

## SMS Sender ID Management

A Sender ID determines how recipients see who sent the message. Instead of displaying a random number, you can show your brand name or website name.

**Default Behavior**: If you haven't registered a custom Sender ID, Aurora SendCloud automatically assigns a random ID. You can send messages without registration.

**Important Note**: Sender ID rules vary significantly by country. Not all countries support custom Sender IDs, and some may charge fees based on local carrier policies.

### Registering a Custom Sender ID

1. **Start Registration**
   - Navigate to **Integration → SMS → Sender ID**
   - Provide the following information:
     - Desired Sender ID
     - Target country or region

2. **Documentation Process**
   - Aurora SendCloud staff will contact you
   - Submit required registration materials as requested
   - Requirements vary by region

3. **Wait for Approval**
   - Registration and review times vary by region
   - You'll be notified once the process is complete