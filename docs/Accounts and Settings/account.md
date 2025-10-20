---
title: Account
deprecated: false
hidden: false
link:
  new_tab: false
metadata:
  robots: index
---
# Account Management

After logging in, click your profile picture in the lower left corner and select "Info" from the dropdown menu to access your account information management page.

<Tabs>
  <Tab title="Account Info">
    
This section guides you through managing your core account information, including your registered email address, login password, and associated phone number.

<Accordion title="Email Management" icon="envelope">

Your registered email address is the primary credential for your account and is used for login and receiving important system notifications.

### How to Change Your Registered Email Address

For security reasons, changing your email address requires verifying ownership of both your current and new email addresses. Please follow these steps:

1. Next to the "Email" field, click the "Modify" button.

2. **Verify your current email address:** The system will send an email with a verification code to your current registered email address. Enter the 6-digit verification code you received in the field.

3. **Enter your new email address:** Enter your desired new email address in the designated field.

4. **Verify your new email address:** Click "Next." The system will send an email with a verification code to your new email address. Enter the 6-digit verification code you received in the field.

5. Click "Save."

> **Note:** The new email address must be in the correct format (e.g., [name@example.com](mailto:name@example.com)) and must not already be associated with another account.

</Accordion>

<Accordion title="Password Management" icon="lock">

Regularly updating your password is an important part of maintaining account security.

### How to Change Your Password

**Scenario 1: You Remember Your Current Password**

1. Next to the "Password" field, click the "Modify" button.
2. Enter your current password.
3. Enter a new password that meets the requirements.
4. Re-enter your new password to confirm.
5. Click "Confirm Change."

**Scenario 2: You Forgot Your Current Password**

If you have forgotten your current password, you can reset it using your registered email address:

1. Click "Forgot password?" on the login page or password change page.
2. Enter your registered email address. A verification code will be sent to that email address.
3. Enter the correct email verification code.
4. Set and confirm your new password.
5. Click "Confirm Reset."

**New Password Requirements:**

* **Length:** 6-16 characters
* **Spaces:** No spaces allowed
* **Character Types:** Only numbers, letters, and special characters are supported. Must contain at least three of the following character types:
  > Lowercase letters (a-z)
  >
  > Uppercase letters (A-Z)
  >
  > Numbers (0-9)
  >
  > Special characters (e.g., ! @ # $ % & *)

</Accordion>

<Accordion title="Phone Number" icon="phone">

Linking your phone number enables 2FA login verification, SMS verification codes, and important system notifications, which enhances account security.

### Connect Your Phone Number

If your phone number isn't linked to your account yet, please follow these steps:

1. Next to the "Phone" field, click the "Connect" button.
2. Select the country or region code (e.g., United States +1).
3. Enter your phone number in the field.
4. Click "SMS Verification." The system will send a text message verification code to the phone number you registered.
5. Enter the received text message verification code.
6. Click "Confirm."

### Modify Phone Number

1. Next to the "Phone" field, click "Modify."
2. **Verify your original phone number:** The system will send a text message verification code to your currently registered phone number. Enter the correct verification code.
3. **Enter your new phone number:** Select a new country code and enter your new phone number.
4. Click "Get Verification Code." You will receive a text message verification code at your new phone number.
5. Enter the verification code sent to your new phone number.
6. Click "Confirm Change."

> **Note:** The new phone number cannot already be registered with another account.

</Accordion>

  </Tab>
  
  <Tab title="Preferences">
    
"Preferences" allows you to customize your account experience so that displayed information (such as time and report categories) is more relevant to your context.

<Cards columns="3">
  <Card title="Time Zone" icon="clock">
    Set your UTC time zone to ensure all time-related data displays accurately for your location.
    
    1. Click the "Time Zone" dropdown box
    2. Select your UTC time zone from the list
    3. Click "Save" to save your selection
    
    > **Note:** The system defaults to UTC+8. All time information will be displayed in this time zone if not modified.
  </Card>
  
  <Card title="Industry" icon="building">
    Select your company's primary business industry for relevant insights and customized services.
    
    **Available Options:**
    E-commerce, Community Forum, Games, Human Resources, IT Services, Sports & Health, Training & Education, Arts & Literature, Finance, Logistics, Biopharma, Cross-border E-commerce
    
    **For "Other":** A text input box will appear to manually enter your specific industry.
  </Card>
  
  <Card title="Channels" icon="bullhorn">
    Tell us how you learned about our services to help us refine our marketing strategies.
    
    **Available Options:**
    Search Engines, Advertising, SAE Service Recommendation, Media Coverage, Social Platforms, Friend Recommendation
    
    **For "Other":** A text input box will appear to manually enter how you found us.
  </Card>
</Cards>

  </Tab>
  
  <Tab title="Region Management">
    
To meet your global business needs for low latency and high availability, our services support multiple geographic regions.

<Accordion title="Understanding Regions" icon="globe">

### What is a Region?

A region is a specific geographic location where our infrastructure is located. Each region is an independently deployed site.

**Default Region**

After successfully registering your account, the Singapore Region will be automatically activated for you. You can immediately purchase and use services in this region.

**Optional Regions**

Based on your business needs, you can request the following additional regions:

- **US (Silicon Valley) Region:** Suitable for businesses with primary users in the Americas
- **CN (Hong Kong SAR) Region:** Suitable for businesses with primary users in Greater China

</Accordion>

<Accordion title="Activating New Regions" icon="plus-circle">

If you need to deploy your service to a different region, please follow these steps:

1. Go to the "Info - Regions" page.
2. In the "Add Region:" dropdown list, locate the region you want to activate
3. Click the "Add" button next to the region. You will be asked to confirm again, after which activation will begin.
4. Once activation is successful, the region will become active, and you can switch to it and begin purchasing services.

> **Note:** Activating a region is free, but you will incur charges for services deployed and used within it.

</Accordion>

<Accordion title="⚠️ Regional Independence" icon="exclamation-triangle">

Understanding the independence between regions is crucial, as it directly impacts your resources, data, and billing.

**Core Principle:** Quotas, data, and services within the same account are isolated and operate independently across regions.

This means:

**Resource and Quota Independence:**
* Each region has its own independent resource quota limits
* You will need to manage your services and resources separately in each region

**Data Isolation:**
* Data stored in one region is not automatically replicated or synchronized to other regions
* Files in one region will not be visible in other regions

**Independent Services and Billing:**
* You must purchase and configure services for each region separately
* Service packages purchased in a region are valid only in that region
* Billing is performed separately by region

### Suggestions

Please choose the most appropriate region for deployment based on the geographic location of your target users. If you serve global users, consider opening multiple regions and utilizing services like global acceleration to optimize the access experience.

</Accordion>

  </Tab>
</Tabs>