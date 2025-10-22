---
title: Campaigns
deprecated: false
hidden: false
link:
  new_tab: false
metadata:
  robots: index
---
# Campaigns

## Create a Regular Email Campaign

To create a regular email campaign, follow these steps:

1. **Determine recipients**: Select who will receive your email campaign. You can choose from All Contacts, specific Tags, or Segments.
2. **Choose the sender**: Specify who the email is from, which tells recipients the sender's identity.
3. **Set reply email address**: Enter the email address where you want to receive recipients' replies.
4. **Select email template**: Choose one of your email templates that contains the message you want recipients to read.
5. **Configure advanced settings** (optional): Decide whether to use advanced settings for your campaign.
6. **Set execution time**: Choose when to send the campaign and select the correct time zone.

## Create an A/B Test Email Campaign

### Step 1: Design Your Test Item and Rules

1. **Choose what to test**: Select which element you want to test. Options include:
   * Email subject line
   * Email content
   * Sender name
   * Send time
   _Note: Each test supports up to 3 different variations._

2. **Determine the winning criteria**: Choose how to judge the winner and set the evaluation time after the campaign begins:
   * Open rate
   * Unique open rate
   * Click rate
   * Unique click rate
   * Delivery rate

3. **Set test percentage**: Choose what percentage of recipients to include in the test. For example, if you select 20%, we'll test with 20% of your recipients, and the remaining 80% will receive the winning variation.

### Step 2: Complete Campaign Information

1. **Determine recipients**: Select who will receive your email campaign (All Contacts, Tags, or Segments).
2. **Choose the sender**: Specify the sender name that recipients will see.
3. **Set reply email address**: Enter the email address for receiving replies.
4. **Select email template**: Choose your desired email template with the message content.
5. **Set execution time**: Schedule when to send the campaign and select the appropriate time zone.

## Advanced Campaign Settings

_Advanced settings are only available for regular email campaigns._

### Google Analytics Tracking

If your email contains hyperlinks and the corresponding landing pages support Google Analytics, you can enable this feature. Available parameters include:

* **Campaign Name**: Google Analytics utm_campaign parameter
* **Campaign Source**: Google Analytics utm_source parameter
* **Campaign Medium**: Google Analytics utm_medium parameter
* **Campaign Term**: Google Analytics utm_term parameter
* **Campaign Content**: Google Analytics utm_content parameter

When Google Analytics Tracking is enabled, SendCloud automatically adds these parameters to your email links.

**Example:**

* Original link: `https://www.aurorasendcloud.com`
* Modified link: `https://web.sendcloud.net?utm_campaign=XX&utm_source=SendCloud&utm_medium=email&utm_term=xx&utm_content=xxxxx`

### Warm-Up Sending

Enable this feature to improve delivery rates for email providers like Gmail and Yahoo, and reduce quota-related failures.

Before establishing a good reputation with email providers, even high-quality subscription emails sent in large volumes may be rejected or marked as spam. Warm-up sending helps by controlling transmission rates and gradually increasing sending volume.

<Image border={false} src="https://files.readme.io/dc1e1222d0a22e94e3abb7b0311b7b63ed54ed96a9b1fdf283a29cc9582e100f-image.png" />

<br />

When using warm-up sending, you can select an initial rate. SendCloud monitors delivery rates and:

* **Increases the rate every 24 hours** when delivery rate exceeds the set rate
* **Decreases the rate every 24 hours** when delivery rate falls below the set rate

**Rate Progression Table:**

| Step   | 1   | 2    | 3   | 4    | 5   | 6   | 7    | 8   | 9    | 10   | 11  | 12  | 13   | 14    | 15   |
| ------ | --- | ---- | --- | ---- | --- | --- | ---- | --- | ---- | ---- | --- | --- | ---- | ----- | ---- |
| Hourly | 100 | 250  | 500 | 650  | 800 | 1k  | 1.4k | 2k  | 2.5k | 3.5k | 5k  | 8k  | 12k  | 17.5k | 25k  |
| Daily  | 1k  | 2.5k | 5k  | 6.5k | 8k  | 10k | 14k  | 20k | 25k  | 35k  | 50k | 80k | 120k | 175k  | 250k |

## Campaign Status

**Waiting**: Campaign hasn't reached execution time and is waiting to be sent. You can modify or delete the campaign in this state.

**Sending**: Campaign emails are currently being sent. You can view campaign reports in this state.

**Failure**: Campaign failed to initiate. View campaign details for specific failure reasons.

**Common failure causes:**

* Insufficient available emails in account
* Insufficient daily quota
* Authentication failure (API_KEY modified before campaign start)

## Campaign Reports

### Overview

Provides overall sending progress data and displays sending status for the top five receiving domains.

### Tracking

Statistics for campaign opens, clicks, unsubscribes, complaints, and other engagement data.

### Statistics

* **Geographic data**: Distribution and ranking of email reading locations
* **Link performance**: Click rates on email links and reading conversion rates
* **Device information**: Equipment, browsers, operating systems, device types, and mobile carriers used when reading emails

### Exportable Data

From the upper right corner of the campaign report, you can export:

* Domain-level statistics
* Email tracking details
* Email failure details
