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
For All SMS API endpoints, requests are authenticated by including your credentials directly in the request parameters (not via HTTPS Basic Auth or request headers). Specifically, you need to pass two parameters with each request: sms_user (your SMS username) and sms_key (your SMS password).
Where to find and manage your credentials:
Log in to your account and navigate to the Integrations page from the main menu.
Select SMS Manage from the Integrations section, then access the Send Settings page.
Here, you can:
Add a new SMS_USER (following platform naming conventions) and generate its associated SMS_KEY.
Reset an existing SMS_KEY: The new SMS_KEY will take effect immediately after resetting. The old key will be invalidated right away, so ensure your integration is updated with the new key promptly to avoid service disruptions.

All requests must include sms_user and the valid sms_key in the parameters to be validated. Since the old key becomes invalid immediately after reset, we recommend testing the integration with the new key right after the reset process.
