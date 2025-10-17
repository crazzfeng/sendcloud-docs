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
# Aurora SendCloud Email Sending Queue

Aurora SendCloud masters mainstream mailbox provider (MP) receiving strategies and employs an adaptive sending queue. Our scalable infrastructure adapts to your business growth, featuring intelligent queuing systems and real-time optimization algorithms that ensure fast and stable email delivery. We provide 24-hour monitoring with intelligent analysis of sending status and continuous optimization of the sending scheduling mechanism.

<Image align="center" alt="Email Sending Queue" border={false} caption="Email Sending Queue" src="https://files.readme.io/49ff5fe507e784ffb56d4eb91f52dd8843939080bb43e45ea7ff1a5c9efaef67-analytics_data.556bbc59.png" />

## Understanding the Sending Queue

On the queue page, you can view specific queue data including status, API_USER, receiving domain, total number of emails to be sent, and rate (In, Try out, Out).

You can change the rate and view the average rate every 5s, 15s, and 30s. The change trend can be viewed through the chart, which refreshes data every 5 seconds.

When the queue is paused, the reason that caused the pause and the next sending time will be displayed. Click the "Recover" button to trigger sending immediately.

A paused queue indicates that email delivery is blocked. The reason is related to the receiving mechanism of the mailbox provider (MP). Common reasons for suspension include:

* You manually paused the queue
* Limitations caused by the domain
* Limitations caused by IP reputation  
* Frequency of IP connections

If the pause duration is unreasonably long (2-3 days), please contact us for assistance.

## Manage the Queue

We know humans make mistakes. In some cases, you may send the wrong content or send to wrong recipients. Don't worry, Aurora SendCloud has solutions. **You can pause or delete the sending queue**.

### Pause the Queue

<Image align="center" alt="Pause the email sending queue" border={false} caption="Pause the email sending queue" src="https://files.readme.io/caca3b5b91f6a7c46a62034db643287d9b928769379854357622e53f59c2a055-image.png" />

You can pause the email sending queue by specifying:

* **API_USER**: Mandatory. The API_USER that you used to send emails.
* **Receiving Domain**: Optional. The recipient email providers' domains, like gmail.com. If left empty, it means you want to pause the sending queue for the API_USER with all receiving domains.

**Recovery Time** is the time you want to resume the paused queue.

1. The recovery time should not be more than 15 days.
2. If the recovery time is not set and delivery is not resumed after 15 days, the suspended emails will be deleted automatically.

### Delete the Queue

<Callout icon="❗️">
  Deletion is not recoverable. Please be cautious.
</Callout>

<Image align="center" alt="Delete the email sending queue" border={false} caption="Delete the email sending queue" src="https://files.readme.io/bf70de4aab56ad6b5a17e58a00ddd763f8126d29f6dd201f791159f4fe1df9c1-image.png" />

You can delete the email sending queue by specifying:

* **API_USER**: Mandatory. The API_USER that you used to send emails.
* **Receiving Domain**: Optional. The recipient email providers' domains, like gmail.com. If left empty, it means you want to delete the sending queue for the API_USER with all receiving domains.
* **Request Time**: The time period of emails that you want to delete.