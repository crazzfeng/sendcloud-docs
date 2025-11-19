---
title: Query Spam Reported List (POST)
excerpt: >-
  Query spam-reported email list within a specified time range using POST
  method. The maximum query time range is 90 days. Supports filtering by
  recipient email, sending domain, email label, and mail server. Returns
  paginated results with detailed spam report information including email ID,
  recipient, sender, subject, send time, report time, mail server, domain, and
  label.
api:
  file: complaint.yaml
  operationId: getSpamReportedListPost
hidden: false
---