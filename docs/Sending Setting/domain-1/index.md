---
title: Domain
deprecated: false
hidden: false
metadata:
  robots: index
---
<br />

Domain
The sending domain name is the "ID card" when sending e-mail. Each account must have a sending domain name. During the SMTP session, it is the suffix of mail from

mail from:  test@liubida.cn
250 sender  test@liubida.cn  OK

Copied!

As shown above_ liubida.cn_ This is the domain name of this email.

After successful registration of sendcloud account, the system will automatically assign a test sending domain name. Before formal use, please be sure to create the domain name used by the real business, do not use the test domain name provided by the system to send the real business.

Sending domain configure



The configuration of sending domain name includes SPF, dkim, MX and dmarc. Among them, SPF, dkim and MX are required, dmarc is optional.

SPF [wiki explanation]( [http://zh.wikipedia.org/wiki/Sender](http://zh.wikipedia.org/wiki/Sender)_ Policy_ Framework )

SPF is a DNS record type proposed to prevent spam, which is used to register all IP addresses of outgoing mail owned by a domain name.

MX

MX is a mail exchange record, which points to a mail server. It is used to locate the mail server according to the address suffix of the recipient when the e-mail system sends mail

DKIM wiki explanation(opens new window)

Dkim is an important technical means to prevent fraudulent e-mail. Usually, the sender will insert dkim signature and electronic signature information into the header of e-mail, while the receiver will get the public key through DNS query and then verify it. It is recommended to configure, especially for users with more foreign domains

DMARC

The main purpose of "dmarc" protocol is to identify and intercept fraudulent mail. After the configuration is passed, the platform will use the current domain name as the domain name suffix of from to deliver the mail. So as to reduce the interception of mail service providers, improve the credibility of mail, improve the rate of box.

Select Setting - domain to enter the sending domain configuration interface. If there is no official domain , you can add a new mail domain
Click the domain to be configured to enter the configuration interface. According to the data given by the system, do the relevant configuration in your domain management system
There are three states after domain configuration:

Unverified: any one of the required items (SPF, dkim and MX) failed (Thus domain cannot bind API_ USER)
Usable : all the three required items have passed the verification, and the optional items have not passed the verification.
Verified : all configuration items have been verified.
After all records are configured, it may take 10-30 minutes for the DNS to take effect

You need to set different domains (domains with different primary domains) for trigger mail and bulk mail, so as to avoid sharing one sending domain , which will restrict both types of mail and prevent trigger mail from being delivered in time
