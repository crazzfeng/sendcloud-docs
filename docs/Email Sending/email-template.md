---
title: Email Template
excerpt: 'Email templates allow you to create reusable email content frameworks. '
deprecated: false
hidden: false
link:
  new_tab: false
metadata:
  robots: index
---
# Email Template

Email templates allow you to create reusable email content frameworks that are ideal for scenarios requiring repetitive emails with personalized content, such as marketing campaigns, system notifications, and verification codes. By using variable substitution, you can achieve personalized email delivery with a single template.

## Access Portal 🔍

Log in to the SendCloud platform and navigate to **[Send Content] - [Email Templates]** from the left menu to access the template management page.

## Template List Information 📋

On the Template List page, you can view comprehensive information for all templates in your account:

| Field Name | Description | Notes |
|------------|-------------|-------|
| **Template Name** ✏️ | Template identification name | For quick identification |
| **Type** 🏷️ | Template classification type | - |
| **Call Name** 🔤 | Identifier used when making API calls | Must be unique |
| **Email Subject** 📮 | Email subject line | Maximum 256 characters |
| **Update Time** ⏰ | Last modified time | Automatically logged |

## Template Editor Introduction 🛠️

SendCloud provides two editing modes to meet different user needs:

### 1. ShanEdit 🎨

**Features:** Visual drag-and-drop editing, easy to use  
**Target audience:** Marketing and operations professionals with non-technical backgrounds

**Functions:**
- Directly drag and drop text, images, and other elements
- Use a library of pre-designed professional templates
- Real-time preview functionality
- One-click copy and use existing templates

### 2. Source Code Editor 💻

**Features:** Direct HTML source code or rich text content editing with high flexibility  
**Target audience:** Developers and professional users

**Operation:**
- Click the "Source" button on the right to switch modes
- Supports direct pasting of external HTML code
- Full code control capabilities

## Template Usage Guidelines 📝

### Content Restrictions 🚫
- JavaScript is not allowed
- Styles and content should be concise and clear
- Responsive table static layout is recommended
- Email subject character limit: 256 characters

### Template Type Matching 📨
- **Batch templates:** Called by batch type API_USER
- **Trigger templates:** Called by trigger type API_USER
- **Important:** Ensure that the template type matches the API_USER type

## Best Practices 💡

### Template Design Tips:
- Use clear naming conventions to facilitate team collaboration 👥
- Utilize variable substitution for personalization ✨
- Regularly optimize and update template content 🔄
- Test display effects on different devices 📱💻

### Workflow:
1. Select the appropriate editor mode
2. Design or edit the template content
3. Set the template type and call name
4. Save and test send
5. Use the API to officially call and implement

## FAQ ❓

**Q: What might cause a template call failure?**  
A: Please verify that the template type matches the API_USER and that the call name is correct.

**Q: How can I achieve responsive design?**  
A: We recommend using an adaptive table layout to ensure proper display across different devices.

**Q: Is there a limit on the number of templates I can create?**  
A: This varies depending on your plan. Please refer to your plan details for specific limits.

## Next Steps

- [Create a new email template]
- [View the template usage guide]  
- [Test template send performance]

Need more help? Please contact our technical support team! 🎯