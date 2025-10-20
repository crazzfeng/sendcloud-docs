---
title: Address
deprecated: false
hidden: false
link:
  new_tab: false
metadata:
  robots: index
---
This section explains how to manage your contact email addresses, with a focus on the **Address List** feature for bulk sending and the **Subscription Management** feature for collecting leads directly from your website.

## Address Lists

The Address List function is designed for **bulk email sending** scenarios, such as marketing campaigns and newsletters. It supports variable replacement, allowing you to personalize email content for different recipients within the same batch

### File Upload Support

Supports uploading address files in **.CSV**, **.TXT**, **.XLS** and **.XLSX** formats for batch import.

<Callout icon="👍">
  **Recommended CSV format:** The first column should contain email addresses, followed by columns for custom variables (e.g., %name%, %company%).
</Callout>

### List Alias

Each Address List has a unique **Alias** used in API requests to specify the recipient list and must be **globally unique**.

<Callout icon="📘" theme="info">
  **Example:** Set a list alias to `monthly_newsletter_us` and use it directly in your sending API calls.
</Callout>

### Upload Processing & Limitations

<br />

**Automatic Processing:** During upload, the system automatically performs:

<Callout icon="🚧">
  **Deduplication:** Removes duplicate email addresses

  **Format Validation:** Checks the basic validity of email address formats
</Callout>

**Capacity Limits:**

<Callout icon="❗️">
  File size for a single upload must not exceed **100MB**

  A single Address List cannot contain more than **1 million** email addresses
</Callout>

**Permission Note:** 

<Callout icon="❗️">
  The Address List feature is only available to **paying customers**.
</Callout>

## Subscription Management

The Subscription Management feature allows you to quickly and easily build an email subscription system on your website to legally collect potential leads' contact information.

### How It Works

<br />

Step 1: Get the Code

Aurora SendCloud provides you with a unique piece of **JavaScript code**

Step 2: Embed on Your Website

Copy and paste this code into the HTML of the webpage where you want the subscription form to appear (e.g., homepage footer, blog sidebar)

Step 3: Frontend Display

After embedding, an email input field will be displayed at the corresponding location on your website

Step 4: Address Collection

When a visitor enters their email address and submits the form, it is automatically collected into a specified **target Address List** within your Aurora SendCloud account

Typical Workflow Example

1. Create a new Address List in SendCloud (e.g., name it "Website Subscribers")
2. Navigate to the "Subscription Management" feature and generate a subscription code for the "Website Subscribers" list
3. Embed the generated code on your website
4. Start collecting subscriber emails and send marketing emails directly to the "Website Subscribers" list
