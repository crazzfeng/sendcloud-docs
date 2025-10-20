---
title: API_USER
deprecated: false
hidden: false
metadata:
  robots: index
---
<br />

API_USER Management​​
This section describes the concept and management of the API_USER, which is the primary credential for authenticating your requests when using our Email Delivery API or SMTP service.
​​Overview of API_USER​​
An ​​API_USER​​ is a dedicated account identity used exclusively for authenticating requests when calling our email-sending interfaces (API or SMTP). It is separate from your main platform login account and is designed specifically for programmatic access.
​​Creating an API_USER​​
When creating an API_USER, you must configure the following three key properties:
​​Type​​
Specify the type of email this API_USER is authorized to send. This ensures the correct sending infrastructure and policies are applied.
​​Trigger Type:​​ API_USERs of this type can ​​only send transactional/triggered emails​​ (e.g., password resets, order confirmations).
​​Batch Type:​​ API_USERs of this type can ​​only send bulk marketing emails​​ (e.g., newsletters, promotions).
​​Sending Domain​​
You must select and bind an ​​authenticated sending domain​​ to the API_USER. All emails sent using this API_USER's credentials will originate from this domain, which is crucial for sender reputation and deliverability.
​​Tracking Options​​
When enabled, SendCloud will automatically collect and provide tracking data for the emails sent by this API_USER. This typically includes metrics such as:
Opens
Clicks
Unsubscribes
Spam complaints

​​Managing Your API_KEY​​
The ​​API_KEY​​ serves as the password for the API_USER and must be included in all sending requests.
​​Generation:​​ After successful platform registration, you must log into your account and ​​manually generate​​ an API_KEY for your API_USER(s).
​​Security:​​ The API_KEY is a sensitive credential. For security reasons, ​​it will be displayed only once​​ upon generation. Please store it securely immediately. It cannot be retrieved again in full; it must be reset if lost.
​​Uniqueness:​​ Each API_USER has its own corresponding API_KEY. The keys for different API_USERs can be the same or different.
​​Resetting the Key:​​
You can reset the API_KEY for an individual API_USER or select multiple API_USERs for a batch reset.
​​Important:​​ A batch reset will assign the ​​same new API_KEY​​ to all selected API_USERs.
​​Key Rotation Grace Period:​​ After a reset, the new API_KEY becomes effective immediately. However, to prevent disruption to your ongoing email streams, the ​​old API_KEY will remain valid for a grace period of 15 minutes​​. This allows you to update your applications smoothly.
​​Important Security Note​​
The combination of your ​​API_USER​​ and ​​API_KEY​​ is the primary credential for authenticating your send requests. Treat them with the same level of security as a username and password.
Keep them confidential and never hard-code them directly into client-side applications or public code repositories.
If compromised, reset the API_KEY immediately.
