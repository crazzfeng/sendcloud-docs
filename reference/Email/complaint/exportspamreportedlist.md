---
title: Export Spam Reported List
excerpt: >-
  Export spam-reported email data within a specified time range to a CSV file.
  The maximum export time range is 30 days, and the generated CSV file is valid
  for 24 hours (after which the download URL expires). The CSV includes fields:
  emailId, email, from, subject, sendTime, reportTime, mailServer, domain,
  labelName.
api:
  file: complaint.yaml
  operationId: exportSpamReportedList
hidden: false
---