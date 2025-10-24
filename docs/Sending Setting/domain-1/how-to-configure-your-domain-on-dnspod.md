---
title: How to Setup Domain on DNSPOD
deprecated: false
hidden: false
metadata:
  robots: index
---
<br />

Overview
This guide demonstrates how to add a root domain or subdomain in DNSPod and configure the DNS records required by Aurora SendCloud for that (sub)domain. This guide assumes that you have already created a DNSPod account.
While this guide is designed to be as helpful and comprehensive as possible, there is a small chance that you may encounter errors or issues when configuring DNS records in DNSPod. If this occurs, we recommend contacting DNSPod's support team, as they will be able to identify and resolve the issue most quickly (or at least provide next steps).
Choosing a Root Domain or Subdomain
Before proceeding, deciding which domain to use—specifically, whether to use the root domain or a subdomain of that root domain—is crucial. Because this can be a challenging decision, we recommend reviewing the following Aurora SendCloud article:
Root Domain vs. Subdomain Selection Guide?
Let's briefly review two key terms: root domain and subdomain.
Examples of root domains include sendcloud.com, mydnsexample.com, or google.com. Examples of subdomains include relay.sendcloud.com, sc.mydnsexample.com, or mail.google.com.
Note the pattern: Subdomains have an additional prefix (sometimes multiple prefixes) before the main domain itself. In most cases, using subdomains with Aurora SendCloud is the preferred option.
Finally, once you've made your decision, add the (sub)domain to your Aurora SendCloud account, and our system will generate the various DNS records required.
Adding a Domain
There are several ways to add a domain or subdomain to DNSPod:

Method 1: Register a new domain/subdomain with DNSPod

Method 2: Transfer the registration of an existing (sub)domain from another domain registrar to DNSPod

Method 3: Configure the name servers of the existing (sub)domain at your domain registrar to reference DNSPod instead of your current DNS provider.
This guide will focus on the first method. Registering a New Domain (Method 1)
If you need to create a new (sub)domain and have it hosted on DNSPod, follow these steps to register a new domain (or subdomain) with DNSPod:
Log in to your DNSPod account
Click "Domain Management" or a similar option
Click the "Add Domain" button
Enter the new domain you want to add
Follow the prompts to complete the domain registration process
Using an Existing Domain (Method 3)
If you already have an existing (sub)domain registered elsewhere but would like to manage your DNS with DNSPod, you can do so by following these steps:
Log in to your DNSPod account
Add your existing domain to DNSPod's DNS management
DNSPod will display the specific NS records you need to use at your domain registrar
Update the name server records at your domain registrar to the values ​​provided by DNSPod
Configuring the Domain
Once the domain has been added, you can access it by following these steps:
Log in to your DNSPod account
Go to "Domain Management"
Find the domain you want to configure and click "Manage"
Click "Add Record" or a similar option to configure the DNS records
Configuring SPF
SPF Records help protect your domain from spoofed email and reduce the likelihood that your email will be marked as spam.
Configure an SPF record for your root domain
In your DNSPod dashboard, enter the SPF record information displayed in the Aurora SendCloud dashboard.
Field
Value
Record Type
TXT
Host Record
@
Record Value
v=spf1 include:sendcloud.org ~all (When activating multiple regions, please configure according to the actual requirements on the page)
TTL
600 (seconds)
Note:
If you already have an SPF record for this root domain, simply insert include:sendcloud.org into the existing SPF record.
Ensure this text appears after v=spf1 and before ~all
Configuring SPF Records for Subdomains
Field
Value
Record Type
TXT
Host Record
Subdomain Prefix (e.g., sc)
Record Value
v=spf1 include:sendcloud.org ~all (When activating multiple regions, please configure according to the actual requirements on the page)
TTL
600 (seconds)
Configuring DKIM
DKIM records help verify your domain to prevent forged emails and reduce the likelihood of your emails being marked as spam. Configure a DKIM record for the root domain.
Field
Value
Record Type
TXT
Host Record
sendcloud._domainkey (or the value assigned by Aurora SendCloud for your domain)
Record Value
k=rsa; p=MIGfMA0GCSqGSIb3DQEBAQUA... (Please configure according to the actual requirements on the page)
TTL
600 seconds
Note: Your DKIM host record may have one of the following values: default.domainkey, sc.domainkey, etc. Be sure to use the value assigned by Aurora SendCloud for your domain. Configuring a DKIM Record for a Subdomain
Field
Value
Record Type
TXT
Host Record
sendcloud.domainkey.subdomain prefix (e.g., sendcloud.domainkey.sc)
Record Value
k=rsa; p=MIGfMA0GCSqGSIb3DQEBAQUA... (Please configure as specified on the page)
TTL
600 (seconds)
Configuring MX Records
MX records describe where emails sent to your domain should be sent.
Configuring an MX Record for the Root Domain
Field
Value
Record Type
MX
Host Record
@
Record Value
mx.sendcloud.org (Please configure as specified on the page when enabling multiple regions)
Priority
10
TTL
600 (seconds)
Note: Ensure that only Aurora SendCloud MX records are configured for your domain. Existing MX records for other email providers can result in unpredictable email delivery.
Configure MX records for subdomains
Field
Value
Record Type
MX
Host Record
Subdomain Prefix (e.g., sc)
Record Value
mx.sendcloud.org (When enabling multiple regions, please configure according to the instructions on the page)
Priority
10
TTL
600 (seconds)
Configure DMARC
DMARC (Domain-based Message Authentication, Reporting & Conformance) is an email authentication protocol used to protect your domain from spoofing and phishing attacks. It builds on SPF and DKIM to provide clear policy guidance for inbox providers. Configuring a DMARC Record for the Root Domain
Field Value
Record Type: TXT
Host Record: _dmarc
Record Value: v=DMARC1; p=none; rua=mailto:[dmarc-reports@yourdomain.com](mailto:dmarc-reports@yourdomain.com); ruf=mailto:[dmarc-forensics@yourdomain.com](mailto:dmarc-forensics@yourdomain.com); fo=1
TTL: 600 seconds
Parameter Description:

v=DMARC1: Protocol version
p=none: Monitor mode (no enforcement)
p=quarantine: Quarantine mode (messages that fail verification will be sent to spam)
p=reject: Reject mode (messages that fail verification will be rejected)
rua: Email address for aggregated reports
ruf: Email address for forensic reports
fo=1: Failure reporting option
Configuring a DMARC Record for a Subdomain
Field Value
Record Type: TXT
Host Record: _dmarc.Subdomain prefix (e.g., _dmarc.sc)
Record Value v=DMARC1; p=none; rua=mailto:[dmarc-reports@yourdomain.com](mailto:dmarc-reports@yourdomain.com)
TTL 600 seconds

Domain Registrar and Name Server Records
If you recently migrated from another DNS hosting provider (or are currently migrating) and your Aurora SendCloud DNS records are failing to verify in the Aurora SendCloud control panel, you may need to update your domain's registration information.
Whenever anyone switches DNS hosting providers, they must update their name server (NS) records in their registrar's system. Your registrar is the company with which you purchased your domain name and registered it on the internet.
If you need help identifying your domain's registrar, the ICANN WHOIS website can assist with this task.
Need support?
Our Aurora SendCloud support team is happy to help! Contact us from the Support page in your Aurora SendCloud control panel, and we'll get back to you as soon as possible!
Important Note:

The DNS record values ​​in this guide are examples only. Please refer to the actual values ​​displayed in the Aurora SendCloud dashboard.

After configuration, it may take some time for the DNS record to propagate globally (typically several minutes to several hours).

It is recommended to set the TTL to a low value (e.g., 300-600 seconds) for faster verification. After successful verification, you can adjust it as needed.
