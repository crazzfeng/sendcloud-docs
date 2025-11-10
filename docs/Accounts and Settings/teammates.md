---
title: Teammates
excerpt: >-
  Allows the Account Owner or Administrators to invite team members to the
  account and assign them specific permissions.
deprecated: false
hidden: false
link:
  new_tab: false
metadata:
  title: 'Teammate Management: Add, Edit & Manage Team Permissions | Aurora SendCloud'
  description: >-
    Learn how to add, edit, and remove teammates with proper permission
    management. Comprehensive guide for account owners and administrators.
  keywords:
    - teammate management
    - team member permissions
    - user access control
    - account administration
  robots: index
---
All teammates have their own separate login credentials and security settings, while sharing access to the account's data within the boundaries of their assigned permissions.

## Adding, Editing, and Removing Teammates

### How to Add a Teammate

Account Owners and Administrators can invite new team members following these steps:

1. **Navigate to Teammate Management**
   * Click the **Add Teammate** button on the Teammates page

2. **Configure Teammate Details**
   * **Name:** Enter the teammate's full name
   * **Email:** Provide their work email address
   * **Permissions:** Select appropriate access level (see Permission Levels below)

3. **Send Invitation**
   * Click **Send Invitation** to automatically email the activation link
   * The teammate receives an email with setup instructions

4. **Teammate Activation Process**
   * Teammate clicks the activation link in their email
   * Sets up mobile number and password
   * Account becomes active immediately

<Callout icon="📋" theme="info">
  **Important Notes:**

  * Permissions can be modified anytime by Account Owners or Administrators
  * Permissions are region-specific and must be set separately for each region
  * Paid accounts support up to **50 teammates**
</Callout>

### Editing and Removing Teammates

From the teammate list, you can manage existing team members:

**To Edit a Teammate:**

* Click the **Edit** button next to their name
* Modify permissions, contact information, or role assignments
* Save changes to apply immediately

**To Remove a Teammate:**

* Click the **Remove** button next to their name
* Confirm the removal action
* Teammate loses access immediately and cannot access any account data

## Permission Levels Explained

The system provides three default roles plus custom permission options:

| Role              | Access Level                                                         | Typical Use Cases                       | Key Capabilities                                                    |
| ----------------- | -------------------------------------------------------------------- | --------------------------------------- | ------------------------------------------------------------------- |
| **Administrator** | Full permissions to manage all account data, settings, and teammates | Technical leads, senior managers        | Create, edit, delete data; manage teammates; access all features    |
| **Visitor**       | View-only access to all features                                     | Stakeholders, clients, auditors         | View dashboards and reports; no editing or downloading capabilities |
| **Custom**        | Granular permissions per feature                                     | Specialized roles based on job function | Tailored access based on specific needs                             |

### Custom Permission Examples

**Developer Role Template:**

* **API Access:** Full (Create, Read, Update, Delete)
* **Documentation:** Edit permissions
* **Analytics:** View only
* **Billing:** No access

**Finance Role Template:**

* **Billing:** Full access
* **Usage Reports:** View and download
* **API Management:** View only
* **Team Management:** No access

**Content Manager Role Template:**

* **Documentation:** Full editing rights
* **Media Library:** Upload and organize
* **API Testing:** View only
* **Account Settings:** No access

### Permission Matrix Example

Here's how different permission levels work across key features:

| Feature          | Administrator | Visitor | Custom Developer | Custom Finance |
| ---------------- | ------------- | ------- | ---------------- | -------------- |
| Create API Keys  | ✅ Yes         | ❌ No    | ✅ Yes            | ❌ No           |
| View Analytics   | ✅ Yes         | ✅ Yes   | ✅ Yes            | ✅ Yes          |
| Download Reports | ✅ Yes         | ❌ No    | ❌ No             | ✅ Yes          |
| Manage Billing   | ✅ Yes         | ❌ No    | ❌ No             | ✅ Yes          |
| Invite Teammates | ✅ Yes         | ❌ No    | ❌ No             | ❌ No           |

## Common Permission Scenarios

### Scenario 1: Insufficient Permissions

When a teammate attempts actions beyond their permission level:

**Example:** A Visitor tries to download a usage report

<Callout icon="⚠️" theme="warning">
  Sorry, you don't have permission to use this feature. If access is required, please reach out to your team administrator.
</Callout>

**Resolution:** Administrator can either:

* Grant download permissions to the user's role
* Download and share the report directly
* Upgrade the user to a role with download access

### Scenario 2: Feature Access Denied

When a teammate tries to access a completely restricted feature:

**Example:** A Developer role tries to access billing information

<Callout icon="⚠️" theme="warning">
  Sorry, you don't have permission to use this feature. If access is required, please reach out to your team administrator.
</Callout>

**Resolution:** Administrator reviews if billing access is necessary for the role or creates a custom permission set.

### Scenario 3: Regional Permission Limits

When working across multiple regions:

**Example:** A teammate has edit permissions for US region but only view access for EU region

* **US Region:** Can create and modify API documentation
* **EU Region:** Can only view existing documentation
* **Action Required:** Administrator must set EU region permissions separately if edit access is needed

## Best Practices for Teammate Management

### Security Recommendations

* **Regular Permission Audits:** Review teammate permissions quarterly
* **Principle of Least Privilege:** Grant minimum necessary access
* **Role-Based Access:** Use templates for consistency
* **Offboarding Process:** Remove access immediately when teammates leave

### Organizational Tips

* **Clear Role Definitions:** Document what each permission level can do
* **Training Documentation:** Provide role-specific guides for new teammates
* **Permission Requests:** Establish a clear process for requesting additional access
* **Backup Administrators:** Ensure multiple people have administrative access

<Callout icon="💡" theme="info">
  **Pro Tip:** Use the quick-set templates (Developer, Operator, Finance) as starting points, then customize based on your specific organizational needs.
</Callout>
