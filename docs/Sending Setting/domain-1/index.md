---
title: Domain
deprecated: false
hidden: false
link:
  new_tab: false
metadata:
  robots: index
---
## What is the Sending Domain?

The sending domain is the fundamental identity of your email delivery service. Properly configuring [domain authentication](https://www.aurorasendcloud.com/blog/guide-to-email-authentication) (including SPF, DKIM,MX, and DMARC records) is crucial for ensuring your emails reach inboxes (and not spam). It also helps build brand credibility and improve email deliverability.

Each account must have a configured sending domain name, which appears as the suffix in the SMTP session's `mail from` command.

**Example:**

```
mail from: test@liubida.cn
250 sender test@liubida.cn OK
```

In this example, `liubida.cn` is the sending domain name.

> **Important:** After successful registration, the system automatically assigns a test sending domain . Before production use, you must create and configure your actual business domain. Do not use the system-provided test domain for real business operations.

## Required DNS Records

The sending domain configuration includes several DNS records. **SPF, DKIM, and MX are required**, while DMARC is optional but recommended.

### [SPF ](https://en.wikipedia.org/wiki/Sender_Policy_Framework)(Sender Policy Framework)

SPF is a DNS record type designed to prevent spam by registering all authorized IP addresses that can send email for a domain name.

### [MX](https://en.wikipedia.org/wiki/MX_record) (Mail Exchange)

MX records point to mail servers and are used by email systems to locate the appropriate mail server based on the recipient's domain suffix.

### [ DKIM](https://en.wikipedia.org/wiki/DomainKeys_Identified_Mail) (DomainKeys Identified Mail)

DKIM is a crucial technology for preventing fraudulent emails. Senders insert DKIM signatures and electronic signature information into email headers, while receivers verify authenticity by querying the public key through DNS. This is especially recommended for users sending to international domains.

### [DMARC ](https://en.wikipedia.org/wiki/DMARC)(Domain-based Message Authentication, Reporting & Conformance)

DMARC protocol helps identify and intercept fraudulent emails. Once configured and verified, the platform uses the current domain as the "from" domain suffix for email delivery, reducing interception by email service providers and improving email credibility and inbox delivery rates.

## Configuration Process

1. **Access Domain Settings**
   * Navigate to **Settings > Domain** to enter the domain configuration interface
   * If you don't have an official domain, click to add a new mail domain

2. **Configure DNS Records**
   * Click on the domain you want to configure
   * Use the system-provided data to configure the relevant DNS records in your domain management system

3. **Verification Status**
   After configuration, your domain will show one of three statuses:

   * **Unverified**: One or more required items (SPF, DKIM, MX) failed verification. Domain cannot be bound to API_USER.
   * **Usable**: All three required items passed verification, but optional items haven't been verified yet.
   * **Verified**: All configuration items have been successfully verified.

> **Note:** After configuring DNS records, it may take 10-30 minutes for DNS changes to propagate and take effect.

## Best Practices

**Separate Domains for Different Email Types**

You should configure different domains (with different root domains) for:

* **Transactional emails** (triggered emails)
* **Bulk marketing emails**

This separation prevents both email types from sharing the same sending reputation, ensuring that transactional emails can be delivered promptly without being affected by bulk email performance.

## Next Steps

Once your domain is verified, you can:

* Bind the domain to your API users
* Begin sending emails with improved deliverability
* Monitor your domain's sending reputation
* Configure additional domains as needed for different email types
