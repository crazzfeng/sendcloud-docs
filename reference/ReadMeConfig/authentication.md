---
title: Authentication
excerpt: Set up the authentication for your API to help users manage their credentials.
api_config: authentication
hidden: true
icon: icon-key1
---
<br />

Email API Authentication
For all Email API endpoints, requests are authenticated using HTTPS Basic Auth. It requires you to provide a username and a password for each API request. The username is your API_USER and the password is your API_KEY — you can find and manage them by navigating to the API Key Management page via the Email API section in your account dashboard.
To set up or update your authentication credentials:
Log in to your account and access the Email API page from the main menu.
Navigate to the API Key Management section within the Email API page.
Here, you can create a new API_USER (following the platform’s naming guidelines) and generate a corresponding API_KEY.
If needed, you can also reset your existing API_KEY (note: resetting will invalidate the old key immediately, so update your integration promptly to avoid service disruptions).
All API requests must include these credentials in the Basic Auth header to be validated successfully.

SMS API Authentication
For All SMS API endpoints, requests are authenticated using HTTPS Basic Auth. It requires you to provide a username and a password for each API request. The username is your API Key and the password is your API Secret Key - you can find them in your API Key Management page.
