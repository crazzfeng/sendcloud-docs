---
title: Address
deprecated: false
hidden: false
link:
  new_tab: false
metadata:
  robots: index
---
# Address Management

This section explains how to manage your contact email addresses, with a focus on the **Address List** feature for bulk sending and the **Subscription Management** feature for collecting leads directly from your website.

<Tabs>
  <Tab title="Address Lists">
    
The Address List function is designed for **bulk email sending** scenarios, such as marketing campaigns and newsletters. It supports variable replacement, allowing you to personalize email content for different recipients within the same batch.

<Cards columns={2}>
  <Card title="File Upload Support" icon="upload">
    Supports uploading address files in **.CSV** and **.TXT** formats for batch import. 
    
    **Recommended CSV format:** The first column should contain email addresses, followed by columns for custom variables (e.g., %name%, %company%).
  </Card>
  
  <Card title="List Alias" icon="tag">
    Each Address List has a unique **Alias** used in API requests to specify the recipient list and must be **globally unique**.
    
    **Example:** Set a list alias to `monthly_newsletter_us` and use it directly in your sending API calls.
  </Card>
</Cards>

<Accordion title="Upload Processing & Limitations" icon="cog">

**Automatic Processing:** During upload, the system automatically performs:

* **Deduplication:** Removes duplicate email addresses
* **Format Validation:** Checks the basic validity of email address formats

**Capacity Limits:**

* File size for a single upload must not exceed **100MB**
* A single Address List cannot contain more than **1 million** email addresses

**Permission Note:** The Address List feature is only available to **paying customers**.

</Accordion>

  </Tab>
  
  <Tab title="Subscription Management">
    
The Subscription Management feature allows you to quickly and easily build an email subscription system on your website to legally collect potential leads' contact information.

## How It Works

<Cards columns={1}>
  <Card title="Step 1: Get the Code" icon="code">
    SendCloud provides you with a unique piece of **JavaScript code**
  </Card>
  
  <Card title="Step 2: Embed on Your Website" icon="globe">
    Copy and paste this code into the HTML of the webpage where you want the subscription form to appear (e.g., homepage footer, blog sidebar)
  </Card>
  
  <Card title="Step 3: Frontend Display" icon="display">
    After embedding, an email input field will be displayed at the corresponding location on your website
  </Card>
  
  <Card title="Step 4: Address Collection" icon="envelope">
    When a visitor enters their email address and submits the form, it is automatically collected into a specified **target Address List** within your SendCloud account
  </Card>
</Cards>

<Accordion title="Typical Workflow Example" icon="list-ol">

1. Create a new Address List in SendCloud (e.g., name it "Website Subscribers")
2. Navigate to the "Subscription Management" feature and generate a subscription code for the "Website Subscribers" list
3. Embed the generated code on your website
4. Start collecting subscriber emails and send marketing emails directly to the "Website Subscribers" list

</Accordion>

  </Tab>
</Tabs>