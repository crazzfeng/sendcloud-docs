---
title: API_USER
deprecated: false
hidden: false
link:
  new_tab: false
metadata:
  robots: index
---
# API_USER

This section describes the concept and management of the API_USER, which is the primary credential for authenticating your requests when using our Email Delivery API or SMTP service.

## Overview of API_USER

An **API_USER** is a dedicated account identity used exclusively for authenticating requests when calling our email-sending interfaces (API or SMTP). It is separate from your main platform login account and is designed specifically for programmatic access.

<Accordion title="Creating an API_USER" icon="plus-circle">

When creating an API_USER, you must configure the following three key properties:

### Email Types

<Cards columns="2">
  <Card title="Trigger Type" icon="bolt">
    API_USERs of this type can **only send transactional/triggered emails** (e.g., password resets, order confirmations).
  </Card>
  <Card title="Batch Type" icon="envelope-bulk">
    API_USERs of this type can **only send bulk marketing emails** (e.g., newsletters, promotions).
  </Card>
</Cards>

### Sending Domain

You must select and bind an **authenticated sending domain** to the API_USER. All emails sent using this API_USER's credentials will originate from this domain, which is crucial for sender reputation and deliverability.

### Tracking Options

When enabled, SendCloud will automatically collect and provide tracking data for the emails sent by this API_USER. This typically includes metrics such as:

- Opens
- Clicks
- Unsubscribes
- Spam complaints

</Accordion>

<Accordion title="Managing Your API_KEY" icon="key">

The **API_KEY** serves as the password for the API_USER and must be included in all sending requests.

<Tabs>
  <Tab title="Generation & Security">
    **Generation:** After successful platform registration, you must log into your account and **manually generate** an API_KEY for your API_USER(s).

    **Security:** The API_KEY is a sensitive credential. For security reasons, **it will be displayed only once** upon generation. Please store it securely immediately. It cannot be retrieved again in full; it must be reset if lost.

    **Uniqueness:** Each API_USER has its own corresponding API_KEY. The keys for different API_USERs can be the same or different.
  </Tab>
  
  <Tab title="Resetting Keys">
    **Individual Reset:** You can reset the API_KEY for an individual API_USER.

    **Batch Reset:** You can select multiple API_USERs for a batch reset.
    
    > **Important:** A batch reset will assign the **same new API_KEY** to all selected API_USERs.

    **Key Rotation Grace Period:** After a reset, the new API_KEY becomes effective immediately. However, to prevent disruption to your ongoing email streams, the **old API_KEY will remain valid for a grace period of 15 minutes**. This allows you to update your applications smoothly.
  </Tab>
</Tabs>

</Accordion>

<Accordion title="Security Best Practices" icon="shield-alt">

The combination of your **API_USER** and **API_KEY** is the primary credential for authenticating your send requests. Treat them with the same level of security as a username and password.

<Cards columns="1">
  <Card title="Security Guidelines" icon="exclamation-triangle">
    - Keep them confidential and never hard-code them directly into client-side applications or public code repositories
    - Store credentials securely using environment variables or secure credential management systems
    - If compromised, reset the API_KEY immediately
    - Regularly rotate your API_KEYs as part of your security practices
  </Card>
</Cards>

</Accordion>