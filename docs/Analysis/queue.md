---
title: Queue
excerpt: >-
  Monitor and analyze the email sending rate and trends of the recipient domains
  to promptly identify and email deliver issues.
deprecated: false
hidden: false
metadata:
  robots: index
---
# Aurora SendCloud Email Sending Queue

Aurora SendCloud can master the mainstream MP (Mailbox Provider) receiving strategy and adopt an adaptive sending queue. Scalable infrastructure adapts to your business growth, with intelligent queuing systems and real-time optimization algorithms to ensure rapid and stable email delivery. 24-hour monitoring, intelligent analysis of sending status, and continuous optimization of sending scheduling mechanism.

<Image align="center" alt="Email Sending Queue" border={false} caption="Email Sending Queue" src="https://files.readme.io/49ff5fe507e784ffb56d4eb91f52dd8843939080bb43e45ea7ff1a5c9efaef67-analytics_data.556bbc59.png" />

## Understand Sending Queue

On the queue page,you can see specific queue data includes status, API_ USER,receiving domain,total of emails to be sent,rate (In,Try out,Out).

You can change the rate and view the average rate every 5s, 15s, and 30s ,and the change trend can be viewed through the chart (refresh the data every 5s).

When the queue is paused, the reason caused the pause and the next sending time will be shown. Click the Recover to trigger the sending immediately.

The pause of queue indicates that the mail delivery is blocked. The reason is related to the receiving mechanism of MP. Common reasons for suspension include :

* The limitations caused by the domain
* The limitations caused by IP reputation
* Frequency of IP connection


If the duration of pause is unreasonable long(2-3 days), please contact us for assistance.
