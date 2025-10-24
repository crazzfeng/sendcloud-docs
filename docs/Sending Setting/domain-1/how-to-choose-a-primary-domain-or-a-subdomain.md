---
title: How to Choose a Primary Domain or a Subdomain
deprecated: false
hidden: false
metadata:
  robots: index
---
<br />

Root Domain vs. Subdomain Selection Guide
Analysis of Key Decision Factors
Based on research into best practices from multiple email service providers, the following is a detailed analysis of choosing a root domain or subdomain:
🔴 Root Domain (APEX) Usage Scenarios

Suitable Use Cases:

Startups or new projects that haven't yet established an email system

Used solely for transactional and notification emails, not mass marketing

Strong brand consistency is required, and a simple sender address is preferred

Low email volume, manageable risk

Risks and Limitations:

DNS Conflict Risk: If the root domain is already used for corporate email (such as Google Workspace or Office 365), configuring MX records will cause existing email outages

Reputation Sharing Risk: All email activity shares the same domain reputation, and a single issue can affect the entire domain

Low Flexibility: Inability to isolate and manage different types of email
🟢 Recommended Subdomain Solutions

Advantages:

Risk Isolation: Subdomains have independent email reputations from the root domain

Business Isolation: Subdomains can be created based on specific usage

marketing. Marketing Emails
transactions → Transaction Notifications
alerts → System Alerts
Flexible Configuration: Does not impact existing root domain email services
Test-Friendly: New projects can be tested with domains without impacting the primary brand
Industry Best Practices:
Root Domain: company.com → Internal Corporate Communications
Subdomain: send.company.com → Email Delivery
Subdomain: news.company.com → Newsletters
Decision Flowchart
Decision Path 1: Existing Email System Check
Is the root domain currently configured with MX records?
├── Yes → Force the use of a subdomain
└── No → Proceed to the next decision point
Decision Path 2: Email Type Analysis
What types of emails are primarily sent?
├── Transactional Emails (Registrations, Orders) → Consider the root domain
├── Marketing Emails (Promotions, News) → Recommended subdomains
└── Mixed Types → Strongly Recommend the use of subdomains
Decision Path 3: Sending Scale Assessment
What is the expected average daily send volume?
├── \< 10,000 emails → Either the root domain or a subdomain is acceptable
├── 10,000-100,000 emails → Subdomains are recommended
└── > 100,000 emails → Subdomains are required
Technical Implementation Recommendations
Subdomain Naming Conventions
​​Recommended format:​​

send.[root domain] - General sending subdomain

news.[root domain] - For newsletters only

notify.[root domain] - For system notifications only
​​Avoid names:​​

mail.[root domain] - May conflict with corporate email

smtp.[root domain] - Has a strong technical connotation

admin.[root domain] - Has a higher security risk
Hybrid Strategy Recommendations

For mature enterprises, a tiered strategy is recommended:

Root domain: company.com
├── Reserved for corporate email (Google Workspace/Office 365)

├── send.company.com → Aurora SendCloud sending service

├── news.company.com → For marketing emails only

└── alerts.company.com → System Monitoring Alerts
Real Case Study
Case 1: E-commerce Platform
Root Domain: store.com → Corporate Email and Official Website
Subdomain: mail.store.com → Order Confirmation and Shipping Notifications
Subdomain: promo.store.com → Promotional Emails
Result: Increased Complaint Rate for Marketing Emails Does Not Affect Transactional Email Delivery
Case 2: SaaS Service Provider
Root Domain: service.com → Reserved for Corporate Communications
Subdomain: notify.service.com → Product Notification Emails
Subdomain: news.service.com → Product Updates and News
Result: Clear Email Categories, Users Can Subscribe on Demand
Summary and Recommendations
Scenarios When Preferring Subdomains:
Company Has an Established Email System
Sending Marketing or Bulk Emails
Needing to Test and Optimize Sending Strategies
Focusing on Email Reputation Management
Scenarios Where Root Domains May Be Considered:
New Project with No Legacy
Sending Only Important Transactional Emails
Pursuing a Minimalistic Brand Presentation
Small and Controllable Sending Volume
Best Practices: Regardless of which solution you choose, it is recommended to always start with a subdomain and then evaluate whether to use the root domain based on actual needs after your sending reputation stabilizes.