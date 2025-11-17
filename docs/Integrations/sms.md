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
    Step-by-step tutorial for integrating SMS with Aurora SendCloud, including
    account setup, template creation, testing, and campaign management with all
    original screenshots preserved.
  robots: index
---
## SMS Overview

Short Message Service (SMS) is a fundamental text messaging component in mobile communication systems. As one of the most critical messaging channels, SMS has been providing reliable services for decades across various use cases:

* **Personal Communication**: Direct messaging between individuals
* **Authentication**: Two-factor authentication and verification codes
* **Marketing**: Promotional campaigns and customer engagement
* **Notifications**: System alerts, reminders, and status updates

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
   1. **Content Type**: Choose from 3 content types: Verification Code, Industry Notice, or Marketing. Choosing the right type can improve the approval rate.
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

## Sending SMS Messages

<Tabs>
  <Tab title="API Integration">
    ### Using the Send SMS API
    
    Once you have your SMS_USER and SMS_KEY credentials from the integration setup, you can send SMS messages programmatically using the [Send SMS API](ref:send_sms_message).
    
    **Required Parameters:**
    * `sms_user`: Your SMS_USER credential
    * `sms_key`: Your SMS_KEY credential
    * `template_id`: ID of your approved SMS template
    * `phone`: Recipient's phone number (with country code)
    * `template_vars`: Variables for template substitution (if applicable)
    
    **Example Request:**
    ```json
    {
      "sms_user": "your_sms_user",
      "sms_key": "your_sms_key", 
      "template_id": "template_123",
      "phone": "+1234567890",
      "template_vars": {
        "name": "John Doe",
        "code": "123456"
      }
    }
    ```
  </Tab>
  
  <Tab title="Dashboard Sending">
    ### Manual SMS Campaigns
    
    For one-time campaigns or testing purposes, you can send SMS messages directly through the Aurora SendCloud dashboard:
    
    1. **Navigate to SMS Campaigns**: Go to Content → SMS → Campaigns
    2. **Create New Campaign**: Click the "New Campaign" button
    3. **Select Template**: Choose an approved SMS template
    4. **Add Recipients**: Upload recipient list or add individual numbers
    5. **Schedule & Send**: Choose immediate sending or schedule for later
    
    <Callout icon="📋" theme="info">
      **Best Practices for SMS Campaigns:**
      - Always test with a small group first
      - Respect sending time zones and local regulations
      - Include clear opt-out instructions for marketing messages
      - Monitor delivery rates and adjust accordingly
    </Callout>
  </Tab>
</Tabs>

## SMS Message Status Tracking

Understanding message statuses helps you monitor delivery performance and troubleshoot issues effectively:

<Accordion title="Message Status Details" icon="chart-line">

### Status Types

<Cards columns="2">
  <Card title="Requested" icon="clock">
    **Initial Status**
    
    The sending request has been received by Aurora SendCloud and is queued for processing. The message is being prepared for delivery to the carrier network.
  </Card>
  
  <Card title="Delivered" icon="check-circle">
    **Successful Delivery**
    
    The message has been successfully sent and the carrier network has confirmed delivery to the recipient's device. This is the desired final status.
  </Card>
  
  <Card title="Waiting Result" icon="hourglass-half">
    **Pending Confirmation**
    
    The message has been sent to the carrier network, but we're still waiting for a delivery report. This is common and usually resolves within minutes.
  </Card>
  
  <Card title="Failed" icon="exclamation-triangle">
    **Delivery Failed**
    
    The carrier network reported that the message could not be delivered. See failure reasons below for troubleshooting.
  </Card>
  
  <Card title="Suppressed" icon="shield-alt">
    **System Blocked**
    
    Aurora SendCloud's system prevented the message from being sent due to compliance, filtering rules, or custom suppression settings.
  </Card>
</Cards>

### Common Failure Reasons

**Device-Related Issues:**
* Recipient's device is turned off or out of service
* Poor network coverage or signal issues
* Recipient's mailbox is full
* Invalid or disconnected phone number

**Content-Related Issues:**
* Message content violates carrier policies
* Suspicious links or prohibited content detected
* Message exceeds carrier-specific length limits

**Timing Issues:**
* Sending outside allowed hours for the destination country
* Carrier-imposed sending restrictions during high-traffic periods

**Account Issues:**
* Insufficient balance in S-Wallet
* Sender ID not approved for the destination country
* Template not approved or expired

</Accordion>

### Status Monitoring Tips

* **Real-time Tracking**: Use webhooks to receive instant status updates
* **Bulk Analysis**: Export delivery reports for campaign performance analysis  
* **Retry Logic**: Implement automatic retries for "Waiting Result" messages after reasonable delays
* **Alert Setup**: Configure notifications for high failure rates or suppressed messages

## SMS Sender ID Management

The Sender ID is the name or number that appears as the message sender. A custom Sender ID helps build brand recognition and trust with recipients.

### Sender ID Overview

<Callout icon="info-circle" theme="info">
**Default Behavior**: If you haven't registered a custom Sender ID, Aurora SendCloud automatically assigns a random numeric ID for your messages. You can send messages immediately without registration, but custom Sender IDs improve brand recognition.
</Callout>

**Benefits of Custom Sender ID:**
* **Brand Recognition**: Recipients see your company name instead of random numbers
* **Trust Building**: Familiar sender names increase message open rates
* **Professional Appearance**: Enhances your brand's credibility
* **Compliance**: Some regions require registered Sender IDs for commercial messages

### Registration Process

<Tabs>
  <Tab title="Registration Steps">
    #### Step 1: Access Sender ID Settings
    Navigate to **Integration → SMS → Sender ID** in your Aurora SendCloud dashboard.
    
    #### Step 2: Provide Registration Information
    Complete the registration form with:
    
    * **Sender ID**: Your desired brand name or identifier (alphanumeric, 3-11 characters)
    * **Applicant Country/Region**: Select target countries where you'll use this Sender ID
    * **Business Documentation**: Upload required business registration documents
    * **Use Case Description**: Explain how you'll use the Sender ID
    
    #### Step 3: Document Submission
    Our registration team will contact you with specific requirements, which may include:
    * Business registration certificates
    * Brand trademark documents  
    * Website verification
    * Sample message content
    * Compliance agreements
    
    #### Step 4: Review Process
    * **Processing Time**: Varies by country (typically 1-4 weeks)
    * **Carrier Approval**: Each carrier in target countries must approve your Sender ID
    * **Status Updates**: Receive notifications throughout the review process
  </Tab>
  
  <Tab title="Country Requirements">
    #### Regional Variations
    
    Sender ID registration rules vary significantly by country and carrier. Here are some key considerations:
    
    **Supported Countries:**
    * Some countries don't support custom Sender IDs
    * Others require specific documentation or impose restrictions
    * Fees may apply depending on local carrier policies
    
    **Common Requirements:**
    * **United States**: Primarily uses numeric sender IDs; limited alphanumeric support
    * **European Union**: Generally supports alphanumeric Sender IDs with business verification
    * **Asia-Pacific**: Mixed requirements; some countries require government approval
    * **Middle East & Africa**: Often require local business presence or sponsorship
    
    **Important Notes:**
    * Registration fees vary by country and are subject to local carrier pricing
    * Some countries require annual renewal of Sender ID registrations
    * Pre-registered Sender IDs may not work in all countries even after approval
    
    <Callout icon="warning" theme="warning">
      **Compliance Warning**: Using unregistered Sender IDs in countries that require registration may result in message blocking or account suspension. Always verify requirements before sending commercial messages.
    </Callout>
  </Tab>
</Tabs>

### Best Practices for Sender IDs

**Choosing Your Sender ID:**
* Keep it short (3-11 characters) and memorable
* Use your brand name or recognizable abbreviation
* Avoid special characters or numbers unless necessary
* Ensure it clearly identifies your organization

**Managing Multiple Sender IDs:**
* Register different IDs for different message types (alerts vs. marketing)
* Use country-specific Sender IDs when required
* Maintain consistent branding across all communications
* Test Sender ID display across different devices and carriers

**Monitoring and Maintenance:**
* Regularly check Sender ID approval status in different countries
* Renew registrations before expiration dates
* Monitor delivery rates for different Sender IDs
* Update documentation when business information changes