---
title: Email Template
excerpt: 'Email templates allow you to create reusable email content frameworks. '
deprecated: false
hidden: false
metadata:
  robots: index
---
They're ideal for scenarios where you need to send repetitive emails but require personalized content, such as marketing campaigns, system notifications, and verification codes. By replacing variables, you can achieve personalized email delivery with one template.



Access Portal 🔍
Log in to the SendCloud platform and select [Send Content] - [Email Templates] from the left menu to access the template management page. Template List Information 📋
On the Template List page, you can view complete information for all templates in your account:
Field Name
Description
Notes
Template Name
✏️
Template identification name
For quick identification
Type
🏷️
Template classification type
Call Name
🔤
Identifier used when making API calls
Must be unique
Email Subject
📮
Email subject line
Maximum 256 characters
Update Time
⏰
Last modified time
Automatically logged
Template Editor Introduction
🛠️
SendCloud provides two editing modes to meet different user needs:

1. ShanEdit
   🎨
   Features: Visual drag-and-drop editing, easy to use
   Target audience: Marketing and operations professionals with non-technical backgrounds
   Functions:
   Directly drag and drop text, images, and other elements
   Use a library of pre-set professional templates
   Real-time preview
   One-click copy and use of existing templates
2. Source Code Editor 💻
   Features: Directly edit HTML source code or rich text content, offering high flexibility.
   Target audience: Developers, professional users.
   Operation:
   Click the "Source" button on the right to switch modes.
   Supports direct pasting of external HTML code.
   Full code control capabilities.
   Template Usage Guidelines:
   📝
   Content Restrictions:
   🚫
   No JavaScript allowed.
   🎨 Styles and content should be concise and clear.
   📱
   Responsive Table static layout is recommended.
   ✂️
   Email subject character limit: 256 characters.
   Template Type Matching:
   📨
   Batch templates: Called by batch type API_USER
   ⚡
   Trigger templates: Called by trigger type API_USER
   🔄
   Please ensure that the template type matches the API_USER type.
   Best Practices:
   💡
   Template Design Tips:
   Use clear naming conventions to facilitate team collaboration.
   👥
   Utilize variable substitution for personalization. ✨
   Regularly optimize and update template content.
   Test the display effects on different devices. 📱💻
   Workflow:

Select the appropriate editor mode.
Design or edit the template content.
Set the template type and call name.
Save and test send.
Use the API to officially call and use.

FAQ
❓

Q: What might be causing a template call failure?

A: Please check that the template type matches the API_USER and that the call name is correct.

Q: How can I achieve responsive design?

A: We recommend using an adaptive table layout to ensure proper display on different devices.

Q: Is there a limit on the number of templates you can create?

A: This varies depending on your plan. Please refer to your plan details.

Next steps:

[Create a new email template]

[View the template usage guide]

[Test template send performance]

Need more help? Please contact our technical support team! 🎯
