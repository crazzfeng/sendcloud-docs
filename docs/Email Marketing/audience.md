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
## Adding Contacts to Your Audience List

Whether adding contacts individually or in bulk, please ensure that your contacts are collected legally and in compliance with data protection regulations. There are two ways to add contacts to your audience:

### Add Individual Contacts

You can add contacts one by one by filling out a contact form. The **Email field is required**, while all other fields are optional.

### Import Multiple Contacts

#### 1. Choose the method to add multiple contacts

**Upload CSV File**

* Email is a required field in your CSV file
* Each column represents a different contact field
* Ensure proper formatting for successful import

**Copy and Paste**

* Email is required for each contact
* Separate fields with commas (,)
* Place each contact on a new line

**Handling Duplicate Contacts**

When importing contacts that already exist in your list, you can choose how to handle duplicates:

* **Update**: Automatically replace existing contact information with new data from your import
* **Skip**: Keep existing contact information unchanged and skip duplicate entries

#### 2. Choose Tags

If you want to add tags to multiple contacts, you can select one or more tags.

**Handling Tags**

* **Replace**: If the imported contact is already in your contact list, we will automatically replace the existing contact's tag with your newly selected tag.
* **Add**: If the imported contact is already in your contact list, we will automatically add your newly selected tag while keeping the existing tags.
* **Skip**: If the imported contact is already in your contact list, we will automatically skip the new tag and only keep the existing tags.

#### 3. Contact Field Matching

The system will recognize each column of the contacts you have imported and automatically match some fields. You only need to verify that they are correct and adjust the matching to the appropriate field.

#### 4. Final Check and Confirm Import

Review your import settings and confirm to complete the process.

<br />

## Managing Your Audience

### Fields

Fields help you identify and categorize your subscribers' characteristics.

**Example:**
Anna's profile might include:

* **Email**: [Anna@example.com](mailto:Anna@example.com)
* **Name**: Anna
* **Gender**: Female
* **Birthday**: 03/01

#### Default Contact Fields

Aurora SendCloud provides these default fields:

| Field Name | Field Type |
| ---------- | ---------- |
| Email      | Email      |
| Name       | Name       |
| Phone      | Phone      |
| Gender     | Text       |
| Birthday   | Birthday   |
| Age        | Number     |

**Important Notes:**

* Email, Name, and Phone fields cannot be deleted or hidden
* You can add or remove custom fields as needed
* When creating new fields, define the attribute name and select the appropriate type
* Supported field types: Text, Number, Date, Birthday, Dropdown
* Maximum of **50 fields** per list

**Customizing Field Order**
To adjust the display order of contact fields, go to **Manage → Fields** and drag fields to reorder them.

### Tags

Tags are labels you can assign to categorize contacts into groups. They consist of text strings and help you organize your audience for targeted campaigns.

**Key Features:**

* Create tags independently and apply them as needed
* Tag contacts individually or in bulk
* Filter contacts by tags
* **Send targeted emails to tagged contacts**

#### Example Use Case

Imagine you run a food-related website:

1. **Create tags**: "Desserts", "Japanese Cuisine", "Chinese Cuisine"
2. **Tag your contacts**:
   * Anna: "Desserts" + "Japanese Cuisine"
   * Emma: "Desserts" + "Chinese Cuisine"
3. **Send targeted campaigns**: When promoting new desserts, select the "Desserts" tag to reach all dessert enthusiasts

### Segments

Segments are dynamic contact groups created by filtering your audience based on specific rules and conditions. Think of them as advanced contact filters that automatically update based on your criteria.

#### Creating a Segment

1. **Name your segment**
2. **Choose matching logic**:
   * **All conditions**: Contacts must meet every condition
   * **Any condition**: Contacts need to meet at least one condition
3. **Set up to 10 conditions** based on contact properties and tags

#### Example Use Case

To conduct a user survey targeting women aged 25-30:

1. Create a segment named "Women 25-30 User Survey"
2. Set matching condition to "All conditions"
3. Add conditions:
   * Age ≥ 25
   * Age ≤ 30
   * Gender = Female
4. Preview filtered contacts and save
5. Send campaigns directly to this segment

**Benefits of Segments:**

* More precise targeting than tags alone
* Automatic updates as contact data changes
* Enable sophisticated marketing automation
* Support complex filtering logic