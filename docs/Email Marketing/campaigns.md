---
title: Campaigns
deprecated: false
hidden: false
metadata:
  robots: index
---
<br />

## Create a regular email campaign

you need to do the followin:

1. Determine the recipients that you want to send the email campaign to. You can select All Contacts or Tag or Segment.
2. Choose the sender.Telling the recipients who send the email.
3. Filling the reply email address that you can receive the recipients' reply.
4. Choose one of your email template that has the message you want the recipients to read.
5. Choose whether to use the advaned setting or not.
6. Set the execution time .Please choose the right time zone.

## Create an A/B test email campaign

### Step 1. you need design your test item and the test rule.

1. Determine which one you would like to test ,it could be the email subject , email content , from or send time.And Each test only can support 3 different item.
2. Detemine how to judge the winner.  You can choose the following condition and the judge time after the campaign begin.
   1. By open ratio
   2. By unique open radio
   3. By click radio
   4. By unique click radio
   5. By delivered radio
3. Choose the test percentage of  the recipients.If you choose 20%,we will use 20% of the recipients to test, and the remaining 80% of the recipients will continue to send according to the winner's setting .

### Step 2 . Fill in the rest info of a campaign

1. Determine the recipients that you want to send the email campaign to. You can select All Contacts or Tag or Segment.
2. Choose the sender.Telling the recipients who send the email.
3. Filling the reply email address that you can receive the recipients' reply.
4. Choose one of your email template that has the message you want the recipients to read.
5. Set the execution time .Please choose the right time zone.

<br />

## Advanced Setting of a campaign

the advanced setting is only available in regular email campaign

### Google Analytics Tracking

If your email contains hyperlinks and the corresponding landing page supports Google analysis, you can turn on this switch. Parameters that can be filled in

* Campaign Name stand for Google Analytics - utm_campaign
* Campaign Source stand for Google Analytics - utm_source
* Campaign Medium stand for Google Analytics - utm_medium
* Campaign Term stand for Google Analytics - utm_term
* Campaign Content stand for Google Analytics - utm_content
  When you open Google Analytics Tracking, SendCloud will add parameters to the original email link according to the data you fill in.

For example:

a link in the content of an email [https://www.aurorasendcloud.com](https://www.aurorasendcloud.com) After treatment, it will become [https://web.sendcloud.net?utm_campaign=XX&utm_source=SendCloud&utm_medium=email&utm_term=xx&utm_content=xxxxx](https://web.sendcloud.net?utm_campaign=XX\&utm_source=SendCloud\&utm_medium=email\&utm_term=xx\&utm_content=xxxxx)

### Warm Up Sending

If you want to improve the delivery rate of mailboxes such as gmail.com \ yahoo.com and reduce the failure of returning over quota, you can turn this switch on.

Before you establish a good reputation with your mailbox, even if you send high-quality subscriptions in a short time, they will be rejected or marked as spam by the mailbox provider. In this case, such problems can be avoided by controlling the transmission rate and gradually increasing the transmission volume.

When you decide to use warm-up sending, you can select an initial rate, and then sendcloud will pay close attention to the delivery rate. When the delivery rate is above 85%, the rate will be increased every 24 hours; Conversely, the rate will be reduced every 24 hours.

Rate Table

| Step   | 1   | 2    | 3   | 4    | 5   | 6   | 7    | 8   | 9    | 10   | 11  | 12  | 13   | 14    | 15   |
| ------ | --- | ---- | --- | ---- | --- | --- | ---- | --- | ---- | ---- | --- | --- | ---- | ----- | ---- |
| Hourly | 100 | 250  | 500 | 650  | 800 | 1k  | 1.4k | 2k  | 2.5k | 3.5k | 5k  | 8k  | 12k  | 17.5k | 25k  |
| Daily  | 1k  | 2.5k | 5k  | 6.5k | 8k  | 10k | 14k  | 20k | 25k  | 35k  | 50k | 80k | 120k | 175k  | 250k |

<br />

## State fo Campaign

**Waiting** : Campaign has not reached execution time, waiting for execution. In this state, you can modify or delete the campaign.

**Sending**: Campaign mail is being sent. In this state, you can view campaign reports.

**Failure** : Campaign initiate failed. For specific reasons, you can view the campaign details, and the message will tell you the reason for the start failure.

Common causes of failure：

* The number of e-mails available in the account is insufficient.
* Daily quota is insufficient.
* Authentication failed. The API_KEY was modified before the campaign started.

## Report of Campaign

**Overview**
Provide the overall sending progress data, and support to view the sending status of the top five receiving domains.

**Traking**
Statistics for you the task to open, click, unsubscribe, complaints and other data.

**Statistics**

* Distribution and ranking of l reading locations.
* Click on email links and reading conversion rate.
* The Equipment, Browser, operating system, device end and wireless brand used when reading e-mail

The following data can be exported from the upper right corner of the task report

* Domain  dimension statistics
* Email tracking details
* Email failure details
