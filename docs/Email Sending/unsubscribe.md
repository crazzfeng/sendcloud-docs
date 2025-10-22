---
title: Unsubscribe
deprecated: false
hidden: false
link:
  new_tab: false
metadata:
  robots: index
---
Email unsubscribe settings allow recipients to opt out of receiving emails, which is a crucial feature for maintaining sender reputation and complying with regulatory requirements. Properly configuring the unsubscribe process can effectively reduce spam complaints and improve user experience.

## Prerequisites for Email Subscription Tracking 

**The unsubscribe feature must be enabled in the tracking settings for subscription tracking to work.**

Path: [Tracking Settings] → Enable [Subscription Tracking]

If this feature is not enabled, all unsubscribe-related services will be unavailable.

## Email Unsubscribe Scope Settings & Configuration 

SendCloud provides three ways to set the scope of unsubscribes:

| Option                                 | Unsubscribe Scope                                                               | Applicable Scenarios                                                                   |
| -------------------------------------- | ------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------- |
| **1. Current API_USER Only (Default)** | The unsubscribe operation only affects the current sending account.             | Multiple business lines operate independently without interfering with each other.     |
| **2. All API_USERS**                   | Unsubscribing from one account unsubscribes users from all associated accounts. | Unifies your brand image and prevents users from having to unsubscribe multiple times. |
| **3. Custom Rules**                    | Set independent unsubscribe rules for each API_USER.                            | Complex business scenarios that require refined operational control.                   |

### Custom Email Unsubscribe Rule Configuration

If you select option 3, you can configure unsubscribe rules for each API_USER:

* Flexibly assign unsubscribe processing methods based on business logic
* Support settings based on business type, sending frequency, and other dimensions

## Email Unsubscribe Link Format & Styling 

### Default Unsubscribe Link Style

The system automatically inserts an unsubscribe button, and the style automatically adapts to the language of the unsubscribe page.

* Conforms to international design standards
* Highly recognizable to users

### Custom Unsubscribe Link Style

```html
<p>
  If you want to unsubscribe , click   
  <a href="%%user_defined_unsubscribe_link%%" >  
   here  
  </a>  
<p>
```

Use the `%%user_defined_unsubscribe_link%%` variable to insert the unsubscribe link.

* Fully customizable HTML and CSS styles are supported
* Can be aligned with your overall email design

## Email Unsubscribe Page Customization

### Customizable Unsubscribe Page Content

 **Page Language**: Supports multiple languages  
 **Color Theme**: Match your brand's primary colors  
 **Brand Logo**: Enhance brand recognition  
 **Redirect Page**: Direct users to a specific page after successful unsubscription

### Unsubscribe Page Editing Permissions

* Standard translations are provided
* Manual editing of non-English translations is supported
* Real-time preview ensures correct display

## Email Unsubscribe Page Binding Methods 

### Method 1: API_USER Email Unsubscribe Binding

Specify a default unsubscribe page for API_USER in Tracking Settings.

* Suitable for batch sending in fixed business scenarios

### Method 2: Dynamic Email Unsubscribe Page Specification (Under Development)

Dynamically specify an unsubscribe page in a single API request.

* Takes priority over the page associated with API_USER
* Suitable for special scenarios such as temporary events

### Email Unsubscribe Page Priority Order

1. Unsubscribe page specified in the API call (highest priority)  
2. Unsubscribe page associated with API_USER  
3. System default unsubscribe page

## Email Marketing Best Practices for Unsubscribe Management 

### Email Compliance & Regulatory Requirements

📋 Ensure the unsubscribe link is clearly visible in emails  
⚖️ Comply with regulations such as CAN-SPAM and GDPR  
🔒 Clearly inform users about how their data is used

### Email Unsubscribe User Experience Optimization

💬 Provide a user-friendly option to collect unsubscribe reasons  
🚀 Simplify the unsubscribe process and reduce the number of steps  
📱 Ensure proper display on mobile devices

### Email Unsubscribe Data Analysis & Optimization

📊 Regularly analyze unsubscribe data and reasons  
🔍 Identify content or frequency issues  
🎯 Optimize delivery strategies based on insights

## Email Unsubscribe Configuration Checklist ✅

* [ ] Enable subscription tracking
* [ ] Select appropriate unsubscribe scope rules
* [ ] Configure the unsubscribe page style and content
* [ ] Test the unsubscribe process
* [ ] Verify mobile display performance
* [ ] Check unsubscribe data statistics
