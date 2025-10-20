---
title: Label
deprecated: false
hidden: false
link:
  new_tab: false
metadata:
  robots: index
---
# Label

Labels are a powerful feature designed to help you categorize and track your email messages. They are particularly useful for scenarios such as A/B testing, campaign segmentation, and performance analysis.

## Overview

A Label allows you to assign a custom identifier to your emails. By using Labels, you can easily filter and query the sending status and performance metrics for a specific group of emails directly within the system.

## How to Work with Labels

<Accordion title="Creating a Label" icon="plus">
Create a Label within the platform by providing a meaningful name (e.g., `Welcome_Email_V2`, `Summer_Sale_Group_A`).

Upon successful creation, the system will automatically generate and assign a unique **Label ID** to it.
</Accordion>

<Accordion title="Tagging an Email" icon="tag">
When sending an email via API, include the unique Label ID in your request parameters.

This action effectively "tags" the email with that specific label.
</Accordion>

<Accordion title="Querying Data by Label" icon="search">
Once emails are sent with a Label, you can use this dimension for analysis:

* In the platform's statistics or analytics section, you can filter data by selecting a specific **Label**.
* This allows you to view aggregated sending statistics (e.g., delivery rates, open rates, click-through rates) and detailed statuses (e.g., processed, delivered, clicked) for all emails associated with that Label.
</Accordion>

## Common Use Cases

<Cards columns="3">
  <Card title="A/B Testing" icon="flask">
    Create different Labels (e.g., `Campaign_A_Subject_1`, `Campaign_A_Subject_2`) to track and compare the performance of various email versions.
  </Card>
  <Card title="Campaign Tracking" icon="chart-line">
    Assign a unique Label to each marketing campaign (e.g., `Q4_Promotion`, `Newsletter_January`) for precise performance monitoring.
  </Card>
  <Card title="Traffic Segmentation" icon="users">
    Use Labels to categorize emails by type (e.g., `Transactional_Password_Reset`, `Bulk_Newsletter`) or by target user group.
  </Card>
</Cards>

## Quick Summary

<Accordion title="Label Workflow Overview" icon="info-circle">
In essence, you create a Label in the system to get a unique ID, use that ID to tag emails when sending them, and then later use the Label as a filter to query the results of that specific batch of emails.

**The process:**
1. **Create** a Label → Get unique Label ID
2. **Tag** emails with Label ID when sending
3. **Query** and analyze results using the Label filter
</Accordion>