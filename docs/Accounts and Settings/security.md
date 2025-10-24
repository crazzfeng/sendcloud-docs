---
title: Security
deprecated: false
hidden: false
link:
  new_tab: false
metadata:
  robots: index
---
Protect your account with our comprehensive security features. We offer multiple verification methods and security controls to keep your data safe.

# Authentication Methods

We provide four security verification methods to protect your account:

<Cards columns="2">
  <Card title="Login Password">
    Your primary account password for authentication
  </Card>

  <Card title="Email Verification">
    Verification codes sent to your registered email address
  </Card>

  <Card title="Mobile Phone">
    SMS verification codes sent to your bound mobile number
  </Card>

  <Card title="Google Authenticator">
    Time-based one-time passwords (TOTP) via Google Authenticator
  </Card>
</Cards>

# Authentication Priority

The system automatically selects the most secure available authentication method:

## Authentication Flow

**Priority 1: Google Authentication Enabled**

* Login password + Google verification code

**Priority 2: Mobile Phone Bound (No Google Auth)**

* Login password + Mobile phone verification code

**Priority 3: Default Method**

* Login password + Email verification code

# Security Features

## Two-Factor Authentication (2FA)

Enable two-factor authentication to add an extra layer of security to your account login process.

**How it works:**

* After entering your password, you'll be prompted for a second form of authentication
* The second factor is determined by your highest priority authentication method
* This significantly reduces the risk of unauthorized account access

**Status:** Toggle the 2FA switch to enable or disable this feature.

## Data Privacy

Automatically pixelate sensitive data to protect privacy during screen sharing or demonstrations.

**Features:**

* Masks sensitive information with pixelated overlay
* Protects account numbers, personal details, and confidential data
* Can be toggled on/off based on your needs

**Usage:** Enable this setting when presenting or sharing your screen to maintain data confidentiality.

## Export Security

Add an additional security layer when exporting data from your account.

**Protection Level:**

* Requires verification before allowing data exports
* Uses your configured authentication method
* Prevents unauthorized data extraction

**Verification Process:** When enabled, you'll need to complete verification using your primary authentication method before any export operation.

# Security Best Practices

> **Recommendation:** For maximum security, we recommend enabling Google Authentication along with 2FA login protection.

### Setup Guide

1. **Enable Google Authentication** for the strongest security
2. **Turn on 2FA Login** to protect account access
3. **Enable Export Verification** to secure data exports
4. **Use Pixelation** when sharing screens or presenting

### Security Tips

* Regularly update your login password
* Keep your mobile number and email address current
* Don't share verification codes with anyone
* Log out from shared or public devices
