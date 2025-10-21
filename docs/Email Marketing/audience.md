---
title: Audience
excerpt: >-
  When you start marketing, you may already have an audience. You can manage
  them as a small CRM.
deprecated: false
hidden: false
link:
  new_tab: false
metadata:
  robots: index
---
## Adding Contacts to Your Audience

<Accordion title="Legal Compliance Reminder" icon="shield-alt">
  Always ensure your contacts are collected legally and comply with data protection regulations like GDPR and CAN-SPAM before adding them to your audience.
</Accordion>

### Add One Contact at a Time

Perfect for adding new contacts as they sign up or when you meet them personally.

**How to add:**

1. Navigate to your audience list
2. Click "Add Contact"
3. Fill out the contact form
4. **Email is required** - all other fields are optional
5. Save the contact

### Import Multiple Contacts

Efficiently add hundreds or thousands of contacts at once using two methods:

#### Method 1: Upload CSV File

* **Email column is mandatory**
* Each column represents a contact field (Name, Phone, etc.)
* Use proper formatting for successful import
* Download our CSV template for best results

#### Method 2: Copy and Paste

* Email is required for each contact
* Separate fields with commas (,)
* Place each contact on a new line
* Example: `john@example.com, John Doe, 555-0123`

<br />

<Cards columns="2">
  <Card title="Step 1: Handle Duplicates" icon="users">
    Choose how to manage existing contacts:

    * **Update**: Replace existing data with new information
    * **Skip**: Keep original data, ignore duplicates
  </Card>

  <Card title="Step 2: Assign Tags" icon="tags">
    Organize your imports with tags:

    * **Replace**: Swap existing tags with new ones
    * **Add**: Keep existing tags, add new ones
    * **Skip**: Maintain current tags only
  </Card>

  <Card title="Step 3: Match Fields" icon="link">
    The system auto-matches columns to contact fields. Verify and adjust the mapping to ensure accuracy.
  </Card>

  <Card title="Step 4: Review & Import" icon="check-circle">
    Double-check your settings and click "Confirm Import" to add your contacts.
  </Card>
</Cards>

***

## Organizing Your Audience

### Contact Fields

Fields store information about your subscribers and help you understand your audience better.

<Accordion title="Default Contact Fields" icon="table">
  | Field Name | Type   | Can Delete? |
  | ---------- | ------ | ----------- |
  | Email      | Email  | ❌ No        |
  | Name       | Text   | ❌ No        |
  | Phone      | Phone  | ❌ No        |
  | Gender     | Text   | ✅ Yes       |
  | Birthday   | Date   | ✅ Yes       |
  | Age        | Number | ✅ Yes       |
</Accordion>

#### Custom Fields

* Add up to **50 total fields** per audience list
* Supported types: Text, Number, Date, Birthday, Dropdown
* Reorder fields by dragging in **Manage → Fields**

**Example Contact Profile:**

```
📧 Email: anna@example.com
👤 Name: Anna Johnson  
📱 Phone: +1-555-0123
🎂 Birthday: March 1st
🎯 Interest: Japanese Cuisine, Desserts
```

### Tags

Tags are flexible labels that help you categorize contacts into meaningful groups.

<Cards columns="2">
  <Card title="Tag Benefits" icon="lightbulb">
    * Create unlimited tags
    * Apply multiple tags per contact
    * Filter audiences instantly
    * Send targeted campaigns
    * Easy bulk management
  </Card>

  <Card title="Example: Food Blog" icon="utensils">
    **Tags Created:**

    * "Dessert Lovers"
    * "Japanese Cuisine"
    * "Chinese Cuisine"
    * "Weekly Newsletter"

    **Usage:** Send dessert recipes only to "Dessert Lovers" tag
  </Card>
</Cards>

### Segments

Segments are smart, dynamic groups that automatically update based on the conditions you set.

#### How Segments Work

<Columns layout="auto">
  <Column>
    **Creating a Segment:**

    1. Name your segment descriptively
    2. Choose matching logic:
       * **All conditions** = AND logic
       * **Any condition** = OR logic
    3. Add up to 10 filter conditions
    4. Preview and save
  </Column>

  <Column>
    **Segment Conditions:**

    * Contact fields (age, gender, location)
    * Tag assignments
    * Engagement history
    * Custom field values
    * Date-based criteria
  </Column>
</Columns>

<br />

<Callout>
  #### Real-World Example

  **Goal:** Survey women aged 25-30 about product preferences

  **Segment Setup:**

  * Name: "Women 25-30 Survey Group"
  * Logic: "All conditions must match"
  * Conditions:
    * Age ≥ 25
    * Age ≤ 30
    * Gender = "Female"
    * Tag = "Active Subscriber"

  **Result:** Dynamic list that automatically includes/excludes contacts as their data changes.
</Callout>

<br />

### Tags vs. Segments: When to Use Each

<Cards columns="2">
  <Card title="Use Tags When..." icon="tag">
    * Simple categorization needed
    * Manual contact organization
    * Campaign targeting by interest
    * Quick filtering required
    * Static grouping works
  </Card>

  <Card title="Use Segments When..." icon="filter">
    * Complex filtering needed
    * Automatic updates required
    * Multiple conditions necessary
    * Behavioral targeting
    * Advanced automation workflows
  </Card>
</Cards>

***

## Best Practices

<Accordion title="Data Quality Tips" icon="star">
  * Regularly clean your audience list
  * Remove invalid email addresses
  * Keep contact information up-to-date
  * Use consistent naming for tags
  * Create meaningful segment names
</Accordion>

<Accordion title="Compliance Guidelines" icon="gavel">
  * Obtain explicit consent before adding contacts
  * Provide easy unsubscribe options
  * Respect data retention policies
  * Follow regional privacy laws (GDPR, CCPA)
  * Document consent methods
</Accordion>

Ready to start building your audience? Begin by adding your first contacts and organizing them with tags that match your marketing strategy.
