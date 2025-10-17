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

Your centralized hub for managing account security, preferences, and regional settings.

## Quick Access

<Cards columns="4">
  <Card title="Security Settings" href="#security" icon="shield-alt">
    Update email, password, and 2FA settings
  </Card>
  <Card title="Personal Preferences" href="#preferences" icon="user-cog">
    Customize timezone, industry, and notifications
  </Card>
  <Card title="Regional Settings" href="#regions" icon="globe-americas">
    Manage multi-region deployments
  </Card>
  <Card title="Support" href="#help" icon="question-circle">
    Get help with account issues
  </Card>
</Cards>

---

## How to Access Settings

Click your **profile picture** (bottom-left corner) → Select **"Info"** → Choose your desired settings section.

<Tabs>
  <Tab title="🔐 Security">

<Accordion title="Email Address - Your Primary Credential" icon="at">
**Current Status:** Your email is your login username and notification endpoint.

### ✉️ Change Email Address
<Columns layout="auto">
  <Column>
    **Steps:**
    1. Click **Modify** → Verify current email (6-digit code)
    2. Enter new email → Verify new email (6-digit code)
    3. **Save** changes
  </Column>
  <Column>
    **⚠️ Important:**
    - Must be a valid email format
    - Cannot be used by another account
    - Verification codes expire in 10 minutes
    - You'll be logged out after change
  </Column>
</Columns>
</Accordion>

<Accordion title="Password - Keep Your Account Secure" icon="lock">
**Security Tip:** Change your password every 3-6 months for optimal security.

### 🔑 Password Change Options

<Columns layout="auto">
  <Column>
    **✅ I Know My Current Password**
    1. Click **Modify** next to Password
    2. Enter current password
    3. Create new secure password
    4. Confirm new password
    5. **Confirm Change**
  </Column>
  <Column>
    **🔄 I Forgot My Password**
    1. On login page → **Forgot password?**
    2. Enter registered email address
    3. Check email for verification code
    4. Set new password
    5. **Confirm Reset**
  </Column>
</Columns>

### Password Requirements Checklist
- ✅ 6-16 characters long
- ❌ No spaces allowed  
- ✅ At least 3 character types:
  - Lowercase letters (a-z)
  - Uppercase letters (A-Z)  
  - Numbers (0-9)
  - Special characters (!@#$%&*)

> **💡 Pro Tip:** Use a password manager to generate and store secure passwords.
</Accordion>

<Accordion title="Phone Number - Enhanced Security & Notifications" icon="mobile-alt">
**Benefits:** Two-factor authentication, SMS notifications, account recovery.

### 📱 First-Time Phone Setup
1. **Connect** → Select country code → Enter number
2. **SMS Verification** → Enter received code
3. **Confirm** setup

### 🔄 Change Phone Number  
1. **Modify** → Verify current number (SMS code)
2. Enter new number + country code
3. **Get Verification Code** → Enter SMS code
4. **Confirm Change**

**⚠️ Limitations:**
- One phone per account only
- Must be able to receive SMS
- International rates may apply
</Accordion>

  </Tab>

  <Tab title="⚙️ Preferences">

<Cards columns="2">
  <Card title="🌍 Time Zone" icon="clock">
    **Purpose:** Ensures all timestamps match your local time.
    
    **Setup:**
    1. Select UTC timezone from dropdown
    2. Click **Save**
    
    **Default:** UTC+8 (Eastern Time)
    
    > Affects: Reports, logs, notifications, scheduling
  </Card>

  <Card title="🏢 Industry" icon="building">
    **Purpose:** Enables industry-specific insights and recommendations.
    
    **Available Industries:**
    - E-commerce & Cross-border  
    - Gaming & Entertainment
    - HR & Training/Education
    - IT Services & Tech
    - Finance & Fintech
    - Healthcare & Biopharma
    - Sports & Arts/Literature
    - Community & Social
    - Logistics & Supply Chain
    
    **Can't find yours?** Select "Other" and specify.
  </Card>

  <Card title="📈 Discovery Channel" icon="chart-line">
    **Purpose:** Helps us improve our marketing and outreach.
    
    **How did you find us?**
    - Search Engines (Google, Bing, etc.)
    - Online Advertising
    - SAE Service Recommendation  
    - Media Coverage/Press
    - Social Media Platforms
    - Friend/Colleague Recommendation
    
    **Other sources?** Select "Other" and describe.
  </Card>

  <Card title="🔔 Notifications" icon="bell">
    **Status:** Coming Soon
    
    **Planned Features:**
    - Email notification preferences
    - SMS alert settings  
    - Push notification controls
    - Frequency preferences
    
    *Stay tuned for these customization options!*
  </Card>
</Cards>

  </Tab>

  <Tab title="🌐 Regions">

### Understanding Regions

<Accordion title="What Are Regions?" icon="info-circle">
**Definition:** Independent geographical data centers that host your services closer to your users.

**Key Characteristics:**
- 🏢 **Isolated Infrastructure:** Each region runs independently
- 💾 **Separate Data Storage:** No automatic data synchronization  
- 💰 **Independent Billing:** Costs calculated per region
- 📊 **Unique Quotas:** Resource limits apply per region
- 🚀 **Performance Benefits:** Lower latency for nearby users
</Accordion>

### Available Regions & Activation

<Cards columns="3">
  <Card title="🇸🇬 Singapore" icon="check-circle">
    **Status:** ✅ Active (Default)
    
    **Best For:**
    - Southeast Asian users
    - APAC headquarters  
    - Regional compliance needs
    
    **Activated:** Automatically upon registration
  </Card>

  <Card title="🇺🇸 US (Silicon Valley)" icon="plus-circle">
    **Status:** Available for Activation
    
    **Best For:**
    - North/South American users
    - US-based operations
    - Lower latency for Americas
    
    **To Activate:** Info → Regions → Add US Region
  </Card>

  <Card title="🇭🇰 CN (Hong Kong SAR)" icon="plus-circle">
    **Status:** Available for Activation
    
    **Best For:**
    - Greater China region users
    - China mainland proximity
    - Asian financial centers
    
    **To Activate:** Info → Regions → Add HK Region
  </Card>
</Cards>

### Region Activation Process

<Accordion title="How to Add New Regions" icon="plus">
**Steps:**
1. Navigate to **Info** → **Regions**
2. Find "Add Region" dropdown menu
3. Select desired region (US Silicon Valley or CN Hong Kong)  
4. Click **Add** button
5. **Confirm** activation in popup dialog
6. Wait for activation completion
7. Switch to new region and begin deploying services

**💰 Cost:** Free to activate, pay only for services you use in each region.

**⏱️ Time:** Usually completes within minutes.
</Accordion>

### Important Regional Considerations

> **🚨 Critical:** Resources don't transfer between regions. You must:
> - Set up services separately in each region
> - Manage data backups/sync manually if needed
> - Monitor billing for each region independently
> - Configure region-specific settings

**💡 Best Practice:** Choose your primary region based on where most of your users are located, then add additional regions as your user base grows globally.

  </Tab>
</Tabs>

## 🆘 Need Help?

<Cards columns="2">
  <Card title="Technical Support" icon="headset">
    Having trouble with account settings or region management?
    
    **Contact Options:**
    - Submit support ticket
    - Live chat (business hours)  
    - Email support team
    - Check documentation
  </Card>
  
  <Card title="Security Issues" icon="exclamation-triangle">
    Concerned about account security or suspicious activity?
    
    **Immediate Actions:**
    - Change password immediately
    - Review recent login activity
    - Contact security team
    - Enable 2FA if not already active
  </Card>
</Cards>

---

**Last Updated:** Account management features are continuously improved. Check back for new options and enhancements.