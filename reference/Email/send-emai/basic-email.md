---
title: Basic Send
excerpt: >-
  Send regular emails with custom content (supports attachments, CC/BCC, address
  lists, etc.)
api:
  file: sendEmail.yaml
  operationId: basic-email
hidden: false
---
<br />

Tips:

1. Assuming that “from” is `IFAXIN support<support@ifaxin.com>`.If “fromName” is empty, “IFAXIN support” will be set as “fromName”; if not, no processing is needed.
2. When sending emails with address lists, specify lists with parameter “to”. Each address included in the email will be sent individually. Address lists cannot be more than 5. cc, bcc and xsmtpapi turn to invalid now.
3. When sending emails without address list, designate recipients with “to”. Multiple recipients are sent through multi-transmission (all recipients will be displayed). Designate cc recipients with parameter “cc”, and bcc recipients with “bcc”.
4. When sending emails without address list, specify recipients with xsmtpapi. Multiple recipients are sent individually. Parameters “to”, “cc” and “bcc” turn to invalid now.
5. Recipients of “to”, “cc” and “bcc” cannot be more than 100; recipients of “to” in xsmtpapi cannot be more than 100.
6. “html” and “plain” cannot be both empty. If both “html” and “plain” are not empty, “html” is in priority. If html and plain need to coexist, contact customer service to open.
7. [Variable](/QuickStart/Interpretation/#Variable) is allowed in subject, html and plains. As special character, “%” needs to be processed in HTTP request.
8. When using return receipt, recipients can choose whether to send reading receipt to “from” after receiving emails.
9. If a Key in the parameter headers starts with "SC-Custom-", this Key:Value will be returned to the user through WebHook. Key:Value must be a string, and Value must not contain special characters '.'. When a Key is passed in, the corresponding Value cannot be empty, otherwise an error 40902, "Unknown exception occurred in mail processing" will be returned.
10. When using an address list (useAddressList = true), headers do not exceed 1024 bytes.
11. “contentSummary” can only be used with “html”; value of “contentSummary” will be invalid without the value of “html”.](../guide/rule.md#x-smtpapi)
12. The size of attachments is 10m by default. Contact customer service for special needs.
