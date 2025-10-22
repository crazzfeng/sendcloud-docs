---
title: Campaigns
excerpt: >-
  Email campaigns are your primary tool for reaching contacts with targeted
  messaging. Whether you're sending newsletters, promotions, or announcements,
  this guide covers everything you need to create, optimize, and track
  successful campaigns.
deprecated: false
hidden: false
link:
  new_tab: false
metadata:
  robots: index
---
## Types of Email Campaigns

Email campaigns are your primary tool for reaching contacts with targeted messaging. Whether you're sending newsletters, promotions, or announcements, this guide covers everything you need to create, optimize, and track successful campaigns.

<Cards columns={2}>
  <Card title="Regular Campaigns" href="#create-a-regular-email-campaign" icon="envelope">
    Create standard email campaigns for newsletters, announcements, and marketing messages.
  </Card>

  <Card title="A/B Testing" href="#create-an-ab-test-email-campaign" icon="flask">
    Test different variations to optimize open rates, clicks, and engagement.
  </Card>
</Cards>

## Create a Regular Email Campaign

Follow these steps to create and send a standard email campaign:

<Accordion title="Step 1: Define Your Audience" icon="users">
  **Determine recipients**: Choose who will receive your campaign:

  * **All Contacts**: Send to your entire contact list
  * **Tags**: Target contacts with specific tags (e.g., "VIP Customers", "Newsletter Subscribers")
  * **Segments**: Use advanced filtering to target specific contact groups

  💡 **Tip**: Using targeted segments typically results in higher engagement rates than sending to all contacts.
</Accordion>

<Accordion title="Step 2: Configure Sender Information" icon="user-circle">
  **Choose the sender**: This appears as the "From" name in recipients' inboxes

  * Use a recognizable name or brand
  * Consistent sender names build trust and improve open rates

  **Set reply email address**: Where replies will be sent

  * Use a monitored email address
  * Consider using a dedicated reply address for campaigns
</Accordion>

<Accordion title="Step 3: Select Content" icon="file-text">
  **Select email template**: Choose from your saved templates

  * Ensure the template matches your campaign goals
  * Preview the template on different devices before sending
</Accordion>

<Accordion title="Step 4: Advanced Configuration (Optional)" icon="cog">
  **Configure advanced settings**: Access additional features such as:

  * Google Analytics tracking
  * Warm-up sending for better deliverability

  [Learn more about advanced settings](#advanced-campaign-settings)
</Accordion>

<Accordion title="Step 5: Schedule & Send" icon="clock">
  **Set execution time**: Choose when to send your campaign

  * **Send now**: Immediate delivery
  * **Schedule**: Set a specific date and time
  * **Time zone**: Ensure you select the correct time zone for your audience

  ⚠️ **Important**: Double-check your time zone selection to avoid sending at unintended times.
</Accordion>

## Create an A/B Test Email Campaign

A/B testing helps you optimize campaigns by comparing different variations. Here's how to set up effective tests:

### Step 1: Design Your Test

<Accordion title="Choose Test Element" icon="bullseye">
  **Select what to test** (choose one):

  | Test Type         | What It Measures        | Best For                     |
  | ----------------- | ----------------------- | ---------------------------- |
  | **Subject Line**  | Open rates              | First impressions, curiosity |
  | **Email Content** | Click rates, engagement | Message effectiveness        |
  | **Sender Name**   | Open rates, trust       | Brand recognition            |
  | **Send Time**     | Open rates, engagement  | Audience behavior            |

  💡 **Note**: Each test supports up to 3 variations (A, B, C).
</Accordion>

<Accordion title="Set Success Metrics" icon="target">
  **Choose winning criteria**:

  * **Open Rate**: Best for subject line and sender name tests
  * **Unique Open Rate**: Focuses on individual engagement
  * **Click Rate**: Best for content and call-to-action tests
  * **Unique Click Rate**: Measures individual click behavior
  * **Delivery Rate**: For deliverability optimization

  **Evaluation time**: Set how long to run the test (recommended: 2-24 hours)
</Accordion>

<Accordion title="Configure Test Size" icon="percentage">
  **Set test percentage**: What portion of your audience participates in the test

  * **20% test**: 20% split between variations, 80% receive the winner
  * **50% test**: 50% split between variations, 50% receive the winner
  * **Custom**: Set your preferred split

  🎯 **Recommendation**: Use 20-30% for tests to maximize the impact of the winning variation.
</Accordion>

### Step 2: Complete Campaign Setup

Follow the same configuration steps as regular campaigns:

1. Select recipients (All Contacts, Tags, or Segments)
2. Configure sender information
3. Set reply email address
4. Choose email template
5. Schedule execution time

---

<br />

## Advanced Campaign Settings

### Google Analytics Tracking

Track campaign performance in Google Analytics by automatically adding UTM parameters to your email links.

**Available Parameters:**

* **Campaign Name** (`utm_campaign`): Identify the specific campaign
* **Campaign Source** (`utm_source`): Automatically set to "SendCloud"
* **Campaign Medium** (`utm_medium`): Automatically set to "email"
* **Campaign Term** (`utm_term`): Optional keyword tracking
* **Campaign Content** (`utm_content`): Distinguish between different links

**Example Transformation:**

```
Original: https://www.aurorasendcloud.com
Enhanced: https://www.aurorasendcloud.com?utm_campaign=newsletter&utm_source=SendCloud&utm_medium=email
```

### Warm-Up Sending

Improve deliverability by gradually increasing sending volume, especially important for new domains or high-volume campaigns.

**How It Works:**

* Starts with conservative sending rates
* Monitors delivery performance automatically
* **Increases rate** when delivery exceeds threshold
* **Decreases rate** when delivery drops below threshold

**Rate Progression:**
Starting at 100 emails/hour, the system can scale up to 25,000 emails/hour over 15 steps based on performance.

| Timeframe  | Conservative   | Moderate       | Aggressive     |
| ---------- | -------------- | -------------- | -------------- |
| First Hour | 100 emails     | 100 emails     | 100 emails     |
| First Day  | 1,000 emails   | 1,000 emails   | 1,000 emails   |
| Week 2+    | Up to 25k/hour | Up to 25k/hour | Up to 25k/hour |

---

<br />

## Campaign Status & Management

Understanding campaign states helps you manage your email marketing effectively:

| Status        | Description                | Available Actions                 |
| ------------- | -------------------------- | --------------------------------- |
| **Waiting**   | Scheduled but not yet sent | ✅ Edit, Delete, Reschedule        |
| **Sending**   | Currently being delivered  | 📊 View Reports, Monitor Progress |
| **Completed** | Successfully sent          | 📊 View Reports, Clone Campaign   |
| **Failed**    | Encountered errors         | 🔍 Review Error Details, Retry    |

### Common Failure Causes

<Accordion title="Troubleshooting Failed Campaigns" icon="exclamation-triangle">
  **Most Common Issues:**

  1. **Insufficient Email Credits**: Check your account balance
  2. **Daily Quota Exceeded**: Wait for quota reset or upgrade plan
  3. **Invalid Recipients**: Check contact list quality
  4. **Template Issues**: Ensure template exists
</Accordion>

---

<br />

## Campaign Analytics & Reports

Understanding your campaign performance is crucial for improving your email marketing results. Aurora SendCloud provides comprehensive analytics to help you track delivery, engagement, and overall campaign success.

### Key Metrics Overview

<Table align={["left","left"]}>
  <thead>
    <tr>
      <th>
        Metric
      </th>

      <th>
        Description
      </th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td>
        <strong>Requested</strong>
      </td>

      <td>
        Total number of email send requests submitted to Aurora SendCloud
      </td>
    </tr>

    <tr>
      <td>
        <strong>Delivered</strong>
      </td>

      <td>
        Emails successfully delivered to recipient inboxes<br />
        <em>Rate = Delivered ÷ Requested</em>
      </td>
    </tr>

    <tr>
      <td>
        <strong>Invalid Email</strong>
      </td>

      <td>
        Emails rejected due to invalid or malformed email addresses<br />
        <em>Rate = Invalid Email ÷ Requested</em>
      </td>
    </tr>

    <tr>
      <td>
        <strong>Soft Bounce</strong>
      </td>

      <td>
        Emails temporarily rejected due to issues like full mailboxes or server problems<br />
        <em>Rate = Soft Bounce ÷ Requested</em>
      </td>
    </tr>

    <tr>
      <td>
        <strong>Billing Counts</strong>
      </td>

      <td>
        Number of emails that count toward your account usage and billing
      </td>
    </tr>

    <tr>
      <td>
        <strong>Opens</strong>
      </td>

      <td>
        Total email opens, including multiple opens by the same recipient<br />
        <em>Rate = Opens ÷ Delivered</em>
      </td>
    </tr>

    <tr>
      <td>
        <strong>Unique Opens</strong>
      </td>

      <td>
        Number of individual recipients who opened the email at least once<br />
        <em>Rate = Unique Opens ÷ Delivered</em>
      </td>
    </tr>

    <tr>
      <td>
        <strong>Clicks</strong>
      </td>

      <td>
        Total link clicks, including multiple clicks by the same recipient<br />
        <em>Rate = Clicks ÷ Delivered</em>
      </td>
    </tr>

    <tr>
      <td>
        <strong>Unique Clicks</strong>
      </td>

      <td>
        Number of individual recipients who clicked at least one link<br />
        <em>Rate = Unique Clicks ÷ Delivered</em>
      </td>
    </tr>

    <tr>
      <td>
        <strong>Spam Reports</strong>
      </td>

      <td>
        Emails marked as spam by recipients<br />
        <em>Rate = Spam Reports ÷ Delivered</em>
      </td>
    </tr>

    <tr>
      <td>
        <strong>Unsubscribes</strong>
      </td>

      <td>
        Recipients who clicked unsubscribe links<br />
        <em>Rate = Unsubscribes ÷ Delivered</em>
      </td>
    </tr>
  </tbody>
</Table>

### Delivery Performance Analysis

Monitor how well your emails are being delivered and identify potential issues:

* **Email status statistics**: Overview of successful deliveries, bounces, and failures
* **Daily send trends**: Track delivery patterns grouped by day to identify optimal sending times  
* **Domain-based performance**: Analyze how different email providers (Gmail, Outlook, etc.) handle your campaigns
* **Invalid email categorization**: Understand why emails failed validation and improve list quality
* **Bounce analysis**: Detailed breakdown of soft bounce reasons to improve deliverability

### Engagement Tracking Insights  

Understand how recipients interact with your campaigns:

* **Open and click trends**: Daily engagement patterns to optimize sending schedules
* **Domain-specific engagement**: How recipients from different email providers engage with your content
* **24-hour activity patterns**: Identify peak engagement hours for your audience
* **Geographic performance**: See where your most engaged subscribers are located
* **Device and platform insights**: Understand whether recipients engage more on mobile or desktop
* **Individual link performance**: Track which specific links generate the most clicks

### Detailed Campaign Data

Access granular information for deeper analysis:

The detailed data section provides comprehensive status information for every email sent in your campaign, allowing you to track the complete lifecycle from send request to final recipient action.

### Data Export Capabilities

Export your campaign data for advanced analysis and reporting:

* **Domain Statistics**: Download performance metrics broken down by email service providers
* **Individual Tracking Data**: Export per-recipient engagement information for customer segmentation  
* **Bounce and Failure Analysis**: Get detailed information about delivery failures for list cleaning

---

## Quick Reference

<Cards columns={3}>
  <Card title="Best Practices" icon="lightbulb">
    * Test subject lines with A/B campaigns
    * Use consistent sender names
    * Segment your audience for relevance
    * Monitor deliverability with warm-up sending
  </Card>

  <Card title="Troubleshooting" icon="wrench">
    * Check account credits before large sends
    * Verify time zones for scheduled campaigns
    * Review template compatibility across devices
    * Monitor bounce rates and list health
  </Card>

  <Card title="Optimization" icon="chart-arrow-up">
    * Use Google Analytics tracking
    * Export data for deeper analysis
    * A/B test different elements regularly
    * Review geographic and device insights
  </Card>
</Cards>

Need help getting started? Check out our [Email Templates Guide] or contact support for personalized assistance.