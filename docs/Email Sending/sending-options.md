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

Configure your email delivery settings to optimize performance and ensure reliable message delivery through Aurora SendCloud.

## Email Address Settings

### From vs Mail From Addresses

**From Address**
- The sender address visible to email recipients
- Must use valid email format
- Can be any legal email address when using API or SMTP
- This is what your recipients see as the message sender

**Mail From Address** 
- The envelope sender used for email routing
- Acts as the delivery agent for your From address  
- Suffix automatically matches your sending domain
- Prefix can be customized or auto-generated

**Why Random Prefixes?**
Aurora SendCloud uses random Mail From prefixes by default to prevent email providers from rate-limiting based on sender volume. This avoids delivery restrictions from repeated use of identical addresses.

**Address Mismatch Issues**
When From and Mail From suffixes differ, emails appear as "sent on behalf of" messages. This can result in:
- Delivery to spam folders
- Message rejection by strict email providers
- Reduced deliverability rates

### Address Configuration Options

**Fixed From Suffix**
- Ensures From address suffix matches Mail From suffix
- Eliminates "on behalf of" sending
- Improves email authentication
- Can be configured per domain

**Fixed Mail From**
- Uses consistent Mail From address instead of random prefixes
- Better for tracking and sender identification
- Recommended for transactional emails

## Delivery Enhancement Features

### Auto AD Tag
*Enabled by default for bulk sending*

Automatically adds advertising identifiers to marketing email subjects to:
- Improve spam filter compliance
- Reduce false positive spam detection  
- Meet anti-spam regulation requirements
- **Recommended**: Keep enabled for all marketing campaigns

### TLS Encryption

Secures email transmission with encryption:
- Protects sensitive email content during delivery
- Required for handling confidential information
- **Trade-off**: May reduce sending speed
- Enable only when security is essential

### Do Not Disturb Hours

Prevents email delivery during specified time periods:
- Configure quiet hours (example: 11 PM to 6 AM)
- Improves recipient experience
- Maintains positive sender reputation
- System automatically queues emails during blocked hours

## Anti-Spam Protection

### Automatic Interception

Aurora SendCloud maintains four protection lists:
- **Bounce**: Non-existent email addresses
- **Complaint**: Addresses that marked emails as spam  
- **Unsubscribe**: Users who opted out
- **Block**: Manually blocked addresses

Blocked addresses receive "blacklist: XXX" error responses.

### Sending Uninterception

Override automatic blocking for specific cases:
- Add addresses or domains to bypass interception
- Useful for testing or critical communications
- Apply to individual addresses or entire domains

### Bounce Interception
*Recommended: Keep Enabled*

Automatically blocks addresses that previously bounced:
- Prevents repeated delivery attempts to invalid addresses
- Improves overall delivery rates and sender reputation
- Returns "in blacklist: bounce" for blocked addresses
- Can be disabled through Options if needed

## Configuration Recommendations

**For Marketing Emails:**
- Enable Auto AD Tag
- Use Do Not Disturb hours
- Keep bounce interception active
- Consider fixed addressing for consistency

**For Transactional Emails:**
- Use fixed Mail From addresses
- Enable TLS for sensitive content
- Configure address matching for authentication

**For All Email Types:**
- Monitor bounce rates regularly
- Review interception lists periodically
- Test delivery with various email providers