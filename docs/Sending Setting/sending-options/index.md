---
title: Sending Options
excerpt: >-
  Configure your email sending settings to optimize deliverability and control
  how your emails are sent through Aurora SendCloud.
deprecated: false
hidden: false
link:
  new_tab: false
metadata:
  title: Email Sending Options & Configuration Guide | Aurora SendCloud Setup
  description: >-
    Configure Aurora SendCloud email sending settings for optimal
    deliverability. Learn about From vs Mail From addresses, TLS encryption,
    bounce interception, and advanced delivery controls.
  keywords:
    - email deliverability
    - From setup
    - Mail From configuration
    - TLS encryption
    - bounce interception
    - email configuration
    - Aurora SendCloud settings
  robots: index
---
<br />

## Email Sender Configuration

### What is "From" vs "Mail From"?

**From**

<Callout icon="📘" theme="info">
  * The sender shown in the email content to recipients
  * Must be a valid email address format
  * Can be customized to any legal email address via API or SMTP
  * This is what recipients see as the sender
</Callout>

**Mail From**

<Callout icon="📘" theme="info">
  * The envelope sender (also known as return-path)
  * Acts as the "secretary" that delivers the message on behalf of the "From" address
  * Suffix is controlled by Aurora SendCloud and matches your sending domain
  * Prefix can be customized or will be auto-generated as a random string
</Callout>

### Why Does Aurora SendCloud Use a Random Default Mail From Prefix?

By default, <Anchor label="Aurora SendCloud" target="_blank" href="https://www.aurorasendcloud.com">Aurora SendCloud</Anchor> generates random strings for mail from prefixes to prevent email providers from limiting delivery based on sender reputation. This helps avoid restrictions when the same mail from address is used repeatedly.

### What Happens When From vs. Mail From Don't Match? How to Fix It.

When the "From" and "Mail From" addresses have different suffixes, emails are sent "on behalf of" the From address. This can cause issues:

* Strict email providers may send emails to spam folders
* Some providers may reject emails entirely
* Only specific email providers accept "on behalf of" sending

**Fixed From Suffix**

Enable this option to ensure the From address suffix matches the Mail From suffix. This setting:

<Callout theme="default">
  * Eliminates "on behalf of" sending
  * Can be configured per domain in Aurora SendCloud
  * Provides better [email authentication](https://www.aurorasendcloud.com/blog/guide-to-email-authentication)
</Callout>

**Fixed Mail From**

Instead of using random prefixes, you can set a fixed Mail From address. This is useful when:

<Callout theme="default">
  * You need consistent sender identification
  * Specific email providers require fixed addressing
  * You want better [tracking and analytics](https://www.aurorasendcloud.com/analytics-report)
</Callout>

## Advanced Sending Options

### Auto AD Tag

**Recommended for bulk marketing emails**

<Callout theme="default">
  * Automatically enabled for all batch API_USER accounts
  * Adds advertising tags to email subjects
  * Helps prevent emails from being marked as spam
  * Improves compliance with anti-spam regulations
</Callout>

### TLS Encryption

Enable secure data transmission for your emails:

<Callout theme="default">
  * Encrypts email content during transmission
  * Recommended when handling sensitive information
</Callout>

**Note**: May reduce sending speed - enable only when necessary

## Delivery Control Features

### Do Not Disturb Hours

Prevent emails from being sent during specific time periods to improve user experience:

<Callout icon="👍" theme="okay">
  * Set quiet hours (e.g., 23:00 to 6:00 AM)
  * System automatically suspends email delivery during configured periods
  * Helps maintain good sender reputation
</Callout>

### Allow List

Override Aurora SendCloud's automatic blocklist filtering for specific addresses or domains:

<Callout theme="default">
  * Add addresses or domains to bypass interception
  * Useful for testing or critical communications
  * Overrides bounce, complaint, unsubscribe, and block lists
</Callout>

### Bounce Interception

**Default: Enabled**

Aurora SendCloud automatically blocks addresses that have previously bounced:

<Callout theme="default">
  * Prevents sending to non-existent email addresses
  * Reduces bounce rates and improves sender reputation
  * Returns "in blacklist: bounce" error for intercepted addresses
  * Can be disabled if needed through Options settings
</Callout>

<br />

## Best Practices

<Callout icon="👍" theme="okay">
  * Keep bounce interception enabled to maintain good sender reputation
  * Use TLS encryption only when handling sensitive data
  * Configure do not disturb hours based on your audience's time zone
  * Enable Auto AD tag for marketing campaigns
  * Consider fixed addressing for [transactional emails](https://www.aurorasendcloud.com/email-api#transactional)
</Callout>
