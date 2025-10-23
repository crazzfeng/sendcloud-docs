---
title: Domain
deprecated: false
hidden: false
link:
  new_tab: false
metadata:
  robots: index
---
## What is a Sending Domain?

Your sending domain is the cornerstone of email deliverability and serves as your email service's digital identity. It's the domain that appears in the `mail from` command during SMTP sessions and directly impacts whether your emails reach inboxes or spam folders.

**SMTP Example:**

```
mail from: notifications@yourdomain.com
250 sender notifications@yourdomain.com OK
```

In this example, `yourdomain.com` is your sending domain.

> **⚠️ Critical:** After registration, you receive a test domain automatically. **Never use this test domain for production emails.** Always configure your business domain before sending real emails.

## Why [Domain Authentication](https://www.aurorasendcloud.com/blog/guide-to-email-authentication) Matters

Proper domain authentication through DNS records is essential for:

* **Email Deliverability**: Prevents emails from being marked as spam
* **Brand Protection**: Establishes sender authenticity and credibility
* **Reputation Management**: Builds trust with email service providers
* **Compliance**: Meets modern email security standards

## Required DNS Records

Your domain configuration requires specific DNS records for authentication. **SPF, DKIM, and MX records are mandatory**, while DMARC is optional but strongly recommended.

#### [SPF ](https://en.wikipedia.org/wiki/Sender_Policy_Framework)(Sender Policy Framework)

**Purpose**: Authorizes specific IP addresses to send emails on behalf of your domain

SPF records act as a whitelist, telling receiving servers which IP addresses are permitted to send emails from your domain. This prevents spammers from spoofing your domain.

**Key Benefits:**

* Prevents domain spoofing
* Reduces spam complaints
* Improves sender reputation

#### [MX ](https://en.wikipedia.org/wiki/MX_record)(Mail Exchange)

**Purpose**: Directs incoming emails to the correct mail server

MX records tell other email systems where to deliver emails sent to your domain. Even if you only send emails (don't receive them), MX records are required for proper domain validation.

**Key Benefits:**

* Enables email routing
* Required for domain verification
* Supports email infrastructure

#### [DKIM ](https://en.wikipedia.org/wiki/DomainKeys_Identified_Mail)(DomainKeys Identified Mail)

**Purpose**: Provides cryptographic authentication for email messages

DKIM adds a digital signature to your email headers, which receiving servers can verify against your public key stored in DNS. This is especially crucial for international email delivery.

**Key Benefits:**

* Cryptographic email authentication
* Prevents email tampering
* Essential for international delivery
* Improves deliverability rates

#### [DMARC ](https://en.wikipedia.org/wiki/DMARC)(Domain-based Message Authentication, Reporting & Conformance)

**Purpose**: Provides policy instructions for handling authentication failures

DMARC builds on SPF and DKIM to give you control over how receiving servers handle emails that fail authentication. It also provides valuable reporting on your email authentication.

**Key Benefits:**

* Enhanced fraud protection
* Detailed authentication reports
* Policy control over failed authentications
* Higher inbox delivery rates

## Step-by-Step Configuration

### Step 1: Access Domain Management

1. Navigate to **Setting → Domain** in your dashboard
2. Click **Add Domain** if configuring your first business domain
3. Enter your domain name (e.g., `yourbusiness.com`)

### Step 2: Retrieve DNS Records

1. Select your domain from the list
2. Copy the provided DNS record values
3. Note down all required records: SPF, MX, DKIM, and DMARC (if applicable)

### Step 3: Configure Your DNS

1. Log into your domain registrar or DNS provider
2. Add each DNS record exactly as provided:
   * **SPF**: Add as a TXT record
   * **MX**: Add as an MX record with proper priority
   * **DKIM**: Add as a TXT record (usually with a selector subdomain)
   * **DMARC**: Add as a TXT record at `_dmarc.yourdomain.com`

### Step 4: Wait for Propagation

DNS changes typically take **10-30 minutes** to propagate globally. Some changes may take up to 24 hours.

### Step 5: Verify Configuration

Return to your domain settings and click **Verify** to check your configuration status.

### Domain Status Explained

Your domain will display one of three verification statuses:

**⚪ Unverified**

* One or more required records (SPF, DKIM, MX) are missing or incorrect
* Domain cannot be used for sending emails
* **Action Required**: Fix missing or incorrect DNS records

**🔵 Usable**

* All required records (SPF, DKIM, MX) are properly configured
* Domain can be used for sending emails
* Optional records (DMARC) may still need configuration

**🟢 Verified**

* All DNS records are properly configured and verified
* Optimal configuration for maximum deliverability
* Ready for production email sending

## Domain Strategy Best Practices

**Separate Domains by Email Type**

Configure different root domains for different email purposes:

**Transactional Domain**: `notifications.yourbusiness.com`

<Callout theme="default">
  * Account confirmations
  * Password resets
  * Order confirmations
  * System notifications
</Callout>

**Marketing Domain**: `marketing.yourbusiness.com`

<Callout theme="default">
  * Newsletters
  * Promotional campaigns
  * Bulk communications
  * Marketing automation
</Callout>

**Why Separation Matters**

* **Reputation Isolation**: Marketing issues won't affect critical transactional emails
* **Deliverability Protection**: Ensures important notifications always reach users
* **Performance Optimization**: Each domain builds its own sending reputation
* **Risk Mitigation**: Reduces impact of potential spam complaints

## Troubleshooting Common Issues

**DNS Records Not Propagating**

* **Wait Time**: Allow up to 24 hours for global propagation
* **Check Multiple Tools**: Use different DNS lookup tools to verify
* **Contact DNS Provider**: Some providers have caching delays

**Verification Failures**

* **Exact Values**: Ensure DNS records match provided values exactly
* **Record Type**: Confirm you're using the correct DNS record type
* **Subdomain Structure**: Verify DKIM and DMARC subdomain formatting

**Mixed Status Results**

* **Partial Success**: Some records verified while others failed
* **Individual Check**: Verify each DNS record type separately
* **Provider Limits**: Some DNS providers have specific formatting requirements

## Next Steps After Verification

Once your domain achieves "Verified" status:

1. **Bind to API Users**: Associate the domain with your sending applications
2. **Start Sending**: Begin production email delivery with improved deliverability
3. **Monitor Performance**: Track delivery rates and sender reputation
4. **Scale Gradually**: Increase sending volume progressively to build reputation
5. **Configure Additional Domains**: Set up separate domains for different email types

### Getting Support

If you encounter issues during domain configuration:

* Check our troubleshooting guide for common solutions
* Verify DNS records using online DNS lookup tools
* Contact support with specific error messages and domain details
* Provide screenshots of your DNS configuration for faster resolution

Remember: Proper domain configuration is crucial for email deliverability. Take time to configure it correctly rather than rushing into production.
