---
title: Dedicated IPs
deprecated: false
hidden: false
metadata:
  robots: index
---
<br />


Aurora SendCloud's global sending pool intelligently allocates sending resources based on customer category, email type, and other factors. While offering efficient shared pool services to standard customers, brand customers receive dedicated sending IPs and exclusive sending pools. This completely eliminates the impact of shared resources and ensures complete control over email delivery performance and brand reputation. Core Values ​​✨
Exclusiveness
🛡️ Completely exclusive IP resources, eliminating interference from other users
📧 Full control over email delivery performance and reputation (domain/IP)
Higher Quotas
🚀 Enjoy higher email sending quota privileges
📈 Supports large-scale email sending needs
Better Configuration
🌟 Supports independent IP and domain name registration (ICP)
✅ Achieve better email delivery performance and inbox reach
Suitable Scenarios 🎯
Verification Emails
Increase the reach of critical emails like verification codes and security notifications
Ensure timely and accurate delivery of important information
Notification Emails
Transactional emails like order confirmations and account changes
Critical information like system alerts and status notifications
Branded Emails
Marketing communications and brand promotional emails
Scenarios requiring independent email delivery reputation
Configuration Requirements ⚙️
Required Requirements
✅ Configure at least one domain for sending emails.
✅ Complete domain SPF, DKIM, MX, and DMARC verification.
✅ Configure an A record for reverse DNS resolution.

Important Tips
⚠️ Reverse DNS resolution is crucial.

Emails sent from IPs without reverse DNS configuration are more likely to be marked as spam and may even be blacklisted by anti-spam organizations.

Once the A record is configured, the system will automatically perform reverse DNS resolution for the IP.

Best Practices
💡

Domain Configuration

Use your brand domain as your sending domain.

Ensure all verification records are configured correctly.

Regularly check verification status.

Sending Strategy

Follow a gradual warm-up strategy for sending volume.

Monitor email quality and feedback data.

Adjust your sending strategy promptly.

Maintain a high-quality email list.

Process unsubscribes and complaints promptly.

Avoid triggering spam rules.

Notes 📝
​​Service Activation​​
After configuring the dedicated IP service, we recommend starting with a low sending volume and gradually increasing it.
​​Cost Considerations​​
Dedicated IP service is charged based on the number of IPs and usage duration.
​​Technical Support​​
Provides professional technical configuration guidance, monitors email performance, and provides optimization suggestions.
​​Troubleshooting​​ 🔧
​​Common Problems​​
❓ ​​Emails are still going to spam.
✅ Check if reverse DNS resolution is working.
✅ Verify that all domain name authentication records are complete.
❓ ​​Sending volume is limited.
✅ Verify that IP pre-warming is complete.
✅ Check email quality and complaint rate.
❓ ​​Domain authentication failed.
✅ Verify that DNS records are configured correctly.
✅ Verify that domain name resolution is working.
