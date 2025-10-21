---
title: SMSHook
deprecated: false
hidden: false
link:
  new_tab: false
metadata:
  robots: index
---
# SMSHook

## Overview

SMSHook is Aurora SendCloud's webhook mechanism that provides real-time notifications about SMS events. When you submit SMS requests, you receive an immediate response, but delivery results and other event notifications are sent asynchronously through SMSHook.

## How SMSHook Works

<Accordion title="Event Flow" icon="flow-chart">
  1. **Event Occurs**: When an SMS-related event happens (delivery, failure, etc.)
  2. **Webhook Triggered**: SendCloud sends a POST request to your configured URL
  3. **Data Processing**: Your application receives and processes the event data
  4. **Response Required**: Your endpoint must return HTTP 200 within 3 seconds
</Accordion>

## Supported Events

| Event               | Code | Description                        | When Triggered                        |
| :------------------ | :--- | :--------------------------------- | :------------------------------------ |
| **Requested**       | 1    | SMS request received and processed | Request successfully submitted        |
| **Delivered**       | 20   | Message successfully delivered     | Recipient receives the SMS            |
| **Suppressed**      | 4    | Message blocked or suppressed      | Message filtered by carrier or system |
| **Failed**          | 5    | Delivery attempt failed            | Message delivery unsuccessful         |
| **Template Verify** | 8    | Template approval status           | Template review completed             |

## Setup Instructions

<Tabs>
  <Tab title="Configuration Steps">
    ### 1. Create Your Webhook Endpoint

    Create an HTTP service that:

    * Accepts POST requests
    * Responds to GET requests (for testing)
    * Returns HTTP status 200
    * Processes webhook data within 3 seconds

    ### 2. Configure in SendCloud Dashboard

    1. Navigate to **【SMSHook】** in your dashboard
    2. Select the events you want to monitor
    3. Enter your webhook URL
    4. Save your configuration

    > **Note**: SendCloud will test your URL to ensure it responds properly before activation.
  </Tab>

  <Tab title="Security Setup">
    ### Enable Signature Verification (Recommended)

    To verify that webhooks are genuinely from SendCloud:

    1. Get your `APP KEY` from the **【SMSHook】** section
    2. Implement signature verification in your code
    3. Compare the generated signature with the received one

    **Signature Algorithm**: SHA256 HMAC using `timestamp + token`
  </Tab>
</Tabs>

## Implementation Examples

<Tabs>
  <Tab title="Python">
    ```python
    import hashlib
    import hmac
    import json

    def verify_signature(app_key, token, timestamp, signature):
        """Verify webhook signature"""
        message = f"{timestamp}{token}"
        expected_signature = hmac.new(
            key=app_key.encode('utf-8'),
            msg=message.encode('utf-8'),
            digestmod=hashlib.sha256
        ).hexdigest()
        return expected_signature == signature

    def handle_webhook(request):
        """Handle incoming webhook"""
        data = json.loads(request.body)
        
        # Verify signature (recommended)
        if verify_signature(APP_KEY, data['token'], data['timestamp'], data['signature']):
            # Process the event
            event_type = data.get('event')
            
            if event_type == 'delivered':
                handle_delivery_success(data)
            elif event_type == 'failed':
                handle_delivery_failure(data)
            # ... handle other events
            
            return {"status": "success"}, 200
        else:
            return {"error": "Invalid signature"}, 401
    ```
  </Tab>

  <Tab title="Java">
    ```java
    import javax.crypto.Mac;
    import javax.crypto.spec.SecretKeySpec;
    import org.apache.commons.codec.binary.Hex;

    public class SMSHookHandler {
        
        public boolean verifySignature(String appKey, String token, long timestamp, String signature) 
                throws Exception {
            Mac sha256HMAC = Mac.getInstance("HmacSHA256");
            SecretKeySpec secretKey = new SecretKeySpec(appKey.getBytes(), "HmacSHA256");
            sha256HMAC.init(secretKey);
            
            String message = timestamp + token;
            String expectedSignature = new String(
                Hex.encodeHex(sha256HMAC.doFinal(message.getBytes()))
            );
            
            return expectedSignature.equals(signature);
        }
        
        @PostMapping("/webhook")
        public ResponseEntity<String> handleWebhook(@RequestBody Map<String, Object> data) {
            try {
                // Verify signature
                boolean isValid = verifySignature(
                    APP_KEY, 
                    (String) data.get("token"),
                    (Long) data.get("timestamp"),
                    (String) data.get("signature")
                );
                
                if (!isValid) {
                    return ResponseEntity.status(401).body("Invalid signature");
                }
                
                // Process event
                String eventType = (String) data.get("event");
                switch (eventType) {
                    case "delivered":
                        handleDeliverySuccess(data);
                        break;
                    case "failed":
                        handleDeliveryFailure(data);
                        break;
                    // ... handle other events
                }
                
                return ResponseEntity.ok("Success");
            } catch (Exception e) {
                return ResponseEntity.status(500).body("Error processing webhook");
            }
        }
    }
    ```
  </Tab>

  <Tab title="PHP">
    ```php
    <?php
    function verifySignature($appKey, $token, $timestamp, $signature) {
        $message = $timestamp . $token;
        $expectedSignature = hash_hmac('sha256', $message, $appKey);
        return hash_equals($expectedSignature, $signature);
    }

    function handleWebhook() {
        $input = file_get_contents('php://input');
        $data = json_decode($input, true);
        
        // Verify signature
        if (!verifySignature(APP_KEY, $data['token'], $data['timestamp'], $data['signature'])) {
            http_response_code(401);
            echo json_encode(['error' => 'Invalid signature']);
            return;
        }
        
        // Process event
        switch ($data['event']) {
            case 'delivered':
                handleDeliverySuccess($data);
                break;
            case 'failed':
                handleDeliveryFailure($data);
                break;
            // ... handle other events
        }
        
        http_response_code(200);
        echo json_encode(['status' => 'success']);
    }
    ?>
    ```
  </Tab>
</Tabs>

## Reliability & Error Handling

<Cards columns="2">
  <Card title="Retry Mechanism" icon="refresh">
    If your endpoint is unreachable or returns an error, SendCloud will retry:

    * **7 retry attempts** with increasing intervals
    * **Intervals**: 3min → 10min → 30min → 1hr → 6hr → 12hr → 24hr
    * **Backup storage**: Messages saved for 15 days after final retry
  </Card>

  <Card title="Response Requirements" icon="clock">
    Your webhook endpoint must:

    * Return **HTTP 200** status
    * Respond within **3 seconds**
    * Handle both GET (testing) and POST (events) requests
  </Card>
</Cards>

## Event Reference

<Tabs>
  <Tab title="Requested Event">
    Triggered when an SMS request is successfully processed.

    ### Parameters

    | Parameter    | Type   | Description                |
    | :----------- | :----- | :------------------------- |
    | `event`      | string | Always "Requested"         |
    | `eventType`  | int    | Always 1                   |
    | `message`    | string | Request status message     |
    | `userId`     | int    | Your user ID               |
    | `smsUser`    | string | SMS user identifier        |
    | `smsIds`     | array  | List of SMS message IDs    |
    | `templateId` | int    | Template used for the SMS  |
    | `phones`     | array  | Recipient phone numbers    |
    | `timestamp`  | long   | Event timestamp            |
    | `token`      | string | Random 50-character string |
    | `signature`  | string | Verification signature     |
    | `customArgs` | object | Your custom parameters     |

    ### Example Payload

    ```json
    {
      "event": "Requested",
      "eventType": 1,
      "message": "request",
      "userId": 19999,
      "smsUser": "App",
      "smsIds": ["1652150994014_9373_14466_36735_99drnc$13888888888"],
      "templateId": 29999,
      "phones": ["13888888888"],
      "timestamp": 1652150994087,
      "token": "VDymF6ihuJkKZjHiJZkLKGmY6q9qAQ2WGopLh7mBsDeAO6GKV5",
      "signature": "1ff237043487aeb4dc1b21c22b5ead9e4df94a31a3afa0ad53238eb38c2cbeea",
      "customArgs": {}
    }
    ```
  </Tab>

  <Tab title="Delivered Event">
    Triggered when an SMS is successfully delivered to the recipient.

    ### Parameters

    | Parameter      | Type   | Description                   |
    | :------------- | :----- | :---------------------------- |
    | `event`        | string | Always "Delivered"            |
    | `eventType`    | int    | Always 20                     |
    | `message`      | string | Delivery confirmation message |
    | `smsId`        | string | Deliver SMS message ID        |
    | `phone`        | string | Recipient phone number        |
    | `userId`       | int    | Your user ID                  |
    | `smsUser`      | string | SMS user identifier           |
    | `templateId`   | int    | Template used for the SMS     |
    | `outboundTime` | string | When message left SendCloud   |
    | `receiptTime`  | string | When delivery was confirmed   |
    | `msgCount`     | int    | Number of SMS segments        |
    | `timestamp`    | long   | Event timestamp               |
    | `token`        | string | Random 50-character string    |
    | `signature`    | string | Verification signature        |
    | `customArgs`   | object | Your custom parameters        |

    ### Example Payload

    ```json
    {
      "event": "Delivered",
      "eventType": 20,
      "message": "Successfully delivered",
      "userId": 19999,
      "templateId": 29999,
      "smsUser": "APP",
      "smsId": "1652117371408_19999_376_4631_qrwnpq$13888888888",
      "phone": "13888888888",
      "outboundTime": "2022-05-10 01:29:31",
      "receiptTime": "2022-05-10 01:29:50",
      "msgCount": 1,
      "timestamp": 1652117390000,
      "token": "4mRG9lGhVb3jZhOMnksFPBtX1OLDMNZMfXTFHkFd9eybfdRiHM",
      "signature": "9ca96fa072bfa048969aa0cb7bf7baf64100234640a1b9793cca1a419afb9cb8",
      "customArgs": {}

    }
    ```
  </Tab>

  <Tab title="Suppressed Event">
    Triggered when SMS delivery suppressed.

    ### Parameters

    | Parameter       | Type   | Description                  |
    | :-------------- | :----- | :--------------------------- |
    | `event`         | string | Always "Suppressed"          |
    | `eventType`     | int    | Always 4                     |
    | `smsId`         | string | Individual SMS message ID    |
    | `phone`         | string | Recipient phone number       |
    | `userId`        | int    | Your user ID                 |
    | `smsUser`       | string | SMS user identifier          |
    | `templateId`    | int    | Template used for the SMS    |
    | `message`       | string | Failure reason               |
    | `encodeMessage` | string | Base64-encoded error message |
    | `statusCode`    | int    | Error status code            |
    | `outboundTime`  | string | When message left SendCloud  |
    | `timestamp`     | long   | Event timestamp              |
    | `token`         | string | Random 50-character string   |
    | `signature`     | string | Verification signature       |
    | `customArgs`    | object | Your custom parameters       |

    ### Common Status Codes

    * **430**: Number in unsubscribe list
    * **440**: Invalid phone number
    * **450**: Carrier rejection

    ### Example Payload

    ```json
    {
      "event": "Suppressed",
      "eventType": 4,
      "userId": 19999,
      "templateId": 29999,
      "smsUser": "APP",
      "message": "REJECTED(其他)",
      "encodeMessage": "UkVKRUNURCjlhbbku5Yp",
      "statusCode": 490,
      "smsId": "1652146271665_19999_8755_3883_37059m$13888888888",
      "phone": "13888888888",
      "outboundTime": "2022-05-10 09:31:12",
      "timestamp": 1652146277000,
      "token": "4mRG9lGhVb3jZhOMnksFPBtX1OLDMNZMfXTFHkFd9eybfdRiHM",
      "signature": "9ca96fa072bfa048969aa0cb7bf7baf64100234640a1b9793cca1a419afb9cb8",
      "customArgs": {}

    }
    ```
  </Tab>

  <Tab title="Failed Event">
    Triggered when SMS delivery failed.

    ### Parameters

    | Parameter       | Type   | Description                  |
    | :-------------- | :----- | :--------------------------- |
    | `event`         | string | Always "Failed"              |
    | `eventType`     | int    | Always 5                     |
    | `phone`         | string | Recipient phone number       |
    | `smsId`         | string | Fail SMS message ID          |
    | `userId`        | int    | Your user ID                 |
    | `smsUser`       | string | SMS user identifier          |
    | `templateId`    | int    | Template used for the SMS    |
    | `message`       | string | Failure reason               |
    | `encodeMessage` | string | Base64-encoded error message |
    | `statusCode`    | int    | Error status code            |
    | `receiptTime`   | string | When failure was detected    |
    | `outboundTime`  | string | When message left SendCloud  |
    | `msgCount`      | int    | Number of SMS segments       |
    | `timestamp`     | long   | Event timestamp              |
    | `token`         | string | Random 50-character string   |
    | `signature`     | string | Verification signature       |
    | `customArgs`    | object | Your custom parameters       |

    ### Common Status Codes

    * **530**: Phone busy
    * **590**: General delivery failure

    ### Example Payload

    ```json
    {
      "event": "Failed",
      "eventType": 5,
      "userId": 19999,
      "templateId": 29999,
      "smsUser": "APP",
      "message": "REJECTED(其他)",
      "encodeMessage": "UkVKRUNURCjlhbbku5Yp",
      "statusCode": 590,
      "smsId": "1652146271665_19999_8755_3883_37059m$13888888888",
      "phone": "13888888888",
      "outboundTime": "2022-05-10 09:31:12",
      "receiptTime": "2022-05-10 09:31:17",
      "msgCount": 1,
      "timestamp": 1652146277000,
      "token": "4mRG9lGhVb3jZhOMnksFPBtX1OLDMNZMfXTFHkFd9eybfdRiHM",
      "signature": "9ca96fa072bfa048969aa0cb7bf7baf64100234640a1b9793cca1a419afb9cb8",
      "customArgs": {}
    }
    ```
  </Tab>

  <Tab title="Template Verify Event">
    Triggered when SMS template review is completed.

    ### Parameters

    | Parameter       | Type   | Description                                         |
    | :-------------- | :----- | :-------------------------------------------------- |
    | `event`         | string | Always "Template Verify"                            |
    | `eventType`     | int    | Always 8                                            |
    | `userId`        | int    | Your user ID                                        |
    | `templateId`    | int    | Template ID                                         |
    | `name`          | string | Template name                                       |
    | `verfiyResult`  | int    | Review result: 0=reviewing, 1=approved, -1=rejected |
    | `verfiyComment` | string | Review comments (if rejected)                       |
    | `timestamp`     | long   | Event timestamp                                     |
    | `token`         | string | Random 50-character string                          |
    | `signature`     | string | Verification signature                              |

    ### Example Payload

    ```json
    {
      "event": "Template Verify",
      "eventType": 8,
      "templateId": 6255,
      "name": "Thank you for visiting the Shanghai Auto Show booth",
      "verfiyResult": 1,
      "verfiyComment": "",
      "userId": 102,
      "timestamp": 1646628597226,
      "token": "M1dgqmmOsM3BC9dCqBsMjtDh6I5jYwXngPEtcVV9v8XoplF1VQ",
      "signature": "b80266d81f527c1ce870ba36c4c9e79fd9725c5a7c943577a25d8116aa67c927"
    }
    ```
  </Tab>
</Tabs>

## Best Practices

<Cards columns="2">
  <Card title="Security" icon="shield">
    * Always verify webhook signatures
    * Use HTTPS endpoints
    * Implement rate limiting
    * Log all webhook events
    * Validate all input data
  </Card>

  <Card title="Performance" icon="tachometer-alt">
    * Respond within 3 seconds
    * Process events asynchronously
    * Implement proper error handling
    * Use database transactions
    * Monitor endpoint health
  </Card>

  <Card title="Reliability" icon="check-circle">
    * Make endpoints idempotent
    * Handle duplicate events gracefully
    * Implement proper logging
    * Set up monitoring alerts
    * Test with various event types
  </Card>

  <Card title="Troubleshooting" icon="tools">
    * Check endpoint accessibility
    * Verify SSL certificate
    * Monitor response times
    * Review error logs
    * Test signature verification
  </Card>
</Cards>

## Need Help?

If you exceed the retry limit or need messages re-pushed, please contact our support team with your webhook configuration details.
