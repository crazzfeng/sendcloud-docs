---
title: Deliverlies
---

# Deliverlies

## Regular delivery

**URL**

```  
https://api2.sendcloud.net/api/mail/send
```

**HTTP Request Method**

```bash
post
```

**Parameter Description**    

|**parameter**|**type**|**required or not**|**description**|
|:---|:---|:---|:---|
|apiUser|string|yes|API_USER|
|apiKey|string|yes|API_KEY|
|from|string|yes|sender email address, e.g.`support@ifaxin.com`, After you configure DMARC, SendCloud will take current domain as the suffix of “from”.|
|to|string|*|Recipient’s email addresses, separated by semicolons, e.g.`ben@ifaxin.com;joe@ifaxin.com`|
|subject|string|yes| subject, cannot be empty                                     |
|html|string|*|email content, formatted with `text/html`|
|contentSummary|string|*|content summary. When adding content summary,, if content summary already exists, the former one will be replaced by the most current summary;if not, the content summary will be added to the email.|
|fromName|string|no|sender name, shown as:`IFAXIN customer service<support@ifaxin.com>`|
|cc|string|no|cc addresses, separated by semicolons|
|bcc|string|no| bcc addresses, separated by semicolons                       |
|replyTo|string|no|default reply addresses, separated by semicolons, cannot be more than 3. If “reply To” does not exist or is null, reply address defaults to “from”|
|labelName|string|no|The label name used for this send. If this label name is not saved in the account, it will be created automatically.|
|headers|string|no|header of email, in JSON format, e.g.`{"header1": "value1", "header2": "value2"}`|
|attachments|file|no|email attachment; when sending attachment, it must be submitted with “multipart/form – data” in “post” (form submission)|
|xsmtpapi|string|no|SMTP extension, see [X-SMTPAPI](/SendCloudSMTP/X-SMTPAPI/) for more|
|plain|string|no|email content, formatted with `text/plain`|
|respEmailId|string (true, false)|no|default value: `true`. Whether returns to [emailId](/SendCloudSMTP/MessageId&EmailId/). With multiple recipients, return to the list of emailId|
|useNotification|string (true, false)|no|default value: false, whether notification is needed|
|useAddressList|string (true, false)|no|default value: false, whether to use address list. For example, `to=group1@maillist.sendcloud.org;group2@maillist.sendcloud.org`|

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

- - -

## Template delivery

**URL**

```  
https://api2.sendcloud.net/api/mail/sendtemplate
```

**HTTP Request Method** 

```bash
post
```

**Parameter Description**

|**parameter**| **type**             | required or not | **description**                                              |
|:---|:---|:---|:---|
|apiUser|string|yes|API_USER|
|apiKey|string|yes|API_KEY|
|from|string|yes|sender email address, e.g.`support@ifaxin.com`.After you configure DMARC, SendCloud will take current domain as the suffix of “from”.|
|to|string|*|address list, used when `useAddressList=true`|
|xsmtpapi|string|*|SMTP extension, see [X-SMTPAPI](/SendCloudSMTP/X-SMTPAPI/) for more|
|subject|string|*|subject|
|templateInvokeName|string|yes|calling name of email template|
|contentSummary|string|*|content summary. When adding content summary, if content summary already exists, the former one will be replaced by the most current content summary; if not, the content summary will be added to the email.|
|fromName|string|no|sender name, shown as: `IFAXIN customer service<support@ifaxin.com>`|
|cc|string|no|cc addresses, separated by semicolons|
|bcc|string|no|bcc addresses, separated by semicolons|
|replyTo|string|no|default reply addresses, separated by semicolons, cannot be more than 3. If “reply To” does not exist or is null, reply address defaults to “from”|
|labelName|string|no|The label name used for this send. If this label name is not saved in the account, it will be created automatically.|
|headers|string|no|header of email, in JSON format, e.g. `{"header1": "value1", "header2": "value2"}`|
|attachments|file|no|email attachment; when sending attachment, it must be submitted with “multipart/form – data” in “post” (form submission)|
|respEmailId|string (true, false)|no|default value: `true`. Whether return to [emailId](/SendCloudSMTP/MessageId&EmailId/). With multiple recipients, return to the list of emailId|
|useNotification|string (true, false)|no|default value:: `false`. whether notification is needed|
|useAddressList|string (true, false)|no|default value:: `false`. whether to use address list. For example, `to=group1@maillist.sendcloud.org;group2@maillist.sendcloud.org`|

Tips:

1. Assuming that “from” is `IFAXIN support<support@ifaxin.com>`.If “fromName” is empty, “IFAXIN support” will be set as “fromName”; if not, no processing is needed.

2. When sending emails with address lists, specify lists with parameter “to”. Each address included in the email will be sent individually. Address lists cannot be more than 5. cc, bcc and xsmtpapi turn to invalid now.

3. When sending emails without address list, designate recipients with “to”. Multiple recipients are sent through multi-transmission (all recipients will be displayed). Designate cc recipients with parameter “cc”, and bcc recipients with “bcc”.

4. When sending emails without address list, specify recipients with xsmtpapi. Multiple recipients are sent individually. Parameters “to”, “cc” and “bcc” turn to invalid now.

5. Recipients of “to”, “cc” and “bcc” cannot be more than 100; recipients of “to” in xsmtpapi cannot be more than 100.

6. Email subject defaults to the topic of emails. If both are empty, an error is received.

7. [Variable](/QuickStart/Interpretation/#Variable). is allowed in subject, html and plain. As special character, “%” needs to be processed in HTTP request.

8. When using return receipt, recipients can choose whether to send reading receipt to “from” after receiving emails.

9. If a Key in the parameter headers starts with "SC-Custom-", this Key:Value will be returned to the user through WebHook. Key:Value must be a string, and Value must not contain special characters '.'. When a Key is passed in, the corresponding Value cannot be empty, otherwise an error 40902, "Unknown exception occurred in mail processing" will be returned.

10. When using an address list (useAddressList = true), headers do not exceed 1024 bytes.


**Samples of request and returned value**

Template delivery (call template ifaxin_bill)
```
# Template content
Dear %name%:
  
    Hello! Your consumption amount this month is: %money% .
#---------------------------------------------------
# Call template send, `%`need urlencode
curl -d 'apiUser=***&apiKey=***&from=test@test.com&fromName=liubida&subject=test&replyTo=reply@test.com&templateInvokeName=ifaxin_bill' --data-urlencode 'xsmtpapi={"to": ["ben@ifaxin.com", "joe@ifaxin.com"],"sub":{"%name%": ["Ben", "Joe"],"%money%":[288, 497]}}&headers={"header1": "value1", "header2": "value2"}' http://api2.sendcloud.net/api/mail/sendtemplate

# Return value
{
  "statusCode": 200,
  "info": {
    "emailIdList": [
      "1447054895514_15555555_32350_1350.sc-10_10_126_221-inbound0$ben@ifaxin.com",
      "1447054895514_15555555_32350_1350.sc-10_10_126_221-inbound1$joe@ifaxin.com"
    ]
  },
  "message": "request was successful",
  "result": true
}


# ben@ifaxin.com received:
Dear Ben:
    
    Hello! Your consumption amount this month is: 288 .

#---------------------------------------------------

# joe@ifaxin.com received:
Dear Joe:
    
     Hello! Your consumption amount this month is: 497 .
```
Template delivery (call template ifaxin_bill, call address list user@maillist.sendcloud.org)
```
curl -d 'apiUser=***&apiKey=***&from=test@test.com&fromName=liubida&to=noexist@maillist.sendcloud.org&subject=test&replyTo=reply@test.com&templateInvokeName=ifaxin_bill&useAddressList=true' --data-urlencode 'headers={"header1": "value1", "header2": "value2"}' http://api2.sendcloud.net/api/mail/sendtemplate

# Return code
{
  "statusCode": 40863,
  "info": {},
  "message": "The Parameter to  has a list of addresses that do not exist.The Parameter to: noexist@maillist.sendcloud.org",
  "result": false
}

curl -d 'apiUser=***&apiKey=***&from=test@test.com&fromName=liubida&to=users@maillist.sendcloud.org&subject=test&replyTo=reply@test.com&templateInvokeName=ifaxin_bill&useAddressList=true' --data-urlencode 'headers={"header1": "value1", "header2": "value2"}' http://api2.sendcloud.net/api/mail/sendtemplate

# Return code
{
  "statusCode": 40821,
  "info": {
    "maillistTaskId": [
      267131
    ]
  },
  "message": "The address list task was created successfully",
  "result": true
}
```

- - -

## Send meeting calendar

**URL**

```  
https://api2.sendcloud.net/api/mail/sendcalendar
```

**HTTP Request Method**

```bash
post
```

**Parameter Description**   

| **parameter**             |**type**|**required or not**|**description**|
|:---|:---|:---|:---|
|apiUser|string|yes|API_USER|
|apiKey|string|yes|API_KEY|
|from|string|yes|sender email address, e.g. `support@ifaxin.com`,After you configure DMARC, SendCloud will take current domain as the suffix of “from”.|
|to|string|*|recipient email addresses, separated by semicolons, e.g. `ben@ifaxin.com;joe@ifaxin.com`|
|subject|string|yes|subject, cannot be empty|
|html|string|*|email content, formatted with `text/html`|
|fromName|string|no|sender name, shown as: `IFAXIN customer<support@ifaxin.com>`|
|cc|string|no|cc addresses, separated by semicolons|
|bcc|string|no|bcc addresses, separated by semicolons|
|replyTo|string|no|default reply addresses, separated by semicolons, cannot be more than 3. If “reply To” does not exist or is null, reply address defaults to “from”|
|dispositionNotificationTo|||not supported|
|labelName|string|no|The label name used for this send. If this label name is not saved in the account, it will be created automatically.|
|headers|string|no|header of email, in JSON format, e.g. `{"header1": "value1", "header2": "value2"}`|
|attachments|file|no|email attachment; when sending attachment, it must be submitted with “multipart/form – data” in “post” (form submission)|
|xsmtpapi|string|no|SMTP extension, see [X-SMTPAPI](/SendCloudSMTP/X-SMTPAPI/) for more |
|plain|string|no|email content, formatted with `text/plain`|
|respEmailId|string (true, false)|no|default value: `true`. Whether return to [emailId](/SendCloudSMTP/MessageId&EmailId/). With multiple recipients, return to the list of emailId|
|useAddressList|||not supported|
|startTime|string|yes|start time, formatted with: yyyy-MM-dd HH:mm:ss|
|endTime|string|yes|end time, formatted with: yyyy-MM-dd HH:mm:ss|
|title|string|yes|meeting title|
|organizerName|string|yes|organizer name|
|organizerEmail|string|yes|organizer email address|
|location|string|yes|meeting location|
|description|string|no|meeting description|
|participatorNames|string|yes|names of participants, separated by semicolons|
|participatorEmails|string|no|email addresses of participants, separated by semicolons|
|uid|string|no|uid parameter needs to be passed around when cancelling or updating calendar. Its value will be returned to users upon the first request of sending email calendar|
|isCancel|string (true, false)|no|default value: `false`. Cancel calendar|
|isUpdate|string (true, false)|no|default value: `false`. Update calendar|

Tips:

1. Assuming that “from” is `IFAXIN support<support@ifaxin.com>`. If “fromName” is empty, “IFAXIN support” will be set as “fromName”; if not, no processing is needed.
3. When sending emails with address lists, specify lists with parameter “to”. Each address in the email will be sent individually. Address list cannot be more than 5. cc, bcc and xsmtpapi turn to invalid now.
4. When sending emails without address list, specify recipients with xsmtpapi. Multiple recipients are sent individually. Parameters “to”, “cc” and “bcc” turn to invalid now.
5. Recipients of “to”, “cc” and “bcc” cannot be more than 100; recipients of “to” in xsmtpapi cannot be more than 100.
6. “html” and “plain” cannot be both empty . If both “html” and “plain” are not empty, “html” is in priority.
7. [Variable](/QuickStart/Interpretation/#Variable) is allowed in subject, html and plain. As special character, “%” needs to be processed in HTTP request.
7. If a Key in the parameter headers starts with "SC-Custom-", this Key:Value will be returned to the user through WebHook. Key:Value must be a string, and Value must not contain special characters '.'. When a Key is passed in, the corresponding Value cannot be empty, otherwise an error 40902 "Unknown exception occurred in mail processing" will be returned.
8. “participatorNames”, “participatorEmails” represent all participants. Generally, recipients need to be include.
9. Please contact customer service for relevant permission before using the interface.

- - -

## Query address list task

**URL**

```
https://api2.sendcloud.net/api/mail/taskinfo
```

**HTTP Request Method**



```bash
post    get
```



**Parameter Description**

|**parameter**|**type**|**required or not**|**description**|
|:---|:---|:---|:---|
|apiUser|string|yes|API_USER|
|apiKey|string|yes|API_KEY|
|maillistTaskId|int|yes|returned maillistTaskId|

**Request Example**    

```
https://api2.sendcloud.net/api/mail/taskinfo?apiUser=***&apiKey=***&maillistTaskId=1
```

**Returned value description**
    

|**Parameter**|**Description**|
|:---|:---|
|maillistTaskId|returned maillistTaskId|
|apiUser|called apiUser|
|addressList|called alias of address list|
|memberCount|count of addresses|
|gmtCreated|creation time|
|gmtUpdated|modification time|
|status|request status of address list|

**Example of Returned value**    

```
{
  "result": true,
  "statusCode": 200,
  "message": "request was successful",
  "info": {
    "data": {
      "maillistTaskId": ***,
      "apiUser": "***",
      "addressList": "***",
      "memberCount": 300,
      "gmtCreated": "2015-11-26 14:38:09",
      "gmtUpdated": "2015-11-26 14:38:23",
      "status": "Completion of the request"
    }
  }
}
```

