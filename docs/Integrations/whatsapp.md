---
title: 'WhatsApp '
excerpt: >-
  Step-by-step tutorial for integrating WhatsApp Business with Aurora SendCloud,
  including account setup, template creation, testing, and campaign management
  with all original screenshots preserved.
deprecated: false
hidden: false
link:
  new_tab: false
metadata:
  robots: index
---
## WhatsApp Business Integration Overview

Transform your marketing strategy with Aurora SendCloud's powerful WhatsApp Business integration. This comprehensive guide walks you through every step from account setup to launching successful campaigns.

<Cards columns={2}>
  <Card title="Quick Integration" icon="rocket">
    Connect your WhatsApp Business Account in minutes with our streamlined process
  </Card>

  <Card title="Template Creation" icon="file-alt">
    Design and submit message templates for Meta approval with built-in editor
  </Card>

  <Card title="Campaign Management" icon="bullhorn">
    Launch targeted marketing campaigns to segmented contact lists
  </Card>

  <Card title="Performance Tracking" icon="chart-line">
    Monitor delivery rates, engagement metrics, and campaign ROI
  </Card>
</Cards>

## Prerequisites Checklist

Before starting your integration, ensure you have:

* ✅ **Facebook Account** with admin access to Meta Business Manager
* ✅ **Dedicated Phone Number** (never used with any WhatsApp service)
* ✅ **Aurora SendCloud Access** with active platform account
* ✅ **Business Documentation** including website and contact information
* ✅ **Verification Capability** for SMS or voice calls on your phone number

> **⚠️ Critical**: Your phone number must be completely new and never registered with personal or business WhatsApp accounts.

***

## Part 1: Integration & Account Binding

<Accordion title="Step 1: Navigate to Integration Module" icon="plug">
  **Access the Integration Hub:**

  Log into your Aurora SendCloud platform dashboard, locate the left-side navigation menu on the Overview page, and click on the fourth icon labeled **\[Integration]**.

  ![Aurora SendCloud Integration Module](https://files.readme.io/d331f19ddcb726dc4ed0fec27c33bcfb28af87e3cf01c67ed6c4563aa2327080-image.png)
</Accordion>

<Accordion title="Step 2: Begin WhatsApp Connection" icon="link">
  **Initiate WhatsApp Setup:**

  On the Integration page, locate the WhatsApp service option and click the blue **\[Connect]** button next to WhatsApp. The system will prepare the integration workflow.

  ![WhatsApp Connection Interface](https://files.readme.io/2f94ea6e445d2079d793dc4b99ed76a289a83a8a8528d936d3d2e06429d55e3c-image.png)
</Accordion>

<Accordion title="Step 3: Facebook Authorization Process" icon="facebook">
  **Complete Facebook Login:**

  After clicking "Connect," you'll be redirected to the WhatsApp Business Account registration guide provided by EngageLab.

  Click the **\[Login with Facebook]** button on the setup page:

  ![Facebook Login Interface](https://files.readme.io/fc0f37173d11d4a781ce4791cb6d0b48b82642d56ca487b0e763811e2329698b-image.png)

  A Facebook login window will appear for authentication:

  ![Facebook Authentication Window](https://files.readme.io/f3a99ebe6e929d8c2901da5d3916254082da8dd64df3aba8a08cbc77397081ec-image.png)

  > **🔑 Important**: Use the Facebook account that manages your Meta Business Manager. Your WhatsApp Business assets must be linked to this account.
</Accordion>

<Accordion title="Step 4: Authorization & Permissions" icon="shield-alt">
  **Grant Required Permissions:**

  After successful Facebook login, an authorization prompt will appear. Click **\[Get Started]** in the bottom-right corner to begin setup:

  ![Authorization Prompt](https://files.readme.io/054254492697583ac9c7d5dbc90a4bfaf77a77f56614001f34bbcf4624f9bd19-image.png)

  Review the permissions list that will be granted to EngageLab, then click **\[Continue]** to complete authorization (required step):

  ![Permission Authorization](https://files.readme.io/7ab3d3e38fa93a9958fadd41af6ae4d9c232b77319bf2251d6f20d6ab6e3fd57-image.png)

  These permissions enable WhatsApp Business API functionality and campaign management.
</Accordion>

<Accordion title="Step 5: Meta Business Account Setup" icon="building">
  **Create or Select Business Account:**

  Choose to either select an existing Meta Business Account or create a new one.

  ![Meta Business Account Setup](https://files.readme.io/17137ad02598c0415c506b478d4337034b27b39179d9fcb8e9c315863603d819-image.png)

  **For New Account Creation, provide:**

  **Company Name**: Your official registered business name\
  **Company Email**: Corporate email address (avoid personal domains like Gmail, QQ, 163)\
  **Company Website**: Official business website accessible internationally\
  **Country/Region**: Your primary business location

  > **💡 Pro Tip**: Use corporate email addresses to improve approval rates. Ensure your website is accessible to international visitors as Meta's review system will verify your business legitimacy.
</Accordion>

<Accordion title="Step 6: WhatsApp Business Account (WABA) Configuration" icon="whatsapp">
  **Setup Your WABA:**

  Similar to the previous step, you can select an existing WABA or create a new one.

  ![WABA Selection Interface](https://files.readme.io/6a7528085dd786df99a09499b122c7fb32588fa4e0a836d606fc2b44e26a181b-image.png)

  Complete the following information:

  ![WABA Configuration Form](https://files.readme.io/58cf438c876157b3d6b91a6d34426b823aca2bddc3ad2b444e1da8d61a22c48e-image.png)

  **WhatsApp Business Account Name**: Internal management identifier\
  **WhatsApp Business Profile Display Name**: Customer-facing business name (visible to recipients)\
  **Time Zone**: Your business operation timezone (⚠️ cannot be changed later)\
  **Category**: Select your business industry classification\
  **Business Description**: Brief overview of your company and services
</Accordion>

<Accordion title="Step 7: Phone Number Verification (Critical Step)" icon="phone">
  **Add and Verify Your Business Number:**

  This is the most critical step requiring careful execution.

  **Phone Number Requirements:**

  * ✅ Must be a brand new number
  * ✅ Never registered with any WhatsApp service (personal or business)
  * ✅ Capable of receiving SMS or voice calls
  * ✅ Will become your permanent WhatsApp Business number

  **Verification Process:**

  ![Phone Number Verification](https://files.readme.io/3ef0f0e7a2e2f738c50483e1cb1a19e4242ea665ce297172758c768b9667046b-image.png)

  Select your country/region code (e.g., US +1), enter your dedicated phone number, choose verification method: **Voice Call** (recommended) or **Text Message**, then receive and enter the 6-digit verification code:

  ![Verification Code Entry](https://files.readme.io/7e3d9c06d9532249907b9576c711582109f4b5e16ae604c8bfe3db81b70d1b28-image.png)

  **🚨 Troubleshooting for +86 (China) Numbers:**
  If you experience issues receiving verification codes, check your phone's call blocking settings or contact your carrier to enable international communications. Consider using numbers from other regions if problems persist.
</Accordion>

<Accordion title="Step 8: Integration Completion" icon="check-circle">
  **Verify Successful Connection:**

  Once verification succeeds, the system automatically completes all configurations and redirects you back to the Aurora SendCloud Integration page.

  ![Successful Integration Status](https://files.readme.io/ed5e8cc97ed6fc12dd6b2c12808d61dc1d29dee46580e72d9ae620b7313ff550-image.png)

  **Success Indicators:**

  * WhatsApp status displays as green **\[Connected]**
  * Integration is now active and ready for template creation
  * Your phone number is verified and operational
</Accordion>

***

## Part 2: WhatsApp Message Template Creation

All promotional WhatsApp messages sent via API must use pre-approved templates. Here's your complete template creation workflow:

### Template Management Workflow

<Tabs>
  <Tab title="Template Creation">
    Navigate to **Content** → **WhatsApp** in the left-side navigation bar, then click **+ New Template** button in the upper-left corner.

    ![New Template Creation](https://files.readme.io/4d4552f4b7a8bb3091e2a113388fb9c96ae9150333ed1fe942eda380dbc335d0-image.png)
  </Tab>

  <Tab title="Basic Information">
    Complete your template configuration with these required fields:

    ![Template Basic Information](https://files.readme.io/a1c5a9472471748c135b1d57aefeb35ef5480c7d9b5728ec338d3137b1617a84-image.png)

    **Template Category**: Defaults to Marketing\
    **Template Name**: Use only numbers, lowercase letters, and underscores\
    **Language**: Select primary language (click "Add more languages" for multilingual templates)
  </Tab>

  <Tab title="Content Design">
    Design your message components using the template editor:

    ![Template Content Editor](https://files.readme.io/4a7e8c821c9943ff69d625155593835b6332d47ec16729867c66d78a22c9d8a4-image.png)

    **Header** (Optional): Eye-catching opening element\
    **Body** (Required): Core message content with personalization variables\
    **Footer** (Optional): Signature or disclaimer text\
    **Buttons** (Recommended): Interactive elements including Quick Reply responses and Call to Action options
  </Tab>

  <Tab title="Submission & Approval">
    Submit your template for Meta review by clicking the **Create** button in the top-right corner. Your template will be submitted to Meta for official review.

    ![Template Approval Status](https://files.readme.io/423237f7100b949951dcdbfc6d9d1bde86171b8d5035eb160d00050a7a23dc1e-image.png)

    **Review Timeline**: Meta approval typically takes several hours to multiple business days. Only templates with **APPROVED** status can be used for campaigns.
  </Tab>
</Tabs>

***

## Part 3: Testing & Validation

### Send Test Messages

**Verify Template Functionality:**

Locate an approved template in your template list and click **[Test]** in the actions column:

<Image alt="Template Testing Interface" border={false} src="https://files.readme.io/0c17dc2d8810e5cb30c67489e0ce64cc8ef5d8a5facfd7e5759220de0d6c1e6b-image.png" />

Enter recipient's mobile number in the test popup:

<Image alt="Test Message Setup" border={false} src="https://files.readme.io/e163b794bcbbe005b616a73442548ab1792b3fa3dbb0f434779b26a10865733c-image.png" />

**Number Format Requirements:**
Use complete international format: `+[Country Code][Mobile Number]` (Example: `+852xxxxxxxx`). Avoid formats starting with "00" or missing country codes.

Click **[Send]** to deliver test message:

<Image alt="Test Message Delivered" border={false} src="https://files.readme.io/4cfb86e3440df2357722a5599e1b1cd55d7df17c784a8e296cbb369daaecdd3a-image.png" />

**✅ Success Validation**: Recipient should receive the formatted message in WhatsApp with all interactive elements functioning properly.

***

## Part 4: Marketing Campaign Creation & Execution

### Campaign Setup Workflow

<Accordion title="Create New Marketing Campaign" icon="bullhorn">
  **Initialize Campaign:**

  Navigate to **\[Marketing]** in the left sidebar to access the Campaigns page, then click the **\[Create]** button to start a new campaign:

  ![Create Campaign Interface](https://files.readme.io/630be8945a6ff6c0cda1691b60ad34180e377f1ba1ebca6b9478d17835755866-image.png)
</Accordion>

<Accordion title="Configure Campaign Type" icon="cog">
  **Set Campaign Parameters:**

  ![Campaign Configuration](https://files.readme.io/de16a67cf00cb6c283fe1c503516922a1f26147e82e827e05d5e98bae53a185d-image.png)

  Enter a descriptive **Task Name** for internal identification, select **WhatsApp Task** as your Task Type, then click **\[Save]** to proceed to detailed configuration.
</Accordion>

<Accordion title="Campaign Execution Settings" icon="settings">
  **Configure Campaign Details:**

  ![Campaign Execution Settings](https://files.readme.io/d7a7da2916edc1a2536055a68ccdc5a4142f12aa634fbcbb217de6b0a77bcc06-image.png)

  **Essential Configuration:**

  **Recipients Management**: Click "Add Recipients" button, select target contact groups or tags, and verify contact data includes properly formatted mobile numbers.

  **Sender Selection**: System automatically selects your connected WhatsApp number. Verify correct business number is displayed.

  **Template Selection**: Click "Select Template", choose an **\[APPROVED]** template from the list, and select appropriate language version.

  **Execution Timing**: Choose **Send Immediately** to launch campaign right away, or **Scheduled Send** to set future date and time for delivery. Consider recipient time zones for optimal engagement.

  **Final Steps**: Click **\[Save]** at the bottom to complete campaign creation and prepare for launch.
</Accordion>

***

## Compliance & Best Practices

<Cards columns={1}>
  <Card title="⚠️ Critical Compliance Warning" icon="exclamation-triangle">
    **Opt-in Requirement**: WhatsApp has strict permission-based marketing requirements. Only message contacts who have explicitly consented to receive your communications. Violating this policy may result in permanent account suspension.
  </Card>
</Cards>

### Success Guidelines & Best Practices

**Permission Management:**

* ✅ Maintain detailed opt-in consent records
* ✅ Provide easy opt-out mechanisms
* ✅ Honor unsubscribe requests immediately
* ✅ Document consent collection methods

**Content Strategy:**

* 🎯 **Relevant Messaging**: Send valuable, targeted content
* ⏰ **Optimal Timing**: Respect local time zones and business hours
* 📊 **Frequency Control**: Avoid overwhelming contacts
* 💬 **Response Management**: Monitor and respond to replies promptly

**Performance Optimization:**

* 📈 **A/B Testing**: Test different templates and timing
* 🎯 **Segmentation**: Target specific audience groups
* 📊 **Analytics**: Track delivery rates and engagement metrics
* 🔄 **Iteration**: Continuously improve based on performance data

### Troubleshooting Common Issues

| Issue                     | Cause                                                | Solution                                                      |
| ------------------------- | ---------------------------------------------------- | ------------------------------------------------------------- |
| **Verification Failures** | Carrier restrictions on international communications | Enable international calls/SMS or use different region number |
| **Template Rejections**   | Content violates Meta policies                       | Review guidelines, avoid promotional language, focus on value |
| **Low Delivery Rates**    | Invalid phone number formats or inactive numbers     | Audit contact data quality, verify number formats             |
| **Account Restrictions**  | Policy violations or suspicious activity             | Ensure compliance, review sending patterns, contact support   |

***

## Support & Next Steps

### Getting Help

If you encounter issues during setup or need assistance with WhatsApp marketing strategy, our support team is ready to help with:

* ✅ **Technical Integration Support**
* ✅ **Template Design Consultation**
* ✅ **Campaign Strategy Guidance**
* ✅ **Performance Optimization**

### Advanced Features

Once your basic integration is complete, explore these advanced capabilities:

* 🤖 **Automated Workflows**: Set up trigger-based messaging
* 🎯 **Advanced Segmentation**: Create detailed audience profiles
* 📊 **Analytics Dashboard**: Deep-dive performance reporting
* 🔄 **API Integration**: Custom integration options

**Ready to scale?** Your WhatsApp Business integration opens up powerful marketing opportunities. Start with compliant, value-driven campaigns and gradually expand your reach while maintaining high engagement rates.

***

> **Success Tip**: Begin with small, targeted campaigns to established contacts, monitor engagement carefully, and scale based on performance data and compliance requirements.