---
title: Data
excerpt: >-
  Aurora SendCloud's Data provide detailed status data of the entire lifecycle
  of each email
deprecated: false
hidden: false
metadata:
  robots: index
---
# Aurora SendCloud Email Data

Provide detailed status data of the entire lifecycle of each email, like email status, recipient, sending domain, API_USER, request time, sending time, request IP, delivery IP, sending content, sending logs.And we automatically analyze delivery logs, categorize failures, and optimize performance.

## Understand Your Email Status

The current status of email can be divided into four categories: sending , delivered, soft bounce, invalid email.

<Cards columns={4}>
  <Card title="Sending" icon="fa-home" target="_blank">
    the email requested by the customer has been successfully received by sendcloud, queued for sending or retrying sending 
  </Card>

  <Card title="Delivered" icon="fa-user">
    successfully delivered to MP (mailbox provider)
  </Card>

  <Card title="Soft Bounce" icon="fa-star">
    After the mail is delivered, it is soft returned. Sendcloud divides the soft return reasons into six sub categories by analyzing the content of the soft return email
  </Card>

  <Card title="Invalid email" icon="fa-question">
    Email delivery failed. Sendcloud divides the failure reasons into eight sub categories by analyzing the MP feedback delivery information
  </Card>
</Cards>
