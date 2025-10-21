---
title: Queue
excerpt: >-
  Monitor and analyze the email sending rate and trends of the recipient domains
  to promptly identify and email deliver issues.
deprecated: false
hidden: false
link:
  new_tab: false
metadata:
  robots: index
---
## Email Sending Queue

Aurora SendCloud uses intelligent queue management to optimize email delivery across all major mailbox providers. Our adaptive sending system automatically adjusts to recipient domain requirements, ensuring fast and reliable email delivery with 24/7 monitoring and real-time optimization.

<Image align="center" alt="Email Sending Queue" border={false} caption="Email Sending Queue" src="https://files.readme.io/49ff5fe507e784ffb56d4eb91f52dd8843939080bb43e45ea7ff1a5c9efaef67-analytics_data.556bbc59.png" />

## Monitor Your Queue

The queue dashboard provides real-time insights into your email delivery:

* **Queue Status**: Current state of your email queue
* **API_USER**: The API_USER associated with the queue
* **Receiving Domain**: Destination email provider (e.g., gmail.com, outlook.com)
* **Email Count**: Total emails pending delivery
* **Sending Rate**: Current throughput (In, Try out, Out)

### Real-Time Analytics

View sending rates with customizable intervals (5s, 15s, 30s) and track trends through live charts that update every 5 seconds.

### Queue Pauses

When a queue pauses, you'll see:

* **Pause Reason**: Why delivery was suspended
* **Next Send Time**: When delivery will resume
* **Recovery Button**: Manual option to resume immediately

**Common pause reasons:**

* Manual pause by user
* Domain-specific limitations
* IP reputation restrictions
* Connection frequency limits

> **Need Help?** If your queue is paused for more than 2-3 days, contact our support team for assistance.

## Queue Management

Made a mistake? No problem. You can pause or delete queues to prevent unwanted deliveries.

### Pause a Queue

<Image align="center" alt="Pause the email sending queue" border={false} caption="Pause the email sending queue" src="https://files.readme.io/caca3b5b91f6a7c46a62034db643287d9b928769379854357622e53f59c2a055-image.png" />

**Required:**

* **API_USER**: Select the API_USER that sent the emails

**Optional:**

* **Receiving Domain**: Target specific email providers (leave empty to pause all domains)
* **Recovery Time**: When to automatically resume (maximum 15 days)

> **Important:** Emails suspended for more than 15 days without a recovery time will be automatically deleted.

### Delete a Queue

<Callout icon="❗️" theme="error">
  **Warning:** Queue deletion is permanent and cannot be undone. Proceed with caution.
</Callout>

<Image align="center" alt="Delete the email sending queue" border={false} caption="Delete the email sending queue" src="https://files.readme.io/bf70de4aab56ad6b5a17e58a00ddd763f8126d29f6dd201f791159f4fe1df9c1-image.png" />

**Required:**

* **API_USER**: Select the API_USER that sent the emails

**Optional:**

* **Receiving Domain**: Target specific email providers (leave empty to delete all domains)
* **Request Time**: Specify the time range of emails to delete

> **Best Practice:** Use pause instead of delete when possible to avoid permanent data loss.
