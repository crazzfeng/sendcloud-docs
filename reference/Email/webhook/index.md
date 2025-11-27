---
title: Webhook
hidden: false
---
<br />

# WebHooks

After you submit an email delivery request to Aurora SendCloud, the system synchronously returns the request result (such as whether the request was accepted). The final delivery result of the email (such as whether it was successfully delivered) and other interaction events (such as opens and clicks) are asynchronously pushed to your specified server via webhook.

Instead of requiring you to poll for updates, Aurora SendCloud actively pushes data to you in real-time when key events occur. This enables subsequent processes like data synchronization, statistical analysis, and triggering business workflows.

## How It Works

**Event Occurs:** When an email-related event occurs (such as an email being opened, a recipient clicking a link, or the email bouncing), Aurora SendCloud generates corresponding data.

**Trigger Notification:** Aurora SendCloud immediately sends an HTTP POST request to the URL you configured in your account settings.

**Data Transfer:** The event data is contained within the body of the POST request, typically encoded in JSON format.

**Receive & Process:** Your server receives the request, parses the data, and handles subsequent business logic (such as updating a database or sending an internal alert) based on the event type.

## Supported Event Types

Currently, Aurora SendCloud supports notifications for the following event types (partial list of common events):

| Event Type    | Description                                                   |
| :------------ | :------------------------------------------------------------ |
| request       | Send request event                                            |
| delivered     | Message successfully delivered to the recipient's mail server |
| open          | Recipient opened the email                                    |
| click         | Recipient clicked a link in the email                         |
| unsubscribe   | Recipient clicked the unsubscribe link                        |
| spam-report   | Recipient reported the email as spam                          |
| invalid_email | Invalid email address                                         |
| soft_bounce   | Soft bounce (temporary delivery failure)                      |
| route         | Routing status event                                          |

For the complete official list of event types and their detailed payload formats, please refer to the [Webhook Event Format Documentation].

## Configuration & Usage Steps

**Set the Webhook URL:**
Log in to the Aurora SendCloud platform, navigate to the Webhook settings page, and specify the API endpoint URL on your server that will receive the events.

**Validate the Endpoint:**
Ensure your server can correctly handle any validation requests sent by Aurora SendCloud to confirm URL accessibility.

**Parse Event Data:**
Write code to parse the JSON data in the POST request body and handle it accordingly based on the event type (such as identified by an event field).

**Return Success Status:**
After successfully receiving and processing the data, your server should return a 2xx HTTP status code (such as 200 OK) to Aurora SendCloud. If a non-2xx status code is returned, Aurora SendCloud may attempt to retry the notification based on its retry policy.

## Important Notes

**Retry Mechanism:** If your server is unreachable or does not return a successful response, Aurora SendCloud will typically retry the notification after a delay, up to a predefined retry limit.

**Security Verification:** It is highly recommended to implement security checks in your endpoint code (such as verifying the request source IP against a whitelist or validating a signature) to ensure requests are genuinely from Aurora SendCloud and prevent spoofing.

**Processing Performance:** Ensure your receiving endpoint can respond quickly (such as within 50ms) to avoid timeouts that might cause Aurora SendCloud to misinterpret the delivery as a failure.
