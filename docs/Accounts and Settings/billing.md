---
title: Billing
excerpt: >-
  Aurora SendCloud provides transparent, usage-based billing for your email
  delivery needs. 
deprecated: false
hidden: false
link:
  new_tab: false
metadata:
  title: Usage-Based Email Delivery Pricing | Aurora SendCloud Billing
  description: >-
    Learn about Aurora SendCloud's transparent, usage-based billing for email
    delivery. Pay only for successful deliveries, soft bounces, and processing -
    not failed attempts. Get detailed monthly reports.
  keywords:
    - email delivery billing
    - usage-based email pricing，email service billing
  robots: index
---
This page explains how our billing system works, what you're charged for, and how to manage your payments.

## How Billing Works

We charge for email delivery based on actual delivery results, not just emails sent. This ensures you only pay for successful email processing and delivery attempts.

### Billing Cycle

* **Monthly billing**: Charges are calculated monthly based on your usage
* **Consumption tracking**: Real-time monitoring of your email delivery volume
* **Detailed reporting**: Monthly consumption reports with itemized details

### Billing Result Types

Your email charges are based on the following delivery result categories:

**Delivered**

Successfully delivered emails to the recipient's inbox. These are emails that reached their intended destination without any issues.

**Soft Bounce**

Temporary delivery failures that may be retried. Examples include:

* Mailbox temporarily full
* Server temporarily unavailable
* Message size too large

**Invalid Email**

Permanent delivery failures including:

* **Format Error**: Malformed email addresses
* **Not Exist**: Email addresses that don't exist
* **Reject**: Emails rejected by the recipient server
* **Junk Mail**: Emails marked as spam or junk

## How to understand the Billing ?


This is your central hub for viewing and analyzing costs.

**1. Selecting a Billing Period**

Use the Date ​filter at the top of the page to select the monthly cycle you wish to review.

**2. Account-Level Summary**

The main summary table now displays data aggregated for your entire account.

Columns typically include:

* Service Item:​ The type of resource or service consumed (e.g., Email, Data Flow, Dedicated IP, Data Masking, BIMI Certification ).
* Usage Quantity:​ The sum of usage for that item across all regions.
* Status:​ The status of the billing (e.g., Paid, Overdrawn).

**3. Drilling Down into Details**

To view the line-item details for a specific service across different regions:

Locate the service item in the summary table. Click the Details​ on the corresponding row. A detailed section will expand, showing a breakdown by region.

Detail columns include:

* Region:​ The specific region where resources are deployed.
* Usage:​ The consumption amount within that region.
* Deductions:​ Any applicable use deductions.
* Balance:​ The balance of your service item.

### Key Functions

**1. Downloading Billing**

You can download a comprehensive report containing all your account's billing data.

Click the Export Billings button located in the top-right corner.

**2. Managing and Paying Overdrafts**

If your account has incurred overdraft charges, you can settle it efficiently.

Click the repay overdrawn​. A payment page will open with the total amount due (already aggregated from all regions).

Follow the prompts to complete the payment using your preferred method.





## Managing Billing Information

The following information will be used to issue invoices. Please fill it in correctly. If any modifications are needed, please contact us.

* Contact Name
* Company Name
* Website
* Company Address
* Detailed Address
* Business License

### Business License Upload Requirements

Please note the following requirements when uploading your business license:

1. The text on the license must be clearly readable and match the billing information provided.
2. File size cannot exceed 2MB.
3. Only JPG, JPEG, or PNG file formats are accepted.

## FAQS

<Accordion title="When is the bill generated each month?" >
Bill generation occurs on the first day of each month after 15:00 UTC+8. You can view and download it from the console at that time.
</Accordion>

<Accordion title="Why will I receive the billing email on the 5th instead of the 1st?" >
The billing email dispatch has been moved to the 5th of the month (UTC+8) to ensure the data included is fully finalized and accurate. This change only affects the email; the invoice is available in the console on the 1st.
</Accordion>

<br />

<Accordion title="Can I still see costs for a single region?">
 Yes. Use the "Details" drill-down feature on any service in the summary table to see its cost allocation across all regions.
</Accordion>

<Accordion title="What data is included in the downloaded CSV report?">
The CSV report includes detailed line-item data visible in the Billing Details page, making it perfect for custom analysis and financial reconciliation.
</Accordion>

