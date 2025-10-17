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

Aurora SendCloud provides detailed status data for the entire lifecycle of each email, including email status, recipient information, sending domain, API_USER, request time, sending time, request IP, delivery IP, sending content, and sending logs. We automatically analyze delivery logs, categorize failures, and optimize performance.

## Understand Your Email Status

The current status of emails can be divided into four categories: sending, delivered, soft bounce, and invalid email.

<Cards columns={4}>
  <Card title="Sending" icon="fa-home" target="_blank">
    The email requested by the customer has been successfully received by SendCloud and is queued for sending or currently being retried.
  </Card>

  <Card title="Delivered" icon="fa-user">
    Successfully delivered to the mailbox provider (MP).
  </Card>

  <Card title="Soft Bounce" icon="fa-star">
    After the email is delivered, it experiences a soft bounce. SendCloud divides soft bounce reasons into six subcategories by analyzing the content of the bounce notification.
  </Card>

  <Card title="Invalid Email" icon="fa-question">
    Email delivery failed. SendCloud divides failure reasons into eight subcategories by analyzing the mailbox provider feedback and delivery information.
  </Card>
</Cards>