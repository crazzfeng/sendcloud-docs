---
title: How to Setup Domain on DNSPOD
excerpt: >-
  Step-by-step guide to configure DNS records on DNSPod for Aurora SendCloud.
  Learn to set up SPF, DKIM, MX, and DMARC records for optimal email delivery.
deprecated: false
hidden: false
link:
  new_tab: false
metadata:
  title: 'Complete Guide: How to Configure Your Domain on DNSPod for Aurora SendCloud'
  description: >-
    Step-by-step guide to configure DNS records on DNSPod for Aurora SendCloud.
    Learn to set up SPF, DKIM, MX, and DMARC records for optimal email delivery.
  keywords:
    - DNSPod domain setup
    - Aurora SendCloud DNS configuration
    - SPF records
    - DKIM configuration
    - MX records setup
    - DMARC policy
    - email authentication
  robots: index
---
<br />

## Overview

This guide demonstrates how to add a primary domain or subdomain in DNSPod and configure the DNS records required by Aurora SendCloud for that domain or subdomain. This guide assumes that you already have a DNSPod account.

While this guide is designed to be as helpful and comprehensive as possible, there is a small chance that you may encounter errors or issues when configuring DNS records in DNSPod. If this occurs, we recommend contacting DNSPod's support team, as they will be able to identify and resolve the issue most quickly (or at least provide next steps).

## Choosing a Primary Domain or Subdomain

Before proceeding, it's crucial to decide which domain to use—specifically, whether to use the primary domain or a subdomain of that primary domain. Because this can be a challenging decision, we recommend reviewing the following Aurora SendCloud article:

**<Anchor label="How to choose a sending domain" target="_blank" href="https://docs.aurorasendcloud.com/docs/how-to-choose-a-sending-domain#/">How to choose a sending domain</Anchor>**

Let's briefly review two key terms: primary domain and subdomain.

Examples of **primary domains** include aurorasendcloud.com, mydnsexample.com, or google.com. Examples of **subdomains** include relay.aurorasendcloud.com, sc.mydnsexample.com, or mail.google.com.

Note the pattern: Subdomains have an additional prefix (sometimes multiple prefixes) before the main domain itself. In most cases, using subdomains with Aurora SendCloud is the preferred option.

Once you've made your decision, add the domain or subdomain to your Aurora SendCloud account, and our system will generate the various DNS records required.

## Adding a Domain

There are several ways to add a domain or subdomain to DNSPod:

**Method 1:** Register a new domain/subdomain with DNSPod

**Method 2:** Transfer the registration of an existing domain or subdomain from another domain registrar to DNSPod

**Method 3:** Configure the name servers of the existing domain or subdomain at your domain registrar to reference DNSPod instead of your current DNS provider

This guide will focus on the first and third methods.

### Registering a New Domain (Method 1)

If you need to create a new domain or subdomain and have it hosted on DNSPod, follow these steps:

1. Log in to your DNSPod account
2. Click "Domain Management" or a similar option
3. Click the "Add Domain" button
4. Enter the new domain you want to add
5. Follow the prompts to complete the domain registration process

### Using an Existing Domain (Method 3)

If you already have an existing domain or subdomain registered elsewhere but would like to manage your DNS with DNSPod, follow these steps:

1. Log in to your DNSPod account
2. Add your existing domain to DNSPod's DNS management
3. DNSPod will display the specific NS records you need to use at your domain registrar
4. Update the name server records at your domain registrar to the values provided by DNSPod

## Configuring the Domain

Once the domain has been added, you can access it by following these steps:

1. Log in to your DNSPod account
2. Go to "Domain Management"
3. Find the domain you want to configure and click "Manage"
4. Click "Add Record" or a similar option to configure the DNS records

### Configuring SPF

SPF records help protect your domain from spoofed email and reduce the likelihood that your email will be marked as spam.

**Configure an SPF Record for Your Primary Domain**

In your DNSPod dashboard, enter the SPF record information displayed in the Aurora SendCloud dashboard.

| Field        | Value                                                                                                                                   |
| ------------ | --------------------------------------------------------------------------------------------------------------------------------------- |
| Record Type  | TXT                                                                                                                                     |
| Host Record  | @                                                                                                                                       |
| Record Value | v=spf1 include:sendcloud.org ~all (When activating multiple regions, please configure according to the actual requirements on the page) |
| TTL          | 600 (seconds)                                                                                                                           |

**Note:** If you already have an SPF record for this primary domain, simply insert `include:sendcloud.org` into the existing SPF record. Ensure this text appears after `v=spf1` and before `~all`.

**Configuring SPF Records for Subdomains**

| Field        | Value                                                                                                                                   |
| ------------ | --------------------------------------------------------------------------------------------------------------------------------------- |
| Record Type  | TXT                                                                                                                                     |
| Host Record  | Subdomain Prefix (e.g., sc)                                                                                                             |
| Record Value | v=spf1 include:sendcloud.org ~all (When activating multiple regions, please configure according to the actual requirements on the page) |
| TTL          | 600 (seconds)                                                                                                                           |

### Configuring DKIM

DKIM records help verify your domain to prevent forged emails and reduce the likelihood of your emails being marked as spam.

**Configure a DKIM Record for the Primary Domain**

| Field        | Value                                                                                                    |
| ------------ | -------------------------------------------------------------------------------------------------------- |
| Record Type  | TXT                                                                                                      |
| Host Record  | sendcloud._domainkey (or the value assigned by Aurora SendCloud for your domain)                         |
| Record Value | k=rsa; p=MIGfMA0GCSqGSIb3DQEBAQUA... (Please configure according to the actual requirements on the page) |
| TTL          | 600 seconds                                                                                              |

**Note:** Your DKIM host record may have one of the following values: default.domainkey, sc.domainkey, etc. Be sure to use the value assigned by Aurora SendCloud for your domain.

**Configuring a DKIM Record for a Subdomain**

| Field        | Value                                                                            |
| ------------ | -------------------------------------------------------------------------------- |
| Record Type  | TXT                                                                              |
| Host Record  | sendcloud._domainkey.subdomain prefix (e.g., sendcloud._domainkey.sc)            |
| Record Value | k=rsa; p=MIGfMA0GCSqGSIb3DQEBAQUA... (Please configure as specified on the page) |
| TTL          | 600 (seconds)                                                                    |

### Configuring MX Records

MX records specify where emails sent to your domain should be delivered.

**Configuring an MX Record for the Primary Domain**

| Field        | Value                                                                                       |
| ------------ | ------------------------------------------------------------------------------------------- |
| Record Type  | MX                                                                                          |
| Host Record  | @                                                                                           |
| Record Value | mx.sendcloud.org (Please configure as specified on the page when enabling multiple regions) |
| Priority     | 10                                                                                          |
| TTL          | 600 (seconds)                                                                               |

**Note:** Ensure that only Aurora SendCloud MX records are configured for your domain. Existing MX records for other email providers can result in unpredictable email delivery.

**Configure MX Records for Subdomains**

| Field        | Value                                                                                                         |
| ------------ | ------------------------------------------------------------------------------------------------------------- |
| Record Type  | MX                                                                                                            |
| Host Record  | Subdomain Prefix (e.g., sc)                                                                                   |
| Record Value | mx.sendcloud.org (When enabling multiple regions, please configure according to the instructions on the page) |
| Priority     | 10                                                                                                            |
| TTL          | 600 (seconds)                                                                                                 |

### Configure DMARC

DMARC (Domain-based Message Authentication, Reporting & Conformance) is an email authentication protocol used to protect your domain from spoofing and phishing attacks. It builds on SPF and DKIM to provide clear policy guidance for inbox providers.

**Configuring a DMARC Record for the Primary Domain**

| Field        | Value                                                                                                                                                                                      |
| ------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Record Type  | TXT                                                                                                                                                                                        |
| Host Record  | _dmarc                                                                                                                                                                                     |
| Record Value | v=DMARC1; p=none; rua=mailto:[dmarc-reports@yourdomain.com](mailto:dmarc-reports@yourdomain.com); ruf=mailto:[dmarc-forensics@yourdomain.com](mailto:dmarc-forensics@yourdomain.com); fo=1 |
| TTL          | 600 seconds                                                                                                                                                                                |

**Parameter Description:**

* `v=DMARC1`: Protocol version
* `p=none`: Monitor mode (no enforcement)
* `p=quarantine`: Quarantine mode (messages that fail verification will be sent to spam)
* `p=reject`: Reject mode (messages that fail verification will be rejected)
* `rua`: Email address for aggregated reports
* `ruf`: Email address for forensic reports
* `fo=1`: Failure reporting option

**Configuring a DMARC Record for a Subdomain**

| Field        | Value                                                                                            |
| ------------ | ------------------------------------------------------------------------------------------------ |
| Record Type  | TXT                                                                                              |
| Host Record  | _dmarc.Subdomain prefix (e.g., _dmarc.sc)                                                        |
| Record Value | v=DMARC1; p=none; rua=mailto:[dmarc-reports@yourdomain.com](mailto:dmarc-reports@yourdomain.com) |
| TTL          | 600 seconds                                                                                      |

### Domain Registrar and Name Server Records

If you recently migrated from another DNS hosting provider (or are currently migrating) and your Aurora SendCloud DNS records are failing to verify in the Aurora SendCloud control panel, you may need to update your domain's registration information.

Whenever anyone switches DNS hosting providers, they must update their name server (NS) records in their registrar's system. Your registrar is the company with which you purchased your domain name and registered it on the internet.

If you need help identifying your domain's registrar, the [ICANN WHOIS website](https://whois.icann.org/) can assist with this task.

## Need Support?

Our Aurora SendCloud support team is happy to help! Contact us from the Support page in your Aurora SendCloud control panel, and we'll get back to you as soon as possible!

## Important Notes

* The DNS record values in this guide are examples only. Please refer to the actual values displayed in the Aurora SendCloud dashboard.
* After configuration, it may take some time for the DNS records to propagate globally (typically several minutes to several hours).
* It is recommended to set the TTL to a low value (e.g., 300-600 seconds) for faster verification. After successful verification, you can adjust it as needed.
