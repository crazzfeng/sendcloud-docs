---
title: Send Calendar Email
excerpt: >-
  Send calendar invitations containing meeting information, supporting
  cancellation/updates of calendars.
api:
  file: sendEmail.yaml
  operationId: send-calendar
hidden: false
---
Tips:

1. Assuming that “from” is `IFAXIN support<support@ifaxin.com>`. If “fromName” is empty, “IFAXIN support” will be set as “fromName”; if not, no processing is needed.
2. When sending emails with address lists, specify lists with parameter “to”. Each address in the email will be sent individually. Address list cannot be more than 5. cc, bcc and xsmtpapi turn to invalid now.
3. When sending emails without address list, specify recipients with xsmtpapi. Multiple recipients are sent individually. Parameters “to”, “cc” and “bcc” turn to invalid now.
4. Recipients of “to”, “cc” and “bcc” cannot be more than 100; recipients of “to” in xsmtpapi cannot be more than 100.
5. “html” and “plain” cannot be both empty . If both “html” and “plain” are not empty, “html” is in priority.
6. Variable is allowed in subject, html and plain. As special character, “%” needs to be processed in HTTP request.
7. If a Key in the parameter headers starts with "SC-Custom-", this Key:Value will be returned to the user through WebHook. Key:Value must be a string, and Value must not contain special characters '.'. When a Key is passed in, the corresponding Value cannot be empty, otherwise an error 40902 "Unknown exception occurred in mail processing" will be returned.
8. “participatorNames”, “participatorEmails” represent all participants. Generally, recipients need to be include.
9. Please contact customer service for relevant permission before using the interface.
