---
title: Data
excerpt: >-
  Aurora SendCloud's Data provide detailed status data of the entire lifecycle
  of each email
deprecated: false
hidden: false
link:
  new_tab: false
metadata:
  title: Email Delivery Analytics & Data Tracking - Aurora SendCloud
  description: >-
    Monitor email delivery performance with Aurora SendCloud's comprehensive
    data analytics. Track delivery status, bounces, opens, clicks, and
    engagement metrics with real-time insights and 6-month data retention.
  keywords:
    - email delivery analytics
  robots: index
---
## Email Data & Analytics

Gain complete visibility into your email performance with Aurora SendCloud's comprehensive tracking and analytics platform. Monitor every stage of your email campaigns—from initial send through final delivery—with real-time status updates and detailed performance metrics.

Our advanced tracking system captures the complete email delivery lifecycle, providing full-link event monitoring for requests, deliveries, opens, clicks, unsubscribes, bounces, spam reports, and routing data.

<Callout icon="📘" theme="info">
  All email status and event data in Aurora SendCloud is retained for 6 months by default, giving you extensive historical insights.
</Callout>

Monitor your email performance across four essential status categories to optimize delivery success and identify improvement opportunities:

<Cards columns={4}>
  <Card title="Delivered" icon="fa-check-circle">
    Successfully delivered to the recipient's inbox. The email reached its final destination and was accepted by the mailbox provider.
  </Card>

  <Card title="Sending" icon="fa-paper-plane">
    Currently in progress. Your email is queued or being processed through our delivery infrastructure.
  </Card>

  <Card title="Soft Bounce" icon="fa-exclamation-triangle">
    Temporarily failed delivery. The receiving server accepted but couldn't deliver the email, often due to full mailboxes or server issues.
  </Card>

  <Card title="Invalid Email" icon="fa-times-circle">
    Permanent delivery failure. Issues include invalid addresses, hard bounces, or suppression list blocks.
  </Card>
</Cards>

<br />

## Understanding Email Failures

### Invalid Email Classifications

When emails fail to deliver, understanding the specific reason helps you maintain list hygiene and improve deliverability:

* **Blacklist**: Address exists on Aurora SendCloud's suppression lists and will be automatically blocked
* **Unsubscribe**: Recipient has opted out; SendCloud will not deliver future emails to this address
* **Server Error**: Connection issues prevent our servers from reaching the recipient's mail provider
* **Format Error**: Email address format is invalid according to Aurora SendCloud or the receiving mail provider
* **Non-existent**: The receiving mail provider confirmed this email address doesn't exist
* **Spam Filter**: Content or sending behavior flagged as spam by the receiving mail provider
* **Recipient Rejection**: Email rejected due to recipient-specific settings or provider policies
* **Other Issues**: Additional failure reasons—view detailed logs by clicking individual records

<br />

#### Managing the Aurora SendCloud Blacklist

When an email shows as "blacklisted," the address appears on one of our suppression lists: Complaint List, Block List, or Bounce List. To resume sending to these addresses:

1. Remove the address from the relevant suppression list
2. Configure bypass rules for specific scenarios
3. Contact support for assistance with list management

### Soft Bounce Classifications

Soft bounces indicate temporary delivery issues that may resolve on subsequent attempts:

* **Server Error**: Recipient's mail provider experienced internal service disruptions
* **IP/Domain Rejection**: Your sending IP or domain is temporarily blocked by the recipient's provider
* **Address Verification**: Recipient's mail provider couldn't verify the email address exists
* **Spam Filtering**: Email content or sending patterns triggered spam filters
* **Policy Rejection**: Email rejected due to recipient settings or provider policies
* **Miscellaneous**: Other temporary issues preventing delivery

<br />

## Email Engagement Tracking

Access comprehensive engagement data to understand how recipients interact with your emails.

<Callout icon="📘" theme="info">
  Open and click tracking must be enabled in your account settings to record engagement events.
</Callout>

### Engagement Data Points

* **Event Type**: Whether the recipient opened the email or clicked a link
* **API User**: The sending account used for the email
* **Recipient**: Target email address
* **Send Time**: When Aurora SendCloud successfully processed your send request
* **Engagement Time**: Exact timestamp when the recipient opened or clicked
* **IP Address**: Location data from the recipient's engagement
* **Device Information**: Detailed system, browser, and device data captured during engagement
* **Link Details**: For click events, specific URL information is recorded

<br />

## Accessing Your Data

Choose from multiple methods to access and analyze your email performance data:

### Real-Time Monitoring

* **Live Dashboard**: Monitor email performance as events occur
* **Instant Alerts**: Get immediate notifications for critical delivery issues

### Integration Options

* **REST API**: Programmatically access delivery and engagement data
* **Webhooks**: Receive real-time event notifications directly to your systems
* **CSV Exports**: Download comprehensive datasets for offline analysis

<br />

<br />

***

_Ready to optimize your email performance? Contact our support team for assistance with tracking setup, data analysis, and deliverability improvements._