---
title: Sending Options
deprecated: false
hidden: false
link:
  new_tab: false
metadata:
  robots: index
---
# Sending Options

Configure your email sending settings to optimize deliverability and control how your emails are sent through Aurora SendCloud.

## Email Sender Configuration

### Understanding "From" vs "Mail From"

**From Address**

* The sender shown in the email content to recipients
* Must be a valid email address format
* Can be customized to any legal email address via API or SMTP
* This is what recipients see as the sender

**Mail From Address**

* The envelope sender (also known as return-path)
* Acts as the "secretary" that delivers the message on behalf of the "From" address
* Suffix is controlled by Aurora SendCloud and matches your sending domain
* Prefix can be customized or will be auto-generated as a random string

### Why Use Random Mail From Prefixes?

By default, Aurora SendCloud generates random strings for mail from prefixes to prevent email providers from limiting delivery based on sender reputation. This helps avoid restrictions when the same mail from address is used repeatedly.

### Handling Address Inconsistencies

When the "From" and "Mail From" addresses have different suffixes, emails are sent "on behalf of" the From address. This can cause issues:

* Strict email providers may send emails to spam folders
* Some providers may reject emails entirely
* Only specific email providers accept "on behalf of" sending

## Advanced Sending Options

### Fixed From Suffix

Enable this option to ensure the From address suffix matches the Mail From suffix. This setting:

* Eliminates "on behalf of" sending
* Can be configured per domain in Aurora SendCloud
* Provides better email authentication

### Fixed Mail From

Instead of using random prefixes, you can set a fixed Mail From address. This is useful when:

* You need consistent sender identification
* Specific email providers require fixed addressing
* You want better tracking and analytics

### Auto AD Tag

**Recommended for bulk marketing emails**

* Automatically enabled for all batch API_USER accounts
* Adds advertising tags to email subjects
* Helps prevent emails from being marked as spam
* Improves compliance with anti-spam regulations

### TLS Encryption

Enable secure data transmission for your emails:

* Encrypts email content during transmission
* Recommended when handling sensitive information
* **Note**: May reduce sending speed - enable only when necessary

## Delivery Control Features

### Do Not Disturb Hours

Prevent emails from being sent during specific time periods to improve user experience:

* Set quiet hours (e.g., 23:00 to 6:00 AM)
* System automatically suspends email delivery during configured periods
* Helps maintain good sender reputation

### Sending Uninterception

Override Aurora SendCloud's automatic blacklist filtering for specific addresses or domains:

* Add addresses or domains to bypass interception
* Useful for testing or critical communications
* Overrides bounce, complaint, unsubscribe, and block lists

### Bounce Interception

**Default: Enabled**

Aurora SendCloud automatically blocks addresses that have previously bounced:

* Prevents sending to non-existent email addresses
* Reduces bounce rates and improves sender reputation
* Returns "in blacklist: bounce" error for intercepted addresses
* Can be disabled if needed through Options settings

## Best Practices

* Keep bounce interception enabled to maintain good sender reputation
* Use TLS encryption only when handling sensitive data
* Configure do not disturb hours based on your audience's time zone
* Enable Auto AD tag for marketing campaigns
* Consider fixed addressing for transactional emails
