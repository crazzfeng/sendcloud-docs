---
title: Campaigns
deprecated: false
hidden: false
link:
  new_tab: false
metadata:
  robots: index
---
# Campaigns

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

### Step 1: Define Your Audience

**Determine recipients**: Choose who will receive your campaign:
- **All Contacts**: Send to your entire contact list
- **Tags**: Target contacts with specific tags (e.g., "VIP Customers", "Newsletter Subscribers")
- **Segments**: Use advanced filtering to target specific contact groups

💡 **Tip**: Using targeted segments typically results in higher engagement rates than sending to all contacts.

### Step 2: Configure Sender Information

**Choose the sender**: This appears as the "From" name in recipients' inboxes
- Use a recognizable name or brand
- Consistent sender names build trust and improve open rates

**Set reply email address**: Where replies will be sent
- Use a monitored email address
- Consider using a dedicated reply address for campaigns

### Step 3: Select Content

**Select email template**: Choose from your saved templates
- Ensure the template matches your campaign goals
- Preview the template on different devices before sending

### Step 4: Advanced Configuration (Optional)

**Configure advanced settings**: Access additional features like:
- Google Analytics tracking
- Warm-up sending for better deliverability

[Learn more about advanced settings](#advanced-campaign-settings)

### Step 5: Schedule & Send

**Set execution time**: Choose when to send your campaign
- **Send now**: Immediate delivery
- **Schedule**: Set a specific date and time
- **Time zone**: Ensure you select the correct time zone for your audience

⚠️ **Important**: Double-check your time zone selection to avoid sending at unintended times.

## Create an A/B Test Email Campaign

A/B testing helps you optimize campaigns by comparing different variations. Here's how to set up effective tests:

### Step 1: Design Your Test

#### Choose Test Element

**Select what to test** (choose one):

| Test Type | What It Measures | Best For |
|-----------|------------------|----------|
| **Subject Line** | Open rates | First impressions, curiosity |
| **Email Content** | Click rates, engagement | Message effectiveness |
| **Sender Name** | Open rates, trust | Brand recognition |
| **Send Time** | Open rates, engagement | Audience behavior |

💡 **Note**: Each test supports up to 3 variations (A, B, C).

#### Set Success Metrics

**Choose winning criteria**:

- **Open Rate**: Best for subject line and sender name tests
- **Unique Open Rate**: Focuses on individual engagement
- **Click Rate**: Best for content and call-to-action tests  
- **Unique Click Rate**: Measures individual click behavior
- **Delivery Rate**: For deliverability optimization

**Evaluation time**: Set how long to run the test (recommended: 2-24 hours)

#### Configure Test Size

**Set test percentage**: What portion of your audience participates in the test

- **20% test**: 20% split between variations, 80% get the winner
- **50% test**: 50% split between variations, 50% get the winner
- **Custom**: Set your preferred split

🎯 **Recommendation**: Use 20-30% for tests to maximize the impact of the winning variation.

### Step 2: Complete Campaign Setup

Follow the same configuration steps as regular campaigns:
1. Select recipients (All Contacts, Tags, or Segments)
2. Configure sender information
3. Set reply email address  
4. Choose email template
5. Schedule execution time

## Advanced Campaign Settings

### Google Analytics Tracking

Track campaign performance in Google Analytics by automatically adding UTM parameters to your email links.

**Available Parameters:**
- **Campaign Name** (`utm_campaign`): Identify the specific campaign
- **Campaign Source** (`utm_source`): Automatically set to "SendCloud"  
- **Campaign Medium** (`utm_medium`): Automatically set to "email"
- **Campaign Term** (`utm_term`): Optional keyword tracking
- **Campaign Content** (`utm_content`): Distinguish between different links

**Example Transformation:**
```
Original: https://www.aurorasendcloud.com
Enhanced: https://www.aurorasendcloud.com?utm_campaign=newsletter&utm_source=SendCloud&utm_medium=email
```

### Warm-Up Sending

Improve deliverability by gradually increasing sending volume, especially important for new domains or high-volume campaigns.

**How It Works:**
- Starts with conservative sending rates
- Monitors delivery performance automatically
- **Increases rate** when delivery exceeds threshold
- **Decreases rate** when delivery drops below threshold

**Rate Progression:**
Starting at 100 emails/hour, the system can scale up to 25,000 emails/hour over 15 steps based on performance.

| Timeframe | Conservative | Moderate | Aggressive |
|-----------|-------------|----------|------------|
| First Hour | 100 emails | 100 emails | 100 emails |
| First Day | 1,000 emails | 1,000 emails | 1,000 emails |
| Week 2+ | Up to 25k/hour | Up to 25k/hour | Up to 25k/hour |

## Campaign Status & Management

Understanding campaign states helps you manage your email marketing effectively:

| Status | Description | Available Actions |
|--------|-------------|-------------------|
| **Waiting** | Scheduled but not yet sent | ✅ Edit, Delete, Reschedule |
| **Sending** | Currently being delivered | 📊 View Reports, Monitor Progress |
| **Completed** | Successfully sent | 📊 View Reports, Clone Campaign |
| **Failed** | Encountered errors | 🔍 Review Error Details, Retry |

### Troubleshooting Failed Campaigns

**Most Common Issues:**
1. **Insufficient Email Credits**: Check your account balance
2. **Daily Quota Exceeded**: Wait for quota reset or upgrade plan  
3. **Authentication Failure**: Verify API keys haven't changed
4. **Invalid Recipients**: Check contact list quality
5. **Template Issues**: Ensure template is properly formatted

**Quick Fixes:**
- Verify account credits and quotas
- Check template preview before sending
- Validate recipient lists for format errors
- Ensure API credentials are current

## Campaign Analytics & Reports

### Overview Dashboard
Get a high-level view of campaign performance:
- **Sending Progress**: Real-time delivery status
- **Top Domains**: Performance breakdown by recipient email provider
- **Key Metrics**: Open rates, click rates, bounces at a glance

### Detailed Tracking
Deep dive into engagement data:
- **Opens & Clicks**: Detailed interaction tracking
- **Unsubscribes**: Monitor list health
- **Complaints**: Identify content issues
- **Geographic Data**: See where your audience engages

### Advanced Analytics

#### Geographic Insights

**Location Data:**
- Country and region breakdown
- Time zone engagement patterns
- Regional performance ranking

**Use Cases:**
- Optimize send times by location
- Create region-specific campaigns
- Understand global audience distribution

#### Link Performance

**Click Analysis:**
- Individual link click rates
- Heat mapping of email interactions
- Conversion tracking from email to action

**Optimization Tips:**
- A/B test different call-to-action buttons
- Analyze which content drives clicks
- Optimize link placement and frequency

#### Device & Technology

**Technical Insights:**
- Mobile vs desktop open rates
- Email client preferences
- Browser and OS breakdown
- Mobile carrier data

**Applications:**
- Optimize templates for popular devices
- Test compatibility across email clients
- Tailor content for mobile-first audiences

### Export Options

From any campaign report, export detailed data:
- **Domain Statistics**: Performance by email provider
- **Individual Tracking**: Per-recipient engagement data  
- **Failure Analysis**: Detailed bounce and error information

---

## Quick Reference

<Cards columns={3}>
  <Card title="Best Practices" icon="lightbulb">
    - Test subject lines with A/B campaigns
    - Use consistent sender names
    - Segment your audience for relevance
    - Monitor deliverability with warm-up sending
  </Card>
  
  <Card title="Troubleshooting" icon="wrench">
    - Check account credits before large sends
    - Verify time zones for scheduled campaigns
    - Review template compatibility across devices
    - Monitor bounce rates and list health
  </Card>
  
  <Card title="Optimization" icon="chart-arrow-up">
    - Use Google Analytics tracking
    - Export data for deeper analysis  
    - A/B test different elements regularly
    - Review geographic and device insights
  </Card>
</Cards>

Need help getting started? Check out our [Email Templates Guide] or contact support for personalized assistance.