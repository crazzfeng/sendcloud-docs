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
  robots: index
---
# Aurora SendCloud Email Data

Get comprehensive insights into your email performance with Aurora SendCloud's detailed tracking and analytics system. Monitor every aspect of your email campaigns from send to delivery with real-time status updates and performance metrics. 

Our platform provides complete visibility into your email delivery lifecycle with full-link event tracking including: request, delivery, open, click, unsubscribe, invalid email, soft bounce, spam reports, and routing information.

<br />

## Email Status Categories

Track your email performance across four key status categories to understand your delivery success and identify areas for improvement:

<Cards columns={4}>
  <Card title="Delivered" icon="fa-check-circle">
    Email successfully delivered to the recipient's mailbox provider and accepted for final delivery. This indicates successful inbox placement.
  </Card>

  <Card title="Sending" icon="fa-paper-plane">
    Your email has been received by Aurora SendCloud and is either queued for delivery or currently being processed through our delivery infrastructure.
  </Card>

  <Card title="Soft Bounce" icon="fa-exclamation-triangle">
    Temporary delivery failure that may resolve automatically. Common causes include full mailboxes or temporary server issues.
  </Card>

  <Card title="Invalid Email" icon="fa-times-circle">
    Permanent delivery failure due to invalid email addresses, hard bounces, or suppression list matches.
  </Card>
</Cards>

## Invalid Email Categories

Understanding why emails fail helps you maintain a clean mailing list and improve deliverability:

<Cards columns={3}>
  <Card title="Hard Bounce" icon="fa-ban">
    Permanent delivery failures due to invalid email addresses, non-existent domains, or blocked recipients.
  </Card>

  <Card title="Suppression" icon="fa-user-slash">
    Emails blocked due to previous unsubscribes, spam complaints, or addresses on your suppression list.
  </Card>

  <Card title="Policy Rejection" icon="fa-shield-alt">
    Emails rejected by recipient servers due to content filtering, reputation issues, or security policies.
  </Card>
</Cards>

## Event Tracking

Monitor detailed engagement metrics and delivery events:

<Accordion title="Available Tracking Events" icon="fa-chart-line">

### Delivery Events
- **Request**: Email submission received by Aurora SendCloud
- **Delivery**: Successful delivery to recipient's mail server
- **Bounce**: Failed delivery with reason codes

### Engagement Events  
- **Open**: Email opened by recipient (pixel tracking)
- **Click**: Links clicked within the email content
- **Unsubscribe**: Recipient opted out via unsubscribe link

### Administrative Events
- **Route**: Delivery path and server routing information
- **Report**: Spam complaints or abuse reports received

</Accordion>

## Data Access and Reporting

Access your email data through multiple channels:

- **Real-time Dashboard**: Monitor campaign performance as it happens
- **API Integration**: Programmatic access to delivery and engagement data
- **Webhooks**: Receive instant notifications for email events
- **CSV Reports**: Download comprehensive data for analysis

<br />

---

*Need help setting up tracking or accessing your data? Contact our support team for assistance with implementation and troubleshooting.*