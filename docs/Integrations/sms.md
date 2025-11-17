---
title: SMS
excerpt: >-
  Step-by-step tutorial for integrating SMS with Aurora SendCloud, including
  account setup, template creation, testing, and campaign management with all
  original screenshots preserved.
deprecated: false
hidden: true
metadata:
  robots: index
---
## SMS overview

Short Message Service, commonly abbreviated as SMS, is the text messaging component in mobile phone and other mobile device systems. As one of the most important messaging channels, SMS has been providing services in various ways for decades, such as personal communication, authentication, marketing, and notifications.

<Callout icon="💰" theme="default">
  ### How does Aurora SendCloud charge for SMS messages?

  1. SMS is charged based on the country/region and count of **SMS messages** sent to the recipients.
  2. The cost for sending SMS messages will be paid by [S-Wallet](doc:s-wallet) . Please ensure that there is sufficient balance in your [S-Wallet](doc:s-wallet) within the account.
</Callout>

### Calculation Rules for SMS Messages

The number of international SMS messages is determined based on the character encoding standard used, with two core scenarios as follows:

* GSM-7 Encoding (Default Standard)

  * 1 message= up to 160 characters; 
  * A SMS sending request exceeding 160 characters are split into multiple messages.(each subsequent message supports up to 153 characters due to segment overhead).
  * For the following characters, two characters will be used for encoding: 

  ```
  |€^{}[]~\
  ```
* Non-GSM-7 Encoding (Unicode/UCS-2)

  * 1 message= up to 70 characters; 
  * A SMS sending request exceeding 70 characters are split into multiple messages (each subsequent segment supports up to 67 characters due to segment overhead).

## Integrate SMS service

Step 1: Navigate to Integration Module

Log into your Aurora SendCloud platform dashboard, locate the left-side navigation menu on the Overview page, and click on the fourth icon labeled [Integrations]

Step 2: Begin SMS Connection

On the Integration page, locate the SMS service option and click the blue [Connect] button next to SMS.

<Image border={false} src="https://files.readme.io/7f4ec1b709d7c8d4e2c1131bb08ffe7519ff164b29dd27449c3d272077864c71-image.png" />

Step 3: Confirm Conntection

Confirm you want connect SMS service. And then, system will generate a SMS_USER and SMS_KEY for you .You can use them to send SMS messages via [Send SMS](ref:send_sms_message).

## SMS template

1. Navigate to Content → SMS in the left-side navigation bar, then click + New Template button in the upper-left corner.

   <Image border={false} src="https://files.readme.io/0f981ea7d352265c50309516326da98d96afbefacdb071aa0d216dd976e28f2f-image.png" />
2. Complete your template configuration with these required fields:
   1. Content Type:  Here are 3 content type you can choose Verification Code or  Industry Notice or Marketing. Choosing the right type can improve the approval rate.
   2. Template Name: The SMS template name.
   3. Content: The SMS message you want to send. You can use link and vars .
      1. You can insert custom variables in the text message, such as %name%. Note that the variable name cannot be Chinese, and% is an English format symbol. If you use variables in the template you need to fill in the variable example for each variables.
      2. You need to include one at the beginning and end of the link you filled in space，and begin with http:// or https://
   4. Applicant country/region: what countries you want send to. This is only for review and reference purposes, and is not intended as a limitation on usage.
3. Save or submit your template.
   1. Save the template means that you just want save the template for draft
   2. Only when you click the 'Save and submit for review' button ,then your template will be submitted to Aurora SendCloud for official review.
   3. Only approved templates can be used to send SMS messages.
4. Testing & Validation
   1. When your templates have been **approved**,you can test them. Locate an approved template in your template list and click [Test] in the actions column:

      <Image border={false} src="https://files.readme.io/35ac581275f100b5e594c6a24544bcf49f61d87d482819063147c1d6c918ce0b-image.png" />
   2. Enter recipient's mobile number and choose your SMS_USER in the test popup:

      <Image border={false} src="https://files.readme.io/028f6b29b77ecf47397513b756b0b221ab9297f987f440e46f5f15bd23c010e7-image.png" />
   3. Click [Send] to deliver test message

## How to send SMS messages

Use [Send SMS](ref:send_sms_message) API to SMS Messages

## How to check SMS messages status

<br />

## The SMS Sender ID

## The report of SMS
