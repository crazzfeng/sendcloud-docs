---
title: Teammates
deprecated: false
hidden: false
link:
  new_tab: false
metadata:
  robots: index
---
# Teammates

The Teammate Management function empowers Account Owners and Administrators to build and manage their team effectively. Invite team members, assign granular permissions, and maintain secure access control while ensuring everyone has the right level of access to accomplish their work.

## Quick Access

<Cards columns={2}>
  <Card title="Access Teammate Management" icon="users">
    Click your profile picture → **Account** → **Teammates**
  </Card>
  <Card title="Account Limits" icon="info-circle">
    Paid accounts support up to **50 teammates** with full permission control
  </Card>
</Cards>

---

## Managing Teammates

<Tabs>
  <Tab title="Adding Teammates">

**Navigate to Management**  
Go to the **Teammates** page and click the **Add Teammate** button.

**Configure Team Member**  
Enter personal information including name and email address. Select the appropriate permission level and configure regional settings as permissions are isolated per region.

**Send Invitation**  
Review the configuration and click **Send Invitation** to automatically email the activation link to the new teammate.

**Teammate Activation Process**  
The new teammate receives an activation email, clicks the activation link, sets up their mobile number and password, and their account becomes active.

**💡 Pro Tips:**  
Double-check email addresses before sending invitations. Consider starting with Visitor permissions and upgrading as needed. Remember that regional permissions must be configured separately for each region.

  </Tab>
  
  <Tab title="Managing Existing Teammates">

**Edit Teammate**  
Modify personal information, adjust permission levels, update regional access settings, and change role assignments for any existing team member.

**Remove Teammate**  
Permanently revoke account access. All data access is immediately terminated and cannot be undone. The teammate must be re-invited to regain access.

**Best Practices**  
Regularly review teammate permissions, remove access promptly when team members leave, document permission changes for compliance, and use the principle of least privilege.

  </Tab>
</Tabs>

---

## Permission Levels

<Accordion title="Administrator" icon="user-shield">

**Full Account Control**  
Complete access to all features and data. Can manage other teammates and their permissions. Access to sensitive account settings and billing. Can create, modify, delete, and download all data.

**Ideal for:** Team leads, IT administrators, account managers

</Accordion>

<Accordion title="Visitor" icon="eye">

**View-Only Access**  
Browse all features and data without modification rights. Cannot create, edit, delete, or download content. Perfect for stakeholders who need visibility without editing capability.

**Ideal for:** Executives, clients, auditors, read-only stakeholders

</Accordion>

<Accordion title="Custom Permissions" icon="cogs">

**Granular Control Options**  
Create tailored permission sets by configuring access for each feature: **View** (browse and read data), **Edit** (modify existing content), and **Manage** (full control including create and delete).

**Quick-Set Templates Available:**  
**Developer** template provides code access, API management, and technical features. **Operator** template covers day-to-day operations, monitoring, and basic management. **Finance** template includes billing, usage reports, and cost-related features.

**Advanced Configuration:**  
Mix and match permissions across features, set different access levels per region, create role-based permission templates, and regularly audit and update as needed.

**Ideal for:** Specialized roles, contractors, department-specific access

</Accordion>

---

## Troubleshooting & System Messages

<Cards columns={1}>
  <Card title="Common Permission Issues" icon="exclamation-triangle">

**System Message:** "Sorry, you do not have permission to use this feature. Please contact your team administrator if needed."

**This appears when:**  
Teammate has view-only access but tries to edit, feature is completely disabled for their role, or when attempting to access admin-only functions.

**Resolution Steps:**  
**For Administrators:** Review and adjust teammate permissions in the management panel.  
**For Team Members:** Contact your administrator to request appropriate access.  
**Check Regional Settings:** Ensure permissions are set for the correct region.

  </Card>
</Cards>

### Quick Permission Diagnostic

| Issue | Likely Cause | Solution |
|-------|-------------|----------|
| Can't see a feature | Feature disabled in permissions | Enable feature access in Custom permissions |
| Can see but can't edit | View-only access assigned | Upgrade to Edit or Manage permissions |
| Works in one region but not another | Region-specific permissions | Configure permissions for each region separately |
| New teammate can't log in | Activation not completed | Resend activation email or check spam folder |

---

## Security Best Practices

<Columns layout="auto">
  <Column>

**Access Management**  
Conduct regular audits by reviewing teammate access quarterly. Remove departing team members immediately. Start with minimal permissions and expand as needed. Keep detailed records of all permission changes.

  </Column>
  <Column>

**Account Security**  
Enforce strong password policies for all team members. Ensure activation emails are from trusted addresses. Leverage region-specific permissions for enhanced data security. Use role-based templates for consistent permission assignment.

  </Column>
</Columns>

> **🔒 Security Note**: All permission changes take effect immediately. Removed teammates lose access instantly and cannot retrieve any previously accessible data.