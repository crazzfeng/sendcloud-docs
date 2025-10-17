---
title: MP Monitor
excerpt: >-
  MP monitor is a professional monitoring function designed for feedback data
  from Mailbox Providers.
deprecated: false
hidden: false
link:
  new_tab: false
metadata:
  robots: index
---
# MP Monitor: Professional Email Performance Monitoring

<Image align="center" alt="MP Monitor" border={false} caption="MP Monitor Dashboard" src="https://files.readme.io/948724cd1ce55938b3c30b5a32b4c7bed148989df824373dd8209ad2db3f6bae-image.png" />

MP Monitor (Mailbox Provider Monitor) is Aurora SendCloud's professional monitoring solution designed to track and analyze feedback data from major mailbox providers. This comprehensive tool enables you to maintain optimal email deliverability by monitoring reputation scores, spam complaints, and delivery performance metrics directly from mailbox providers.

## Why Use MP Monitor?

<Cards columns={2}>
  <Card title="Delivery Optimization" icon="rocket">
    Get direct insights from mailbox providers to optimize your email delivery performance and reduce bounce rates.
  </Card>
  <Card title="Reputation Protection" icon="shield-alt">
    Monitor your domain and IP reputation scores to prevent blacklisting and maintain sender credibility.
  </Card>
  <Card title="Performance Analytics" icon="chart-line">
    Access detailed analytics on delivery rates, inbox placement, and spam complaints to improve campaign effectiveness.
  </Card>
  <Card title="Proactive Monitoring" icon="eye">
    Receive real-time feedback to identify and resolve deliverability issues before they impact your campaigns.
  </Card>
</Cards>

## Key Features & Benefits

<Accordion title="Comprehensive Monitoring" icon="monitor">
  Track essential metrics including:
  - **Spam Rate**: Monitor the percentage of your emails marked as spam
  - **IP & Domain Reputation**: View reputation scores from major providers
  - **Delivery Errors**: Identify and resolve delivery issues quickly
  - **Authentication Status**: Ensure proper SPF, DKIM, and DMARC configuration
</Accordion>

<Accordion title="Data-Driven Insights" icon="analytics">
  - Analyze delivery and inbox placement rates across different providers
  - Identify trends and patterns in email performance
  - Generate actionable recommendations for campaign optimization
  - Compare performance across different domains and IPs
</Accordion>

<Accordion title="Reputation Management" icon="star">
  - Prevent emails from being marked as spam or blocked
  - Maintain high deliverability rates through continuous monitoring
  - Receive alerts when reputation scores drop below acceptable thresholds
  - Track improvement over time with historical data
</Accordion>

## Supported Providers

<Tabs>
  <Tab title="Google Postmaster">
    Google Postmaster Tools provides comprehensive analytics for Gmail delivery, offering insights into spam rates, reputation scores, authentication status, and delivery errors.
  </Tab>
  <Tab title="Yahoo CFL">
    Yahoo Complaint Feedback Loop helps monitor spam complaints and protect your sender reputation specifically for Yahoo Mail recipients.
  </Tab>
</Tabs>

## Setup Instructions

### Google Postmaster Configuration

Google Postmaster provides valuable analytics insights that can optimize your email performance and improve deliverability to Gmail users.

<Callout theme="info">
  **Setup Time**: Configuration takes 5-10 minutes, with data collection beginning within a few hours.
</Callout>

**Step 1: Access Google Postmaster Tools**
1. Navigate to the <Anchor label="Google Postmaster Tool" target="_blank" href="https://postmaster.google.com/">Google Postmaster Tool</Anchor>
2. Sign in with your Google account or create a new one if needed

**Step 2: Add and Verify Your Domain**
1. Click the "**+**" button in the bottom right corner of the homepage
2. Enter your sending domain name and click "**Next**"
3. Copy the generated TXT record value
4. Add this TXT record to your domain's DNS configuration
5. Return to Google Postmaster and click "**Verify**"

<Callout theme="warning">
  **DNS Propagation**: It may take up to 24 hours for DNS changes to propagate. You can check propagation status using online DNS checker tools.
</Callout>

**Step 3: Grant Access to SendCloud**
1. After domain verification, hover over your domain on the homepage
2. Click the "**More ⋮**" button on the right side
3. Select "**Manage Users**" from the dropdown menu
4. Click the "**+**" button in the bottom right corner
5. Add the Aurora SendCloud monitoring email: **sendcloudfbl@gmail.com**
6. Set permissions to "**Read Only**"

<Callout theme="success">
  Aurora SendCloud only requires read-only access and will not modify any settings or affect your business operations.
</Callout>

### Yahoo CFL Configuration

Yahoo Complaint Feedback Loop monitors spam complaints from Yahoo Mail users, helping you maintain a positive sender reputation.

<Callout theme="info">
  **Requirements**: You must have an active sending domain configured in Aurora SendCloud before setting up Yahoo CFL.
</Callout>

**Step 1: Domain Selection**
1. In your Aurora SendCloud dashboard, navigate to MP Monitor
2. Select Yahoo CFL configuration
3. Choose one of your existing verified sending domains from the dropdown

**Step 2: DNS Configuration**
1. Copy the generated TXT record value provided by the system
2. Access your domain's DNS management panel
3. Create a new TXT record with the provided value
4. Save the DNS changes

**Step 3: Verification**
1. Return to the Aurora SendCloud MP Monitor interface
2. Click the "**Verify**" button
3. The system will check for the TXT record and confirm setup

<Callout theme="warning">
  **Verification Timing**: DNS changes may take 5-15 minutes to be recognized by Yahoo's systems. If verification fails, wait a few minutes and try again.
</Callout>

## Monitoring and Analytics

Once configured, MP Monitor will begin collecting data from your connected mailbox providers. You can access:

- **Real-time dashboards** showing current reputation scores
- **Historical trends** to track performance over time  
- **Alert notifications** for reputation or delivery issues
- **Detailed reports** for campaign optimization insights

<Callout theme="success">
  **Pro Tip**: Regular monitoring of MP Monitor data can help you maintain deliverability rates above 95% and keep your sender reputation in good standing.
</Callout>

## Troubleshooting

<Accordion title="Google Postmaster Issues" icon="question-circle">
  **Common Issues:**
  - **Domain not verifying**: Ensure the TXT record is added correctly and DNS has propagated
  - **No data appearing**: Data collection can take 24-48 hours to begin, especially for new domains
  - **Access denied**: Verify that sendcloudfbl@gmail.com was added with proper permissions
  
  **Solutions:**
  - Check DNS records using online DNS lookup tools
  - Wait 24-48 hours for initial data collection
  - Re-verify domain ownership if issues persist
</Accordion>

<Accordion title="Yahoo CFL Issues" icon="exclamation-triangle">
  **Common Issues:**
  - **TXT record not found**: DNS propagation may still be in progress
  - **Domain not eligible**: Only verified sending domains can be configured
  - **Verification timeout**: Multiple verification attempts may be needed
  
  **Solutions:**
  - Wait 15-30 minutes between verification attempts
  - Double-check TXT record formatting and placement
  - Contact support if issues persist beyond 24 hours
</Accordion>

Need additional help? Contact our support team for personalized assistance with MP Monitor configuration.