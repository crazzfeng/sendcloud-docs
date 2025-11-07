---
title: Authentication
excerpt: Set up the authentication for your API to help users manage their credentials.
api_config: authentication
hidden: true
icon: icon-key1
---
<br />

Email API Authentication
For all Email API endpoints, requests are authenticated using HTTPS Basic Auth. It requires you to provide a username and a password for each API request. The username is your API Key and the password is your API Secret Key - you can find them in your API Key Management page. Both keys are generated automatically when your account is created.

SMS API Authentication
All SMS API endpoints use Bearer Token authentication. Bearer Tokens are a compact, URL-safe means of representing claims to be transferred between two parties. Create your token in Mailjet's SMS Dashboard by clicking on 'Generate your access token'. The token value is displayed only once. Make sure to save it locally before closing the modal window.

The access token must be included in the Authorization header of your request.
