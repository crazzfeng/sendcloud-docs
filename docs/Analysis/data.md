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

Our platform provides complete visibility into your email delivery lifecycle with full-link event tracking including: requests, delivery, opens, clicks, unsubscribes, invalid emails, soft bounces, spam reports, and routing information.

<Callout icon="📘">
  Email status and event data in Aurora SendCloud is stored by default for 6 months.
</Callout>

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
    The mailbox provider initially received the email but could not deliver it to the recipient's inbox and returned it. Common causes include full mailboxes or temporary server issues.
  </Card>

  <Card title="Invalid Email" icon="fa-times-circle">
    Delivery failure due to invalid email addresses, hard bounces, or suppression list matches.
  </Card>
</Cards>

<br />

### Invalid Email Categories

Understanding why emails fail helps you maintain a clean mailing list and improve deliverability:

* **Blacklist**: The email address is in the Aurora SendCloud blacklist and will not be sent.
* **Unsubscribe**: Once a user clicks the unsubscribe link, they will enter the unsubscribe list, and SendCloud will not deliver emails to such addresses.
* **Server Error**: Temporary or permanent connection issues prevent SendCloud's sending pool from accessing the MX service of the receiving domain.
* **Format Error**: Aurora SendCloud or the Mail Provider (MP) determines that the email address format is invalid.
* **Not Exist**: The MP returns notification that this email address does not exist.
* **Junk Mail**: The MP returns notification that the sending behavior or content of this email is determined to be spam.
* **Rejected**: The MP returns notification that the email was rejected abnormally or due to recipient settings.
* **Others**: Other reasons. You can see detailed logs by clicking the record.

<br />

#### What is the Aurora SendCloud Blacklist?

If an invalid email type shows "in the blacklist," it means the address is in the "Complaint List," "Block List," or "Bounce List." If you need to send an email to such an address, you can delete the address from the corresponding "Complaint," "Block," or "Bounce" list, or configure it to bypass interception.

### Soft Bounce Categories

Understanding soft bounces helps you maintain email deliverability and troubleshoot temporary issues:

* **Server Error**: MP internal service cannot complete delivery.
* **IP Rejection**: MP returns notification that email sending is rejected due to IP or domain-related reasons.
* **Not Exist**: MP returns notification that this email address does not exist.
* **Spam Rejected**: MP returns notification that the sending behavior or content of this email is determined to be spam.
* **Rejected**: MP returns notification that the email was rejected abnormally or due to recipient settings.
* **Others**: Other reasons.

<br />

## Open and Click Records

Complete records with all the information you need.

<Callout icon="📘" theme="info">
  Open or Click events can only be recorded after you have enabled the tracking switch.
</Callout>

* **Event**: Open or Click
* **API_USER**: The API_USER that you used to send the email
* **Recipient**: The address to which you sent your email
* **Request Time**: The time you successfully requested Aurora SendCloud to send the email
* **Trigger Time**: The time the recipient opened the email or clicked a link in the email
* **IP**: The IP address from which the recipient opened or clicked the email
* **Device**: When the email was opened or clicked, we recorded the system, brand, and browser of the device
* **Link**: Only click events include link information

<br />

## Data Access and Reporting

Access your email data through multiple channels:

* **Real-time Records**: View data as it happens
* **API Integration**: Programmatic access to delivery and engagement data
* **Webhooks**: Receive instant notifications for email events
* **CSV Reports**: Download comprehensive data for analysis

<br />

***

_Need help setting up tracking or accessing your data? Contact our support team for assistance with implementation and troubleshooting._