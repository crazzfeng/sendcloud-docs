---
title: SMS
excerpt: >-
  Complete guide for SMS integration with Aurora SendCloud, including setup,
  template creation, pricing, piece calculation, testing, and campaign
  management with detailed instructions and examples.
deprecated: false
hidden: true
link:
  new_tab: false
metadata:
  description: >-
    Complete guide for SMS integration with Aurora SendCloud, including setup,
    template creation, pricing, piece calculation, testing, and campaign
    management with detailed instructions and examples.
  robots: index
---
## SMS Overview

Short Message Service (SMS) is a fundamental text messaging component in mobile communication systems. As one of the most critical messaging channels, SMS has been providing reliable services for decades across various use cases:

* **OTP**: Two-factor authentication and verification codes
* **Marketing**: Promotional campaigns and customer engagement
* **Notification**: System alerts, reminders, and status updates

<br />

<Callout icon="💰" theme="default">
  ### How does Aurora SendCloud charge for SMS messages?

  1. SMS is charged based on the country/region and the number of **SMS pieces** sent to recipients.
  2. The cost for sending SMS messages will be paid through [S-Wallet](doc:s-wallet). Please ensure that there is sufficient balance in your [S-Wallet](doc:s-wallet) account.
</Callout>

## SMS Piece Calculation

Understanding how SMS pieces are calculated is crucial for cost estimation and message planning. The number of SMS pieces depends on the character encoding standard used:

### GSM-7 Encoding ( Standard)

* 1 piece = up to 160 characters
* SMS message requests exceeding 160 characters are split into multiple pieces (each subsequent piece supports up to 153 characters due to piece overhead)
* The following characters use two characters for encoding:

```
|€^{}[]~\
```

### Non-GSM-7 Encoding (Unicode/UCS-2)

* 1 piece = up to 70 characters
* SMS messages exceeding 70 characters are split into multiple pieces (each subsequent piece supports up to 67 characters due to piece overhead)

## Integrate SMS Service

**Step 1: Navigate to Integration Module**

Log into your Aurora SendCloud platform dashboard, locate the left-side navigation menu on the Overview page, and click on the fourth icon labeled [Integrations].

**Step 2: Begin SMS Connection**

On the Integration page, locate the SMS service option and click the blue [Connect] button next to SMS.

<Image border={false} src="https://files.readme.io/7f4ec1b709d7c8d4e2c1131bb08ffe7519ff164b29dd27449c3d272077864c71-image.png" />

**Step 3: Confirm Connection**

Confirm that you want to connect the SMS service. The system will then generate an SMS_USER and SMS_KEY for you. You can use these credentials to send SMS messages via [Send SMS](ref:send_sms_message).

## SMS Template

1. Navigate to Content → SMS in the left-side navigation bar, then click the + New Template button in the upper-left corner.

   <Image border={false} src="https://files.readme.io/0f981ea7d352265c50309516326da98d96afbefacdb071aa0d216dd976e28f2f-image.png" />

2. Complete your template configuration with these required fields:
   1. **Content Type**: Choose from 3 content types: OTP,  Notification , or Marketing. Choosing the right type can improve the approval rate.
   2. **Template Name**: The SMS template name.
   3. **Content**: The SMS message you want to send. You can use links and variables.
      1. You can insert custom variables in the text message, such as %name%. Note that the variable name cannot be in Chinese, and % must be an English format symbol. If you use variables in the template, you need to provide a variable example for each variable.
      2. You need to include one space at the beginning and end of any link you add, and links must begin with http:// or https://
   4. **Applicant Country/Region**: Select the countries you want to send to. This is for review and reference purposes only and is not intended as a limitation on usage.

3. Save or submit your template.
   1. **Save the template** means you want to save the template as a draft.
   2. Only when you click the 'Save and submit for review' button will your template be submitted to Aurora SendCloud for official review.
   3. Only approved templates can be used to send SMS messages.

4. **Testing & Validation**
   1. When your templates have been **approved**, you can test them. Locate an approved template in your template list and click [Test] in the actions column:

      <Image border={false} src="https://files.readme.io/35ac581275f100b5e594c6a24544bcf49f61d87d482819063147c1d6c918ce0b-image.png" />

   2. Enter the recipient's mobile number and choose your SMS_USER in the test popup:

      <Image border={false} src="https://files.readme.io/028f6b29b77ecf47397513b756b0b221ab9297f987f440e46f5f15bd23c010e7-image.png" />

   3. Click [Send] to deliver the test message.

## How to Send SMS Messages

Use your SMS_USER and SMS_KEY to send SMS messages via [Send SMS](ref:send_sms_message).

## SMS Message Status

* **Requested**: The sending request has been received by Aurora SendCloud and is in the process of being sent to the carrier.
* **Delivered**: The message has been sent, and the report from the carrier shows that the message has been delivered.
* **Waiting Result**: The message has been sent, but there is no report from the carrier yet.
* **Failed**: The message has been sent, but the report from the carrier shows that the message was not delivered. Reasons for failure include:
  * Device issues: turned off, no signal
  * Your message content is inappropriate
  * Your message sending time is not allowed
* **Suppressed**: The message is suppressed by Aurora SendCloud due to system interception or custom interception.

## SMS Sender ID

The Sender ID shows who sent the message. With a Sender ID, you can send SMS from a custom sender (brand name or website name) instead of a random string of numbers.

If you have not registered a Sender ID, Aurora SendCloud will randomly assign an ID for you to send messages. Therefore, you can send messages without registering.

The rules vary greatly from country to country. Not all countries offer Sender ID registration, and some countries charge for the ID, subject to local carrier policies.

### Create Your Sender ID

1. Go to Integration > SMS > Sender ID. You need to provide the following information for registration:
   1. Sender ID
   2. Applicant country or region

2. Our staff will contact you and you may need to submit the relevant Sender ID registration materials as requested.

3. Wait for registration and review. Review times may vary by region.
