---
title: Authentication
excerpt: Set up the authentication for your API to help users manage their credentials.
api_config: authentication
hidden: true
icon: icon-key1
---
<br />

Email API Authentication
For all Email API endpoints, requests are authenticated by including your credentials directly in the request parameters (not via HTTPS Basic Auth or request headers). Specifically, you need to pass two parameters with each request: API_USER (your API username) and API_KEY (your API password).
Where to find and manage your credentials:
Log in to your account and navigate to the Email API page from the main menu.
Select the API Key Management section within the Email API page.
Here, you can:
Create a new API_USER (following platform naming conventions) and generate its associated API_KEY.
Reset an existing API_KEY: After resetting, the old key will remain valid for 15 minutes to allow time for updating your integration. It will be automatically invalidated once this grace period ends.

All requests must include api_user and api_key in the parameters to be validated. To avoid service interruptions, update your integration with the new API_KEY within the 15-minute window after resetting.

SMS API Authentication
For All SMS API endpoints, requests are authenticated using HTTPS Basic Auth. It requires you to provide a username and a password for each API request. The username is your API Key and the password is your API Secret Key - you can find them in your API Key Management page.
