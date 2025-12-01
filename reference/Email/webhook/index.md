---
title: Webhook
excerpt: 'A webhook is a mechanism for asynchronously receiving event notifications. '
hidden: false
---
<br />

# WebHooks

After you submit an email delivery request to Aurora SendCloud, the system synchronously returns the request result (such as whether the request was accepted). The final delivery result of the email (such as whether it was successfully delivered) and other interaction events (such as opens and clicks) are asynchronously pushed to your specified server via webhook.

Instead of requiring you to poll for updates, Aurora SendCloud actively pushes data to you in real-time when key events occur. This enables subsequent processes like data synchronization, statistical analysis, and triggering business workflows.

## How It Works

**Event Occurs:** When an email-related event occurs (such as an email being opened, a recipient clicking a link, or the email bouncing), Aurora SendCloud generates corresponding data.

**Trigger Notification:** Aurora SendCloud immediately sends an HTTP POST request to the URL you configured in your account settings.

**Data Transfer:** The event data is contained within the body of the POST request, typically encoded in JSON format.

**Receive & Process:** Your server receives the request, parses the data, and handles subsequent business logic (such as updating a database or sending an internal alert) based on the event type.

## Supported Event Types

Currently, Aurora SendCloud supports notifications for the following event types (partial list of common events):

| Event Type    | Description                                                   |
| :------------ | :------------------------------------------------------------ |
| request       | Send request event                                            |
| delivered     | Message successfully delivered to the recipient's mail server |
| open          | Recipient opened the email                                    |
| click         | Recipient clicked a link in the email                         |
| unsubscribe   | Recipient clicked the unsubscribe link                        |
| spam-report   | Recipient reported the email as spam                          |
| invalid_email | Invalid email address                                         |
| soft_bounce   | Soft bounce (temporary delivery failure)                      |
| route         | Routing status event                                          |

For the complete official list of event types and their detailed payload formats, please refer to the [Webhook Event Format Documentation].

## Configuration & Usage Steps

**Set the Webhook URL:**
Log in to the Aurora SendCloud platform, navigate to the Webhook settings page, and specify the API endpoint URL on your server that will receive the events.

**Validate the Endpoint:**
Ensure your server can correctly handle any validation requests sent by Aurora SendCloud to confirm URL accessibility.

**Parse Event Data:**
Write code to parse the JSON data in the POST request body and handle it accordingly based on the event type (such as identified by an event field).

**Return Success Status:**
After successfully receiving and processing the data, your server should return a 2xx HTTP status code (such as 200 OK) to Aurora SendCloud. If a non-2xx status code is returned, Aurora SendCloud may attempt to retry the notification based on its retry policy.

## Important Notes

**Retry Mechanism:** If your server is unreachable or does not return a successful response, Aurora SendCloud will typically retry the notification after a delay, up to a predefined retry limit.

**Security Verification:** It is highly recommended to implement security checks in your endpoint code (such as verifying the request source IP against a whitelist or validating a signature) to ensure requests are genuinely from Aurora SendCloud and prevent spoofing.

**Processing Performance:** Ensure your receiving endpoint can respond quickly (such as within 50ms) to avoid timeouts that might cause Aurora SendCloud to misinterpret the delivery as a failure.

<br />

## Webhook Event Description

**Request ( request )**

| Parameter         | Type   | Description                                                      |
| :---------------- | :----- | :--------------------------------------------------------------- |
| event             | string | event type: “request”                                            |
| message           | string | message content                                                  |
| maillistTaskId    | long   | task ID will be generated when you send emails with address list |
| mail_list_task_id | long   | task ID will be generated when you send emails with address list |
| messageId         | string | messageId                                                        |
| apiUser           | string | API_USER                                                         |
| category          | string | message ID                                                       |
| recipientArray    | list   | recipients                                                       |
| emailIds          | list   | emailId array                                                    |
| labelId           | int    | custom label ID                                                  |
| labelName         | string | custom label name                                                |
| recipientSize     | int    | count of requests                                                |
| timestamp         | long   | timestamp                                                        |
| token             | string | random string of 50 characters                                   |
| signature         | string | signature string                                                 |
| userHeaders       | string | custom header with start of “SC-Custom”                          |

<br />

**Delivery ( deliver )**

| parameter         | type   | description                                                      |
| ----------------- | ------ | ---------------------------------------------------------------- |
| event             | string | event type: "deliver"                                            |
| message           | string | message content                                                  |
| apiUser           | string | API_USER                                                         |
| category          | string | API_USER                                                         |
| maillistTaskId    | long   | task ID will be generated when you send emails with address list |
| mail_list_task_id | long   | task ID will be generated when you send emails with address list |
| emailId           | string | unique ID of each email                                          |
| outIp             | string | outbound IP address                                              |
| recipient         | string | recipients                                                       |
| labelId           | int    | custom label ID                                                  |
| labelName         | string | custom label name                                                |
| timestamp         | long   | timestamp                                                        |
| token             | string | random string of 50 characters                                   |
| signature         | string | signature string                                                 |
| userHeaders       | string | custom header with start of "SC-Custom"                          |

<br />

**Open ( open )**

| parameter         | type   | description                                                      |
| ----------------- | ------ | ---------------------------------------------------------------- |
| event             | string | event type: "open"                                               |
| message           | string | message content                                                  |
| apiUser           | string | API_USER                                                         |
| category          | string | API_USER                                                         |
| maillistTaskId    | long   | task ID will be generated when you send emails with address list |
| mail_list_task_id | long   | task ID will be generated when you send emails with address list |
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
| userHeaders       | string | custom header with start of "SC-Custom"                          |

<br />

**Click ( click )**

| parameter         | type   | description                                                      |
| ----------------- | ------ | ---------------------------------------------------------------- |
| event             | string | event type: "type"                                               |
| message           | string | message content                                                  |
| apiUser           | string | API_USER                                                         |
| category          | string | API_USER                                                         |
| maillistTaskId    | long   | task ID will be generated when you send emails with address list |
| mail_list_task_id | long   | task ID will be generated when you send emails with address list |
| emailId           | string | unique ID of each email                                          |
| recipient         | string | recipients                                                       |
| labelId           | int    | custom label ID                                                  |
| labelName         | string | custom label name                                                |
| url               | string | clicked links                                                    |
| ip                | string | clicked IP addresses                                             |
| explorerName      | string | browser name                                                     |
| explorerVer       | string | browser version                                                  |
| oSName            | string | OS name                                                          |
| oSVer             | string | OS version                                                       |
| timestamp         | long   | timestamp                                                        |
| token             | string | random string of 50 characters                                   |
| signature         | string | signature string                                                 |
| userHeaders       | string | custom header with start of "SC-Custom"                          |

<br />

**Unsubscribe ( unsubscribe )**

| parameter         | type   | description                                                      |
| ----------------- | ------ | ---------------------------------------------------------------- |
| event             | string | event type: "unsubscribe"                                        |
| message           | string | message content                                                  |
| apiUser           | string | API_USER                                                         |
| category          | string | API_USER                                                         |
| labelId           | int    | custom label ID                                                  |
| labelName         | string | custom label name                                                |
| maillistTaskId    | long   | task ID will be generated when you send emails with address list |
| mail_list_task_id | long   | task ID will be generated when you send emails with address list |
| emailId           | string | unique ID of each email                                          |
| recipient         | string | recipients                                                       |
| ip                | string | IP address                                                       |
| explorerName      | string | explorer name                                                    |
| explorerVer       | string | explorer version                                                 |
| oSName            | string | OS name                                                          |
| oSVer             | string | OS version                                                       |
| timestamp         | long   | timestamp                                                        |
| token             | string | random string of 50 characters                                   |
| signature         | string | signature string                                                 |
| userHeaders       | string | custom header with start of "SC-Custom"                          |

<br />

**Spam Reporting ( report_spam )**

| parameter   | type   | description                             |
| ----------- | ------ | --------------------------------------- |
| event       | string | event type: "report_spam"               |
| message     | string | message content                         |
| apiUser     | string | API_USER                                |
| category    | string | API_USER                                |
| labelId     | int    | custom label ID                         |
| labelName   | string | custom label name                       |
| emailId     | string | unique ID of each email                 |
| recipient   | string | recipients                              |
| timestamp   | long   | timestamp                               |
| token       | string | random string of 50 characters          |
| signature   | string | signature string                        |
| userHeaders | string | custom header with start of "SC-Custom" |

<br />

**Invalid Email ( invalid )**

| parameter         | type    | description                                                      |
| ----------------- | ------- | ---------------------------------------------------------------- |
| event             | string  | event type: "invalid"                                            |
| message           | string  | message content                                                  |
| apiUser           | string  | API_USER                                                         |
| category          | string  | API_USER                                                         |
| labelId           | int     | custom label ID                                                  |
| labelName         | string  | custom label name                                                |
| maillistTaskId    | long    | task ID will be generated when you send emails with address list |
| mail_list_task_id | long    | task ID will be generated when you send emails with address list |
| emailId           | string  | unique ID of each email                                          |
| outIp             | string  | outbound IP address                                              |
| recipient         | string  | recipients                                                       |
| timestamp         | long    | timestamp                                                        |
| token             | string  | random string of 50 characters                                   |
| signature         | string  | signature string                                                 |
| userHeaders       | string  | custom header with start of "SC-Custom"                          |
| substatdesc       | string  | invalid subclass description                                     |
| substat           | integer | invalid subclass                                                 |

<br />

Substat's Return Code and Description

| subStat | subStatDesc                 |
| ------- | --------------------------- |
| 401     | in SendCloud blacklist      |
| 402     | unsubscribe                 |
| 403     | server unreachable          |
| 404     | address format error        |
| 405     | IP and domain rejected      |
| 406     | address does not exist      |
| 407     | spam                        |
| 408     | sender / recipient rejected |
| 409     | others                      |

<br />

**Soft Bounce ( soft_bounce )**

| parameter         | type    | description                                                      |
| ----------------- | ------- | ---------------------------------------------------------------- |
| event             | string  | event type: "soft_bounce"                                        |
| apiUser           | string  | API_USER                                                         |
| category          | string  | API_USER                                                         |
| labelId           | int     | custom label ID                                                  |
| labelName         | string  | custom label name                                                |
| maillistTaskId    | long    | task ID will be generated when you send emails with address list |
| mail_list_task_id | long    | task ID will be generated when you send emails with address list |
| emailId           | string  | unique ID of each email                                          |
| outIp             | string  | outbound IP address                                              |
| recipient         | string  | recipients                                                       |
| timestamp         | long    | timestamp                                                        |
| token             | string  | random string of 50 characters                                   |
| signature         | string  | signature string                                                 |
| userHeaders       | string  | custom header with start of "SC-Custom"                          |
| substatdesc       | string  | soft drop back subclass description                              |
| substat           | integer | soft drop back subclass                                          |
| cause             | string  | reasons for soft credit withdrawal                               |

<br />

Substat's Return Code and Description

| subStat | subStatDesc                  |
| ------- | ---------------------------- |
| 503     | service not available        |
| 505     | ip or domain rejected        |
| 506     | email address does not exist |
| 507     | spam                         |
| 508     | sender / recipient rejected  |
| 509     | others                       |

<br />

**Mail Routing (route)**

| parameter       | type   | description                                                                                                                                                       |
| --------------- | ------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| event           | string | event type: "route"                                                                                                                                               |
| message         | string | message content "mx route"                                                                                                                                        |
| timestamp       | long   | timestamp                                                                                                                                                         |
| from            | string | sender email address                                                                                                                                              |
| fromname        | string | sender name                                                                                                                                                       |
| to              | string | recipients address                                                                                                                                                |
| toname          | string | recipient name                                                                                                                                                    |
| x_mx_mailfrom   | string | envelope sender                                                                                                                                                   |
| x_mx_rcptto     | string | Actual recipient address                                                                                                                                          |
| headers         | string | email headers, formatted with JSON                                                                                                                                |
| html            | string | content in html format of routing email                                                                                                                           |
| text            | string | content in text format of routing email                                                                                                                           |
| subject         | string | subject                                                                                                                                                           |
| raw_message_url | string | The download link of the route email, the suffix of the download file is '.eml', and the link is valid for 15 days                                                |
| raw_message     | string | raw email                                                                                                                                                         |
| token           | string | random string of 50 characters                                                                                                                                    |
| signature       | string | signature string                                                                                                                                                  |
| userHeaders     | string | Custom header with start of "SC-Custom"                                                                                                                           |
| reference       | string | If there is a value, it is: Message-ID of the email sent by SendCloud                                                                                             |
| emailId         | string | The unique id of the parent email. This field allows the reply email to be associated with the parent email. This value is parsed from reference and In-Reply-To. |
| labelId         | int    | Parent email customized label ID                                                                                                                                  |
| labelName       | string | Parent email customized label Name                                                                                                                                |


Note:

1. When you do not pass in a custom Message-ID, the Message-ID in reference is automatically generated according to the platform rules, and the prefix of the Message-ID is the same as the prefix of the emailid. When you pass in a custom Message-ID through an SMTP request, the Message-ID in reference will be the Message-ID you passed in. When the reply email does not match the parent email, it will be empty.
2. eg："reference"："[1644468027883_1024_25239_6195.sg-10_1_253_1-inbound0@ifaxin.com](mailto:1644468027883_1024_25239_6195.sg-10_1_253_1-inbound0@ifaxin.com)
   (opens new window)
   " #ifaxin.com is the send domain name.
3. Java parsing EML file example,click here download

<br />

<br />
