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

Get comprehensive insights into your email performance with Aurora SendCloud's detailed tracking and analytics system. Monitor every aspect of your email campaigns from send to delivery with real-time status updates and performance metrics.Support full-link events: request, delivery, open, click, unsubscribe, invalid email, soft bounce, report, route.

<br />

## Email Status Categories

Track your email performance across four key status categories:

<Cards columns={4}>
	<Card title="Delivered" icon="fa-check-circle">
    Email successfully delivered to the recipient's mailbox provider and accepted for final delivery.
  </Card>
  <Card title="Sending" icon="fa-paper-plane">
    Your email has been received by SendCloud and is either queued for delivery or currently being processed through our retry system.
  </Card>
  <Card title="Soft Bounce" icon="fa-exclamation-triangle">
    Temporary delivery issue occurred after initial acceptance. SendCloud categorizes soft bounces into six detailed subcategories based on bounce notification analysis.
  </Card>
  <Card title="Invalid Email" icon="fa-times-circle">
    Permanent delivery failure detected. Our system analyzes mailbox provider feedback to classify failures into eight specific subcategories for better troubleshooting.
  </Card>
</Cards>

### Invalid Email Categories
