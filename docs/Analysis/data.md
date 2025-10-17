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
   At the beginning, the mailbox provider received the email, but can't deliver the email into the recipient's inbox, then returns the email. Common causes include full mailboxes or temporary server issues.
  </Card>

  <Card title="Invalid Email" icon="fa-times-circle">
    Delivery failure due to invalid email addresses, hard bounces, or suppression list matches.
  </Card>
</Cards>

## Invalid Email Categories

Understanding why emails fail helps you maintain a clean mailing list and improve deliverability:

* **Blacklist** : the email address is in the Aurora SendCloud blacklist and will not be sent.
* **Unsubscribe** : once a user clicks the unsubscribe link, he will enter the unsubscribe list, and sendcloud will not deliver such e-mail addresses
* **Server Error** : temporary or permanent connection of sendcloud sending pool cannot access MX service of receiving domain
* **Format Error** : Aurora SendCloud or MP determines that the email address format is illegal
* **Not Exist** : MP returns to inform this email address does not exist
* **Junk Mail** : MP returns to inform that the sending behavior or content of this email is determined as spam
* **Rejected** : MP returns to inform the sender that the email was rejected abnormally or because of recipient settings
* **Others** : other reasons. You can see the detail log by clicking the record.

### What is Aurora SendCloud blacklist

If the type of invalid mail is "in the blacklist", it is because the address is in "Complaint List", "Block List" or "Bounce List". If you insist on sending a letter to an address, you can delete the address in the corresponding "Complaint" / "Block" / "Bounce" or set no interception.

## Soft Bounce Categories

Understanding why emails fail helps you maintain a clean mailing list and improve deliverability:

* Sever Error : MP internal service cannot be delivered
* IP rejection : MP returns to inform that the email sending is rejected due to IP or domain name related reasons
* Not Exist : MP returns to inform this email address does not exist
* Spam Rejected : MP returns to inform that the sending behavior or content of this email is determined as spam
* Rejected : MP returns to inform the sender that the email was rejected abnormally or because of recipient settings
* Others : other reasons

<br />

## Event Tracking Records

Support full-link events with device information

<Accordion title="Available Tracking Events" icon="fa-chart-line">
  ### Delivery Events

  * **Request**: Email submission received by Aurora SendCloud
  * **Delivery**: Successful delivery to recipient's mail server
  * **Bounce**: Failed delivery with reason codes

  ### Engagement Events

  * **Open**: Email opened by recipient (pixel tracking)
  * **Click**: Links clicked within the email content
  * **Unsubscribe**: Recipient opted out via unsubscribe link

  ### Administrative Events

  * **Route**: Delivery path and server routing information
  * **Report**: Spam complaints or abuse reports received
</Accordion>

## Data Access and Reporting

Access your email data through multiple channels:

* **Real-time Dashboard**: Monitor campaign performance as it happens
* **API Integration**: Programmatic access to delivery and engagement data
* **Webhooks**: Receive instant notifications for email events
* **CSV Reports**: Download comprehensive data for analysis

<br />

***

_Need help setting up tracking or accessing your data? Contact our support team for assistance with implementation and troubleshooting._
