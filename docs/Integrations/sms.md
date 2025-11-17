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
## How to integrate SMS service

Step 1: Navigate to Integration Module

Log into your Aurora SendCloud platform dashboard, locate the left-side navigation menu on the Overview page, and click on the fourth icon labeled [Integrations]

Step 2: Begin SMS Connection

On the Integration page, locate the SMS service option and click the blue [Connect] button next to SMS.

<Image border={false} src="https://files.readme.io/7f4ec1b709d7c8d4e2c1131bb08ffe7519ff164b29dd27449c3d272077864c71-image.png" />

Step 3: Confirm Conntection

Confirm you want connect SMS service. And then, system will generate a SMS_USER and SMS_KEY for you .You can use them to send SMS messages via [Send SMS](ref:send_sms_message).

## How to create a SMS template

1. Navigate to Content → SMS in the left-side navigation bar, then click + New Template button in the upper-left corner.

   <Image border={false} src="https://files.readme.io/0f981ea7d352265c50309516326da98d96afbefacdb071aa0d216dd976e28f2f-image.png" />
2. Complete your template configuration with these required fields:
   1. Content Type:  Here are 3 content type you can choose Verification Code or  Industry Notice or Marketing. Choosing the right type can improve the approval rate.
   2. Template Name: The SMS template name.
   3. Content: The SMS message you want to send. You can use link and vars .
      1. You can insert custom variables in the text message, such as %name%. Note that the variable name cannot be Chinese, and% is an English format symbol. If you use variables in the template you need to fill in the variable example for each variables.
      2. You need to include one at the beginning and end of the link you filled in space，and begin with http:// or https://
   4. Applicant country/region: what countries you want send to. This is only for review and reference purposes, and is not intended as a limitation on usage.

## How to send SMS message

## How to check SMS message status

## The SMS Sender ID

## The report of SMS
