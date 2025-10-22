---
title: Unsubscribe
deprecated: false
hidden: false
link:
  new_tab: false
metadata:
  robots: index
---
# Unsubscribe Settings ✋

## Feature Overview

Unsubscribe settings allow recipients to opt out of receiving emails, which is a crucial feature for maintaining sender reputation and complying with regulatory requirements. Properly configuring the unsubscribe process can effectively reduce spam complaints and improve user experience.

## Enabling Prerequisites 🔑

**The unsubscribe feature must be enabled in the tracking settings for subscription tracking to work.**

Path: [Tracking Settings] → Enable [Subscription Tracking]

If this feature is not enabled, all unsubscribe-related services will be unavailable.

## Unsubscribe Dimension Settings 🎯

SendCloud provides three ways to set the scope of unsubscribes:

| Options | Unsubscribe Scope | Applicable Scenarios |
|---------|-------------------|---------------------|
| **1. Current API_USER Only (Default)** | The unsubscribe operation only affects the current sending account. | Multiple business lines operate independently without interfering with each other. |
| **2. All API_USERS** | Unsubscribing from one account unsubscribes from all associated accounts. | Unifying your brand image prevents users from having to unsubscribe multiple times. |
| **3. Custom Rules** | Set independent unsubscribe rules for each API_USER. | Complex business scenarios that require refined operational needs. |

### Custom Rule Description

If you select option 3, you can configure unsubscribe rules for each API_USER:

- Flexibly assign unsubscribe processing methods based on business logic
- Support settings based on business type, sending frequency, and other dimensions

## Unsubscribe Link Format 🔗

### Default Style
The system automatically inserts an unsubscribe button, and the style automatically adapts to the language of the unsubscribe page.

- Conforms to international design standards
- Highly recognizable to users

### Custom Style

```html
<a href="%%user_defined_unsubscribe_link%%" style="color: #666; text-decoration: underline;">Unsubscribe from Email</a>
```

Use the `%%user_defined_unsubscribe_link%%` variable to insert the unsubscribe link.

- Fully customizable HTML and CSS styles are supported
- Can be aligned with the overall email design

## Personalize the Unsubscribe Page

### Customizable Content
🌍 **Page Language**: Supports multiple languages  
🎨 **Color Theme**: Match your brand's primary colors  
🏢 **Brand Logo**: Enhance brand recognition  
🔀 **Redirection Page**: Direct redirect after successful unsubscription

### Editing Permissions
- Standard translations are provided
- Manual editing of non-Chinese translations is supported  
- Real-time preview to ensure correct display

## Page Binding Methods ⚙️

### Method 1: API_USER Binding
Specify a default unsubscribe page for API_USER in Tracking Settings.

- Suitable for batch sending in fixed business scenarios

### Method 2: Specifying During API Call (Under Development)
Dynamically specify an unsubscribe page in a single API request.

- Priority higher than the page associated with API_USER
- Suitable for special scenarios such as temporary events

### Priority Order
🥇 Unsubscribe page specified in the API call (highest priority)  
🥈 Unsubscribe page associated with API_USER  
🥉 System default unsubscribe page

## Best Practices 💡

### Compliance Recommendations
📋 Ensure the unsubscribe link is clearly visible in emails  
⚖️ Comply with regulations such as CAN-SPAM and GDPR  
🔒 Clearly inform users about how their data is used

### User Experience Optimization
💬 Provide a user-friendly option to collect unsubscribe reasons  
🚀 Simplify the unsubscribe process and reduce the number of steps  
📱 Ensure proper display on mobile devices

### Data Analysis Applications
📊 Regularly analyze unsubscribe data and reasons  
🔍 Identify content or frequency issues  
🎯 Optimize delivery strategies based on data

## Configuration Checklist ✅

- [ ] Enable subscription tracking
- [ ] Select appropriate unsubscribe dimension rules
- [ ] Configure the unsubscribe page style and content
- [ ] Test the unsubscribe process
- [ ] Verify mobile display performance
- [ ] Check unsubscribe data statistics