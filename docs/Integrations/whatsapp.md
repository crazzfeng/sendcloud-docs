---
title: WhatsApp Business Integration Guide
excerpt: >-
  Complete step-by-step guide to integrate WhatsApp Business with Aurora
  SendCloud, create message templates, and launch successful marketing
  campaigns.
deprecated: false
hidden: true
link:
  new_tab: false
metadata:
  robots: index
---
# WhatsApp Business Integration Guide

Welcome to Aurora SendCloud's comprehensive WhatsApp Business integration guide. This tutorial will help you connect your WhatsApp Business Account, create approved message templates, and launch effective marketing campaigns.

<Cards columns={2}>
  <Card title="Quick Setup" icon="rocket">
    Get started in minutes with our streamlined integration process
  </Card>
  <Card title="Template Management" icon="file-alt">
    Create and manage WhatsApp message templates with approval workflow
  </Card>
  <Card title="Campaign Tools" icon="bullhorn">
    Launch targeted marketing campaigns to your contact lists
  </Card>
  <Card title="Analytics" icon="chart-bar">
    Track performance and optimize your WhatsApp marketing efforts
  </Card>
</Cards>

## Prerequisites

Before you begin, ensure you have:

- ✅ A Facebook account with admin access to Meta Business Manager
- ✅ A dedicated phone number (never used with WhatsApp before)
- ✅ Aurora SendCloud platform access
- ✅ Valid business website and contact information

> **Important**: The phone number must be completely new and able to receive SMS or voice calls for verification.

---

## Part 1: Integration & Account Setup

<Accordion title="Step 1: Access Integration Module" icon="plug">

1. Log into your Aurora SendCloud platform
2. Navigate to the left sidebar and click the **Integration** module (4th icon)
3. Locate the WhatsApp option and click the blue **Connect** button

![Integration Module](https://files.readme.io/d331f19ddcb726dc4ed0fec27c33bcfb28af87e3cf01c67ed6c4563aa2327080-image.png)

</Accordion>

<Accordion title="Step 2: Facebook Authorization" icon="facebook">

1. Click **Login with Facebook** when redirected to the EngageLab setup page
2. Use the Facebook account that manages your Meta Business Manager
3. Complete the Facebook login process

> **Critical**: Use the same Facebook account that has access to your business assets and Meta Business Manager.

</Accordion>

<Accordion title="Step 3: Grant Permissions" icon="shield-alt">

1. Click **Get Started** in the authorization prompt
2. Review the permission list that will be granted to EngageLab
3. Click **Continue** to complete authorization

These permissions are required for proper WhatsApp Business API functionality.

</Accordion>

<Accordion title="Step 4: Business Account Setup" icon="building">

Choose to either **select existing** or **create new** Meta Business Account.

**For new accounts, provide:**
- **Company Name**: Your official business name
- **Company Email**: Use corporate email (avoid personal domains like Gmail/Yahoo)
- **Company Website**: Accessible business website with international access
- **Country/Region**: Your business location

> **Pro Tip**: Ensure your website is accessible from international IPs, as Meta's review bots need to verify your business.

</Accordion>

<Accordion title="Step 5: WhatsApp Business Account (WABA)" icon="whatsapp">

Create or select your WhatsApp Business Account with these details:

**Required Information:**
- **Account Name**: Internal management name
- **Display Name**: Customer-facing business name (important!)
- **Time Zone**: Cannot be changed later - choose carefully
- **Category**: Your business industry
- **Description**: Brief business overview

</Accordion>

<Accordion title="Step 6: Phone Number Verification" icon="phone">

This is the most critical step requiring careful attention.

**Number Requirements:**
- ✅ Brand new number (never registered with any WhatsApp)
- ✅ Can receive SMS or voice calls
- ✅ Will become your official business WhatsApp number

**Verification Process:**
1. Select country code (e.g., +1 for US)
2. Enter phone number
3. Choose verification method: **Voice Call** (recommended) or SMS
4. Enter the 6-digit verification code

> **Troubleshooting**: If using a +86 (China) number, enable international calls/SMS with your carrier or consider using a number from another region.

</Accordion>

## Part 2: Message Template Creation

All WhatsApp marketing messages must use pre-approved templates. Here's how to create them:

### Template Management

<Tabs>
  <Tab title="Create Template">
**Navigation Steps:**

Navigate to **Content** → **WhatsApp** in the left sidebar, then click **+ New Template**.

**Template Configuration:**

Set the **Category** to Marketing (default), create a **Name** using only numbers, lowercase letters, and underscores, and select your primary **Language** (you can add more later).
  </Tab>
  <Tab title="Content Design">
**Template Components:**

**Header (Optional):** Eye-catching opening element

**Body (Required):** Core message content that can include personalization variables

**Footer (Optional):** Short signature or disclaimer

**Buttons (Recommended):** Choose between **Quick Reply** for preset response options or **Call to Action** for phone call or website visit buttons
  </Tab>
  <Tab title="Approval Process">
**Review & Approval:**

Click **Create** to submit your template. Meta will review it within hours to several business days. The status changes to **APPROVED** when ready, and only approved templates can be used for campaigns.

**Best Practices:** Follow Meta's content policies, avoid spam-like language, include clear value proposition, and test with different audiences.
  </Tab>
</Tabs>

---

## Part 3: Testing & Validation

### Send Test Messages

<Columns layout="auto">
  <Column>
**Test Process:**

Find your approved template in the list, click **Test** in the actions column, enter the recipient's phone number in international format, then click **Send** to deliver the test message.
  </Column>
  <Column>
**Format Requirements:**

Use complete international format like `+852xxxxxxxx`. Do not use "00" prefix or missing country codes. The recipient must have WhatsApp installed.
  </Column>
</Columns>

> **Success Indicator**: Test recipient receives message in WhatsApp with proper formatting and functionality.

---

## Part 4: Marketing Campaigns

### Campaign Creation Workflow

<Accordion title="Campaign Setup" icon="bullhorn">

**Create New Campaign:**

Navigate to **Marketing** → **Campaigns**, click the **Create** button, enter a descriptive **Task Name**, select **WhatsApp Task** as the task type, then click **Save**.

</Accordion>

<Accordion title="Campaign Configuration" icon="cogs">

**Essential Settings:**

**Recipients:** Click "Add Recipients" and select contact groups or tags. Ensure contacts have valid phone numbers.

**Sender:** The system will auto-select your connected WhatsApp number.

**Template:** Choose your approved template and select the language version.

**Timing:** Send immediately or schedule for later, considering recipient time zones.

</Accordion>

<Accordion title="Launch & Monitor" icon="rocket">

**Final Steps:**

Review all settings carefully, click **Save** to create the campaign, monitor delivery status and responses, then track engagement metrics.

</Accordion>

---

## Compliance & Best Practices

<Cards columns={1}>
  <Card title="Permission-Based Marketing" icon="exclamation-triangle">
    **Critical Requirement**: Only message contacts who have explicitly opted in to receive your communications. Sending unsolicited messages can result in account suspension.
  </Card>
</Cards>

### Success Guidelines

- **Opt-in Consent**: Maintain clear records of user consent
- **Relevant Content**: Send valuable, targeted messages
- **Timing**: Respect local time zones and business hours
- **Frequency**: Avoid overwhelming contacts with too many messages
- **Response Handling**: Monitor and respond to customer replies promptly

### Troubleshooting Common Issues

- **Verification Failures**: Check phone carrier settings for international calls/SMS
- **Template Rejections**: Review Meta's content policies and avoid promotional language
- **Low Delivery Rates**: Verify contact data quality and phone number formats
- **Account Restrictions**: Ensure compliance with WhatsApp Business policies

---

## Need Help?

If you encounter any issues during setup or have questions about WhatsApp marketing best practices, contact our support team for assistance.

**Next Steps**: Once your integration is complete, explore advanced features like automated workflows, customer segmentation, and analytics reporting to maximize your WhatsApp marketing ROI.