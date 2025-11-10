---
title: Getting Started
excerpt: >-
  Complete guide to setting up your API documentation dashboard and helping
  users make their first successful API call.
api:
  file: send.json
  operationId: get_new-endpoint
api_config: getting-started
hidden: true
icon: icon-book1
link:
  new_tab: false
---
<br />

# AuroraSendCloud API Quickstart

Get started with AuroraSendCloud's powerful APIs to send emails, manage contacts, track performance, and integrate seamlessly with your applications. Follow this step-by-step guide to make your first API call in minutes—with clear distinctions between multi-region email APIs and the single-region SMS API.

## Prerequisites

Before you begin, ensure you have:

* An active AuroraSendCloud account (sign up at [aurorasendcloud.com](https://www.aurorasendcloud.com/))
* Your **API Key** and **API User** (found in your account’s [API Key Management](https://www.aurorasendcloud.com/docs/API/index/) page)
* A supported HTTP client (e.g., cURL, Postman, Python’s `requests` library)
* Confirm your account’s **region** (Singapore, US, or Hong Kong) for email API access (not required for SMS API)

## 1. API Base URLs (By Service Type)

### Email & Core APIs (Multi-Region)

Choose the base URL that matches your account’s region for email, contact management, templates, and other core services. All requests must use **HTTPS**, and responses are in **JSON** format.

| Region             | Base URL                                 | Coverage                                  |
| ------------------ | ---------------------------------------- | ----------------------------------------- |
| Singapore (SG)     | `https://api.aurorasendcloud.com/v1/`    | Default region for APAC users             |
| United States (US) | `https://api-us.aurorasendcloud.com/v1/` | For North American users and services     |
| Hong Kong (HK)     | `https://api-hk.aurorasendcloud.com/v1/` | For Greater China and nearby APAC regions |

> ℹ️ Note: Your account is tied to a specific region during sign-up. Using a non-matching base URL for email/core APIs will cause authentication failures or data inconsistencies. Confirm your region in account settings.

### SMS API (Single Region)

The SMS API uses a **unified global base URL** (no regional endpoints required):

* Base URL: `https://api.aurorasendcloud.com/v1/`
* All SMS requests must use this URL regardless of your account’s region.
* Authentication and response format are consistent with email/core APIs.

## 2. Authentication

Authenticate all API requests (email, SMS, core services) by including your credentials as **request parameters**:

* `api_user`: Your AuroraSendCloud API username
* `api_key`: Your AuroraSendCloud API key

> ⚠️ Critical Security Note: Never expose your API credentials in client-side code (e.g., browsers, mobile apps). Restrict access to your API key, rotate it regularly via the API Key Management page, and avoid hardcoding credentials in source code.

## 3. API Response Format

All API responses (email and SMS) follow a consistent JSON structure:

### Success Example (Request Successful)

```json
{
  "result": true,
  "statusCode": 200,
  "message": "request was successful",
  "info": {}
}
```

### Success Example (Data Acquisition)

```json
{
  "statusCode": 200,
  "info": {
    "data": {
      "gmtCreated": "2015-10-19 15:39:27",
      "gmtUpdated": "2015-10-19 15:39:27",
      "labelId": 123,
      "labelName": "test"
    }
  },
  "message": "request was successful",
  "result": true
}
```

### Error Example (Authentication Failed)

```json
{
  "result": false,
  "statusCode": 40005,
  "message": "authentication failed",
  "info": {}
}
```

#### Response Field Definitions:

* `result`: Boolean indicating if the request succeeded (`true`) or failed (`false`).
* `statusCode`: Numeric code representing the request status (see full list below).
* `message`: Chinese description of the status code (for debugging and user feedback).
* `info`: Contains response data (e.g., SMS/email IDs, retrieved records) on success; empty on failure.

## 4. API Return Codes

The following table lists common return codes and their meanings (applicable to both email and SMS APIs):

| Status Code | Meaning                                                |
| ----------- | ------------------------------------------------------ |
| 200         | Request was successful                                 |
| 40001       | `start` cannot be empty                                |
| 40002       | Invalid `start` parameter                              |
| 40003       | `limit` cannot be empty                                |
| 40004       | Invalid `limit` parameter                              |
| 40005       | Authentication failed (check `api_user`/`api_key`)     |
| 40006       | Invalid `days` format (must be a positive integer)     |
| 40007       | Invalid `startDate` format (use "YYYY-MM-DD")          |
| 40008       | Invalid `endDate` format (use "YYYY-MM-DD")            |
| 40011       | `email` cannot be empty                                |
| 40012       | Invalid email format                                   |
| 40100       | Label was successfully created                         |
| 40101       | Failed to create label                                 |
| 40107       | Label was successfully deleted                         |
| 40108       | Failed to delete label                                 |
| 40301       | User does not exist                                    |
| 40903       | Email sent successfully                                |
| 40901       | Email sending failed                                   |
| 40912       | Your account balance is insufficient (please recharge) |
| 50000       | Interface frequency limited                            |
| 501         | Server exception                                       |
| 6001        | You don't have permission to access                    |

For a full list of return codes, refer to the [API Reference](https://www.aurorasendcloud.com/docs/API/index/).

## 5. Next Steps

Explore key API endpoints to extend your integration:

* [Email APIs](https://www.aurorasendcloud.com/docs/API/index/): Send transactional/bulk emails, track deliveries (use region-specific base URL)
* [SMS API](https://www.aurorasendcloud.com/docs/API/index/): Send transactional SMS (use unified `api.aurorasendcloud.com/v1/` URL)
* [Contact Management](https://www.aurorasendcloud.com/docs/API/index/): Create/update contacts, manage lists (region-specific)
* [Email Templates](https://www.aurorasendcloud.com/docs/API/index/): Use pre-built templates for consistent branding (region-specific)
* [Suppression Lists](https://www.aurorasendcloud.com/docs/API/index/): Manage unsubscribes and bounces (region-specific)

## 6. Resources

* [Full API Reference](https://www.aurorasendcloud.com/docs/API/index/): Detailed docs for all endpoints (includes SMS-specific parameters)
* [SDKs & Libraries](https://www.aurorasendcloud.com/docs/API/index/): Official libraries for Python, Java, Node.js, and PHP (supports both multi-region and SMS APIs)
* [Region-Specific Compliance](https://www.aurorasendcloud.com/docs/API/index/): Guidelines for GDPR (EU/US), PDPA (SG/HK), and SMS regulatory requirements
* [Support](https://www.aurorasendcloud.com/support): Contact the team for region-specific or SMS API-related technical issues

***

Want me to help you add **SMS API-specific parameter details** (e.g., required fields for sending SMS) or **a side-by-side comparison of email vs. SMS API usage** to clarify differences?
