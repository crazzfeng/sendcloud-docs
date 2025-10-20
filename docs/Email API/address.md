---
title: Address
deprecated: false
hidden: false
metadata:
  robots: index
---

This section explains how to manage your contact email addresses, focusing on the ​​Address List​​ feature for bulk sending and the ​​Subscription Management​​ feature for collecting leads directly from your website.
​​Address Lists​​
The Address List function is designed for ​​bulk email sending​​ scenarios (e.g., marketing campaigns, newsletters). It supports variable replacement, allowing you to personalize email content for different recipients within the same batch.
​​Key Features & Specifications​​
​​File Upload Support​​
Supports uploading address files in ​​.CSV​​ and ​​.TXT​​ formats for batch import.
Recommended CSV format: The first column should contain email addresses, followed by columns for custom variables (e.g., %name%, %company%).
​​List Alias​​
Each Address List has a unique ​​Alias​​.
This alias is used in API requests to specify the recipient list and must be ​​globally unique​​.
​​Example:​​ You can set a list alias to monthly_newsletter_usand use it directly in your sending API calls.
​​Upload Processing & Limitations​​
​​Automatic Processing:​​ During upload, the system automatically performs:
​​Deduplication:​​ Removes duplicate email addresses.
​​Format Validation:​​ Checks the basic validity of email address formats.
​​Capacity Limits:​​
The file size for a single upload must not exceed ​​100MB​​.
A single Address List cannot contain more than ​​1 million​​ email addresses.
​​Permission Note​​
The Address List feature is only available to ​​paying customers​​.
​​Subscription Management​​
The Subscription Management feature allows you to quickly and easily build an email subscription system on your own website to legally collect potential leads' contact information.
​​How It Works​​
​​Get the Code:​​ SendCloud provides you with a unique piece of ​​JavaScript code​​.
​​Embed on Your Website:​​ Copy and paste this code into the HTML of the webpage where you want the subscription form to appear (e.g., homepage footer, blog sidebar).
​​Frontend Display:​​ After embedding, an email input field will be displayed at the corresponding location on your website.
​​Address Collection:​​ When a visitor enters their email address and submits the form, it is automatically collected into a specified ​​target Address List​​ within your SendCloud account.
​​Typical Workflow​​
Create a new Address List in SendCloud (e.g., name it "Website Subscribers").
Navigate to the "Subscription Management" feature and generate a subscription code for the "Website Subscribers" list.
Embed the generated code on your website.
Start collecting subscriber emails and send marketing emails directly to the "Website Subscribers" list.
