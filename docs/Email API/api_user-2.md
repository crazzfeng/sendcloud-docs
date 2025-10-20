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

This section describes the concept and management of API_USER, which serves as the primary credential for authenticating requests when using our Email Delivery API or SMTP service.

## Overview of API_USER

An **API_USER** is a dedicated account identity used exclusively for authenticating requests when calling our email-sending interfaces (API or SMTP). It operates separately from your main platform login account and is designed specifically for programmatic access.

<Accordion title="Creating an API_USER" icon="plus-circle">
  When creating an API\_USER, you must configure the following three key properties:

  ### Email Types

  <Cards columns="2">
    <Card title="Trigger Type" icon="bolt">
      API\_USERs of this type can **only send transactional/triggered emails** (e.g., password resets, order confirmations).
    </Card>

    <Card title="Batch Type" icon="envelope-bulk">
      API\_USERs of this type can **only send bulk marketing emails** (e.g., newsletters, promotions).
    </Card>
  </Cards>

  ### Sending Domain

  You must select and bind an **authenticated sending domain** to the API\_USER. All emails sent using this API\_USER's credentials will originate from this domain, which is crucial for maintaining sender reputation and ensuring deliverability.

  ### Tracking Options

  When enabled, SendCloud will automatically collect and provide tracking data for emails sent by this API\_USER. This typically includes metrics such as:

  * Opens
  * Clicks
  * Unsubscribes
  * Spam complaints
</Accordion>

<Accordion title="Managing Your API_KEY" icon="key">
  The **API\_KEY** serves as the password for the API\_USER and must be included in all sending requests.

  <Tabs>
    <Tab title="Generation & Security">
      **Generation:** You must log into your account and **manually generate** an API\_KEY for your API\_USER(s).

      **Security:** The API\_KEY is a sensitive credential. For security reasons, **it will be displayed only once** upon generation. Store it securely immediately, as it cannot be retrieved again in full and must be reset if lost.

      **Uniqueness:** Each API\_USER has its own corresponding API\_KEY. The keys for different API\_USERs may be the same or different.
    </Tab>

    <Tab title="Resetting Keys">
      **Individual Reset:** You can reset the API\_KEY for an individual API\_USER.

      **Batch Reset:** You can select multiple API\_USERs for a batch reset.

      > **Important:** A batch reset will assign the **same new API\_KEY** to all selected API\_USERs.

      **Key Rotation Grace Period:** After a reset, the new API\_KEY becomes effective immediately. However, to prevent disruption to your ongoing email streams, the **old API\_KEY will remain valid for a 15-minute grace period**. This allows you to update your applications smoothly.
    </Tab>
  </Tabs>
</Accordion>

<Accordion title="Security Best Practices" icon="shield-alt">
  The combination of your **API\_USER** and **API\_KEY** serves as the primary credential for authenticating your send requests. Treat them with the same level of security as a username and password.

  <Cards columns="1">
    <Card title="Security Guidelines" icon="exclamation-triangle">
      * Keep credentials confidential and never hard-code them directly into client-side applications or public code repositories
      * Store credentials securely using environment variables or secure credential management systems
      * If credentials are compromised, reset the API\_KEY immediately
      * Regularly rotate your API\_KEYs as part of your security practices
    </Card>
  </Cards>
</Accordion>
