---
title: Email Template
excerpt: 'Email templates allow you to create reusable email content frameworks. '
deprecated: false
hidden: false
link:
  new_tab: false
metadata:
  title: Email Templates - Aurora SendCloud Platform Guide
  description: >-
    Create reusable email templates with Aurora SendCloud. Use visual or code
    editors for marketing campaigns, notifications, and personalized content
    delivery.
  robots: index
---
# Email Template

Email templates allow you to create reusable email content frameworks that are ideal for scenarios requiring repetitive emails with personalized content, such as marketing campaigns, system notifications, and verification codes. By using variable substitution, you can achieve personalized email delivery with a single template.

To access the template management page, log in to the Aurora SendCloud platform and navigate to **Content > Email Template** from the left menu.

## Template List

The Template List page displays comprehensive information for all templates in your account:

* **Template Name** - Template identification name for quick identification
* **Type** - Template classification type
* **Invoke Name** - Unique identifier used when making API calls
* **Email Subject** - Email subject line (maximum 256 characters)
* **Update Time** - Last modified time (automatically logged)

## Template Editors

Aurora SendCloud provides two editing modes to meet different user needs:

<Tabs>
  <Tab title="ShanEdit(Visual Editor)">
    * Features: Visual drag-and-drop editing, easy to use
    * Target audience: Marketing and operations professionals with non-technical backgrounds
    * Functions:
      * Directly drag and drop text, images, and other elements
      * Use a library of pre-designed professional templates
      * Real-time preview functionality
      * One-click copy and use existing templates
  </Tab>

  <Tab title="Source Code Editor">
    * Features: Direct HTML source code or rich text content editing with high flexibility
    * Target audience: Developers and professional users
    * Operation:
      * Click the "Source" button on the right to switch modes
      * Supports direct pasting of external HTML code
      * Full code control capabilities
  </Tab>
</Tabs>

## How to create and send an email template?

This section will demonstrate how to create and send an email template using a fashion brand launching a new product.

Example : Creating a "New Product Launch Announcement" Template

The goal of this email is to introduce the new product line to subscribers, create anticipation, and directly drive sales.

### Creating a New Template

1.Log in to Aurora SendCloud and go to "Content" - "Email".

2.Click "Template Create" and choose a template editing method, such as Flash Editor.

3.Set the basic template information:

* Template Name: New Product Launch Announcement
* Invoke Name: New_product_launch
* Email Type: Batch Email
* Email Subject (to attract openes): New Product Launch | %product_name% Series, Now Available!

4.Design Template Content

Select from the template library or create a new template directly.

* Template library: Replace product images and modify product description text.
* Create a new template: Drag and drop components, upload product images, and modify product description text.

If you want to add variables (such as user names) to the template, please use %% to enclose your variable name. For example: %name%

Don't forget to add preview text. For example: Explore exquisite products and start a minimalist new experience...

5.Save Template

Preview the effect (especially on mobile devices), ensure all modules display correctly, and then click "Save".

### How to Use This Template to Launch a New Product Launch Campaign

1.Log in to Aurora SendCloud and go to "Marketing" - "Campaign".

2.Click "Create Campaign" and set the campaign information.

* Send Content, Select Template: New Product Launch Announcement
* Select Target Audience: Choose the email list to send to, such as "All Subscribers" or a more granular segmentation list.

Fill in Content and Variables: The system will load the template and replace the variables in the email template with the corresponding variable values ​​from the contact attributes.

3.Test and Send

Be sure to send a test email: Send it to your own email address to check that all links (especially purchase links and discount codes) are correct.

Set Send Time: Choose to send it during the time when your target users are most active (such as a weekday afternoon).

Click "Save".

## Usage Guidelines

### Content Restrictions

* JavaScript is not allowed
* Styles and content should be concise and clear
* Responsive table static layout is recommended
* Email subject character limit: 256 characters

### Template Type Matching

* **Batch templates:** Called by batch type API_USER
* **Trigger templates:** Called by trigger type API_USER
* **Important:** Ensure that the template type matches the API_USER type

## Best Practices

### Template Design Tips

* Use clear naming conventions to facilitate team collaboration
* Utilize variable substitution for personalization
* Regularly optimize and update template content
* Test display effects on different devices

### Recommended Workflow

1. Select the appropriate editor mode
2. Design or edit the template content
3. Set the template type and invoke name
4. Save and test send
5. Use the API to officially call and implement

## Frequently Asked Questions

**What might cause a template call failure?**
Please verify that the template type matches the API_USER and that the invoke name is correct.

**How can I achieve responsive design?**
We recommend using an adaptive table layout to ensure proper display across different devices.

**Is there a limit on the number of templates I can create?**
This varies depending on your plan. Please refer to your plan details for specific limits.

## Getting Started

Ready to create your first template? Choose your preferred editor mode and start building personalized email content that engages your audience effectively.

<br />
