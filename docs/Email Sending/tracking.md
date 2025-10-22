---
title: Tracking
deprecated: false
hidden: false
link:
  new_tab: false
metadata:
  robots: index
---
Email tracking helps you collect open data, click data, and unsubscribe data for sent emails, allowing you to effectively evaluate email delivery performance and optimize marketing strategies and content design. Improve user engagement and conversion rates through data-driven insights.

## Tracking Configuration

**Configuration Path:**

Go to **Settings** → **Tracking** → Select the target **API_USER** → **Tracking Switch**

**Configurable Options:**

✅ **Open Tracking**: Records email opens  
✅ **Click Tracking**: Tracks clicks on links in emails  
✅ **Unsubscribe Tracking**: Manages the user unsubscribe process and data collection

## How Tracking Works

**Open Tracking**: Inserts a 1-pixel transparent tracking image into the email HTML. When the email is opened, the email client automatically loads the image, sending a request to the Aurora SendCloud server to count the open event.

**Click Tracking**: Replaces the original links in the email with tracking domain links containing parameters. When a user clicks a link, the request is first sent to Aurora SendCloud server (because the CNAME points to track2.sendcloud.net). After recording the click data, the system automatically redirects to the original target link.

**Unsubscribe Tracking**:

* The system inserts HTML code containing an unsubscribe link at the bottom of the email
* Alternatively, it replaces the `%%user_defined_unsubscribe_link%%` variable with the unsubscribe link
* Users click the link to access the unsubscribe page, select a reason, and submit
* Aurora SendCloud collects and processes unsubscribe information

## Tracking Domain Configuration

**Default Domain:**

* Aurora SendCloud provides shared tracking domains
* ⚠️ Data accuracy may be affected by other users' behavior

**Recommended Solution:**

🎯 **Customized Tracking Domain**: Enhance brand professionalism and ensure data independence

🔒 **HTTPS Encrypted Tracking**: Avoid browser blocking and improve data accuracy

**Important Note:**
Due to browser upgrades like Chrome, loading HTTP resources will be blocked. It is recommended to upload an SSL certificate and enable HTTPS tracking. Ensure the CNAME configuration in your DNS remains valid to prevent link failures.

## Tracking On/Off Management 

**Smart Recommendations:**

| Tracking Type        | Recommended Settings | Description                                                      |
| -------------------- | -------------------- | ---------------------------------------------------------------- |
| Open Tracking        | Enable as needed     | Helps understand email delivery performance                      |
| Click Tracking       | Recommended          | Key user engagement metrics                                      |
| Unsubscribe Tracking | Highly Recommended   | Prevents users from complaining directly to their email provider |

**Importance of Unsubscribe Tracking:**

* Provides legitimate unsubscribe channels to protect sender reputation
* Collects unsubscribe reasons to aid content optimization
* Complies with global privacy regulations (e.g., GDPR, CAN-SPAM)

## Best Practices

💡 **Data Accuracy Optimization:**

* Regularly monitor tracking domain name resolution status
* Promptly update SSL certificate validity periods
* Monitor data fluctuations and identify causes

**Privacy Compliance Recommendations:**

* Explain tracking data usage in your privacy policy
* Give users clear data control options
* Comply with local data protection regulations

**Data Analysis Tips:**

* Evaluate effectiveness by combining open and click-through rates
* Analyze user engagement trends over time
* Optimize email subject lines and content strategies based on data insights

## Troubleshooting

 **Common Problems:**

❓ **Clicking links doesn't redirect properly**  
✅ Check if the tracking domain CNAME configuration is working correctly

❓ **Open rate statistics are inaccurate**  
✅ Verify that automatic image loading is not blocked. HTTPS is recommended

❓ **Unsubscribe link doesn't display**  
✅ Verify that the template contains unsubscribe variables or code
