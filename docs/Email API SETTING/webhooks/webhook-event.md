---
title: Webhook Event
excerpt: >-
  Complete webhook events API documentation including request, delivery, open,
  click, unsubscribe, spam, bounce, and routing events with detailed parameters
  and response codes.
deprecated: false
hidden: true
metadata:
  title: Webhook Events API Reference - Email Event Types & Parameters
  description: >-
    Complete webhook events API documentation including request, delivery, open,
    click, unsubscribe, spam, bounce, and routing events with detailed
    parameters and response codes.
  robots: index
---
<br />

## Request

Parameter description

| Parameter         | Type   | Description                                                      |
| :---------------- | :----- | :--------------------------------------------------------------- |
| event             | string | event type: “request”                                            |
| message           | string | message content                                                  |
| maillistTaskId    | long   | task ID will be generated when you send emails with address list |
| mail_list_task_id | long   | task ID will be generated when you send emails with address list |
| messageId         | string | messageId                                                        |
| apiUser           | string | API_USER                                                         |
| category          | string | API_USER ID                                                      |
| recipientArray    | list   | recipients                                                       |
| emailIds          | list   | emailId array                                                    |
| labelId           | int    | custom label ID                                                  |
| labelName         | string | custom label name                                                |
| recipientSize     | int    | count of requests                                                |
| timestamp         | long   | timestamp                                                        |
| token             | string | random string of 50 characters                                   |
| signature         | string | signature string                                                 |
|                   |        |                                                                  |
| userHeaders       | string | custom header with start of “SC-Custom”                          |

## Delivery

Parameter description

<br />

| Parameter         | Type   | Description                                                      |
| :---------------- | :----- | :--------------------------------------------------------------- |
| event             | string | event type: “deliver”                                            |
| message           | string | message content                                                  |
| maillistTaskId    | long   | task ID will be generated when you send emails with address list |
| mail_list_task_id | long   | task ID will be generated when you send emails with address list |
| apiUser           | string | API_USER                                                         |
| category          | string | API_USER ID                                                      |
| emailId           | string | unique ID of each email                                          |
| recipient         | string | recipients                                                       |
| outIp             | string | outbound IP address                                              |
| labelId           | int    | custom label ID                                                  |
| labelName         | string | custom label name                                                |
| timestamp         | long   | timestamp                                                        |
| token             | string | random string of 50 characters                                   |
| signature         | string | signature string                                                 |
| userHeaders       | string | custom header with start of “SC-Custom”                          |

## Open

Parameter description

| Parameter         | Type   | Description                                                      |
| :---------------- | :----- | :--------------------------------------------------------------- |
| event             | string | event type: “open”                                               |
| message           | string | message content                                                  |
| maillistTaskId    | long   | task ID will be generated when you send emails with address list |
| mail_list_task_id | long   | task ID will be generated when you send emails with address list |
| apiUser           | string | API_USER                                                         |
| category          | string | API_USER ID                                                      |
| emailId           | string | unique ID of each email                                          |
| recipient         | string | recipients                                                       |
| labelId           | int    | custom label ID                                                  |
| labelName         | string | custom label name                                                |
| ip                | string | opened IP address                                                |
| explorerName      | string | browser name                                                     |
| explorerVer       | string | browser version                                                  |
| oSName            | string | OS name                                                          |
| oSVer             | string | OS version                                                       |
| timestamp         | long   | timestamp                                                        |
| token             | string | random string of 50 characters                                   |
| signature         | string | signature string                                                 |
| userHeaders       | string | custom header with start of “SC-Custom”                          |

## Click

Parameter description

| Parameter         | Type   | Description                                                      |
| :---------------- | :----- | :--------------------------------------------------------------- |
| event             | string | event type: “click”                                              |
| message           | string | message content                                                  |
| maillistTaskId    | long   | task ID will be generated when you send emails with address list |
| mail_list_task_id | long   | task ID will be generated when you send emails with address list |
| apiUser           | string | API_USER                                                         |
| category          | string | API_USER ID                                                      |
| emailId           | string | unique ID of each email                                          |
| recipient         | string | recipients                                                       |
| labelId           | int    | custom label ID                                                  |
| labelName         | string | custom label name                                                |
| url               | string | clicked links                                                    |
| ip                | string | clicked IP address                                               |
| explorerName      | string | browser name                                                     |
| explorerVer       | string | browser version                                                  |
| oSName            | string | OS name                                                          |
| oSVer             | string | OS version                                                       |
| timestamp         | long   | timestamp                                                        |
| token             | string | random string of 50 characters                                   |
| signature         | string | signature string                                                 |
| userHeaders       | string | custom header with start of “SC-Custom”                          |

## Unsubscribe

Parameter description

| Parameter         | Type   | Description                                                      |
| :---------------- | :----- | :--------------------------------------------------------------- |
| event             | string | event type: “unsubscribe”                                        |
| message           | string | message content                                                  |
| maillistTaskId    | long   | task ID will be generated when you send emails with address list |
| mail_list_task_id | long   | task ID will be generated when you send emails with address list |
| apiUser           | string | API_USER                                                         |
| category          | string | API_USER ID                                                      |
| emailId           | string | unique ID of each email                                          |
| recipient         | string | recipients                                                       |
| labelId           | int    | custom label ID                                                  |
| labelName         | string | custom label name                                                |
| ip                | string | IP address                                                       |
| explorerName      | string | browser name                                                     |
| explorerVer       | string | browser version                                                  |
| oSName            | string | OS name                                                          |
| oSVer             | string | OS version                                                       |
| timestamp         | long   | timestamp                                                        |
| token             | string | random string of 50 characters                                   |
| signature         | string | signature string                                                 |
| userHeaders       | string | custom header with start of “SC-Custom”                          |

## Spam Reporting

Parameter description

| Parameter   | Type   | Description                             |
| :---------- | :----- | :-------------------------------------- |
| event       | string | event type: “report_spam”               |
| message     | string | message content                         |
| apiUser     | string | API_USER                                |
| category    | string | API_USER ID                             |
| emailId     | string | unique ID of each email                 |
| recipient   | string | recipients                              |
| labelId     | int    | custom label ID                         |
| labelName   | string | custom label name                       |
| timestamp   | long   | timestamp                               |
| token       | string | random string of 50 characters          |
| signature   | string | signature string                        |
| userHeaders | string | custom header with start of “SC-Custom” |

## Invalid Email

Parameter description

| Parameter         | Type    | Description                                                      |
| :---------------- | :------ | :--------------------------------------------------------------- |
| event             | string  | event type: “unsubscribe”                                        |
| message           | string  | message content                                                  |
| maillistTaskId    | long    | task ID will be generated when you send emails with address list |
| mail_list_task_id | long    | task ID will be generated when you send emails with address list |
| apiUser           | string  | API_USER                                                         |
| category          | string  | API_USER ID                                                      |
| emailId           | string  | unique ID of each email                                          |
| recipient         | string  | recipients                                                       |
| labelId           | int     | custom label ID                                                  |
| labelName         | string  | custom label name                                                |
| outIp             | string  | outbound IP address                                              |
| timestamp         | long    | timestamp                                                        |
| token             | string  | random string of 50 characters                                   |
| signature         | string  | signature string                                                 |
| userHeaders       | string  | custom header with start of “SC-Custom”                          |
| substatdesc       | string  | invalid subclass description                                     |
| substat           | integer | invalid subclass                                                 |

Substat's return code and description：

| subStat | subStatDesc                 |
| :------ | :-------------------------- |
| 401     | in SendCloud blocklist      |
| 402     | unsubscribe                 |
| 403     | server unreachable          |
| 404     | address format error        |
| 405     | IP and domain rejected      |
| 406     | address does not exist      |
| 407     | spam                        |
| 408     | sender / recipient rejected |
| 409     | others                      |

## Soft Bounce

Parameter description

| Parameter         | Type    | Description                                                      |
| :---------------- | :------ | :--------------------------------------------------------------- |
| event             | string  | event type: “soft_bounce”                                        |
| message           | string  | message content                                                  |
| maillistTaskId    | long    | task ID will be generated when you send emails with address list |
| mail_list_task_id | long    | task ID will be generated when you send emails with address list |
| apiUser           | string  | API_USER                                                         |
| category          | string  | API_USER ID                                                      |
| emailId           | string  | unique ID of each email                                          |
| recipient         | string  | recipients                                                       |
| labelId           | int     | custom label ID                                                  |
| labelName         | string  | custom label name                                                |
| outIp             | string  | outbound IP address                                              |
| timestamp         | long    | timestamp                                                        |
| token             | string  | random string of 50 characters                                   |
| signature         | string  | signature string                                                 |
| userHeaders       | string  | custom header with start of “SC-Custom”                          |
| substatdesc       | string  | soft drop back subclass description                              |
| substat           | integer | soft drop back subclass                                          |
| cause             | string  | reasons for soft credit withdrawal                               |

Substat's return code and description：

| subStat | subStatDesc                  |
| :------ | :--------------------------- |
| 503     | service not available        |
| 505     | ip or domain rejected        |
| 506     | email address does not exist |
| 507     | spam                         |
| 508     | sender / recipient rejected  |
| 509     | others                       |

## Mail Routing

Parameter description

| Parameter       | Type   | Description                                                                                                                                                      |
| :-------------- | :----- | :--------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| event           | string | event type: “route”                                                                                                                                              |
| message         | string | message content “mx route”                                                                                                                                       |
| timestamp       | long   | timestamp                                                                                                                                                        |
| from            | string | sender email address                                                                                                                                             |
| fromname        | string | sender name                                                                                                                                                      |
| to              | string | recipients address                                                                                                                                               |
| toname          | string | recipient name                                                                                                                                                   |
| x_mx_mailfrom   | string | envelope sender                                                                                                                                                  |
| x_mx_rcptto     | string | Actual recipient address                                                                                                                                         |
| headers         | string | email headers, formatted with JSON                                                                                                                               |
| html            | string | content in html format of routing email                                                                                                                          |
| text            | string | content in text format of routing email                                                                                                                          |
| subject         | string | subject                                                                                                                                                          |
| raw_message_url | string | The download link of the route email, the suffix of the download file is '.eml', and the link is valid for 15 days                                               |
| raw_message     | string | raw email                                                                                                                                                        |
| token           | string | random string of 50 characters                                                                                                                                   |
| signature       | string | signature string                                                                                                                                                 |
| userHeaders     | string | custom header with start of “SC-Custom”                                                                                                                          |
| reference       | string | If there is a value, it is: Message-ID of the email sent by Aurora SendCloud                                                                                     |
| emailId         | string | The unique id of the parent email. This field allows the reply email to be associated with the parent email. This value is parsed from reference and In-Reply-To |
| labelId         | int    | Parent email customized label ID                                                                                                                                 |
| labelName       | string | Parent email customized label Name                                                                                                                               |

Note:

1. When you do not pass in a custom Message-ID, the Message-ID in reference is automatically generated according to the platform rules, and the prefix of the Message-ID is the same as the prefix of the emailid. When you pass in a custom Message-ID through an SMTP request, the Message-ID in reference will be the Message-ID you passed in. When the reply email does not match the parent email, it will be empty.
2. eg："reference"："[1644468027883_1024_25239_6195.sg-10_1_253_1-inbound0@ifaxin.com](mailto:1644468027883_1024_25239_6195.sg-10_1_253_1-inbound0@ifaxin.com) (opens new window)" #ifaxin.com is the send domain name.
3. Java parsing EML file example,click here download
