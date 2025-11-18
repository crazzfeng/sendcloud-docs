---
title: Block Spam-Reported Address
excerpt: >-
  Add one or more spam-reported email addresses to the system's blocklist. After
  blocking, the system will permanently reject all future email sends to these
  addresses to protect sending reputation and comply with anti-spam regulations.
  Supports batch blocking (up to 100 addresses per request, separated by
  semicolons). Addresses already in the blocklist will be ignored.
api:
  file: complaint.yaml
  operationId: blockSpamReportedAddress
hidden: false
---