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

Aurora SendCloud masters mainstream MP (Mailbox Provider) receiving strategies and adopts an adaptive sending queue. Our scalable infrastructure adapts to your business growth, featuring intelligent queuing systems and real-time optimization algorithms that ensure rapid and stable email delivery. We provide 24-hour monitoring with intelligent analysis of sending status and continuous optimization of the sending scheduling mechanism.

<Image align="center" alt="Email Sending Queue" border={false} caption="Email Sending Queue" src="https://files.readme.io/49ff5fe507e784ffb56d4eb91f52dd8843939080bb43e45ea7ff1a5c9efaef67-analytics_data.556bbc59.png" />

## Understanding the Sending Queue

On the queue page, you can view specific queue data including status, API_USER, receiving domain, total number of emails to be sent, and rate (In, Try out, Out).

You can change the rate and view the average rate every 5s, 15s, and 30s. The change trend can be viewed through the chart, which refreshes data every 5 seconds.

When the queue is paused, the reason that caused the pause and the next sending time will be displayed. Click the "Recover" button to trigger sending immediately.

A paused queue indicates that mail delivery is blocked. The reason is related to the receiving mechanism of the MP (Mailbox Provider). Common reasons for suspension include:

* Limitations caused by the domain
* Limitations caused by IP reputation
* Frequency of IP connections

If the pause duration is unreasonably long (2-3 days), please contact us for assistance.

## Manage the Queue

<br />
