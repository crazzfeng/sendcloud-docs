---
title: Tracking
deprecated: false
hidden: false
metadata:
  robots: index
---
<br />

Email Tracking and Analytics

Email tracking helps you collect open data, click data, and unsubscribe data for sent emails, allowing you to effectively evaluate email delivery performance and optimize marketing strategies and content design. Improve user engagement and conversion rates through data-driven insights.

Tracking Configuration

Configuration Path:

Go to [Settings] → [Tracking] → Select the target API_USER → [Tracking Switch]

Configurable Options:

✅ Open Tracking: Records email opens
✅ Click Tracking: Tracks clicks on links in emails
✅ Unsubscribe Tracking: Manages the user unsubscribe process and data collection

How it works

Open Tracking: Inserts a 1-pixel transparent tracking image into the email HTML. When the email is opened, the email client automatically loads the image. A request is sent to the Aurora SendCloud server to count the open event.

Click Tracking: Replaces the original link in the email with a tracking domain link with parameters. When a user clicks a link, the request is first sent to Aurora SendCloud. SendCloud server (because the CNAME points to track2.sendcloud.net)
After recording the click data, the system automatically redirects to the original target link.

Unsubscribe tracking:

The system inserts HTML code containing an unsubscribe link at the bottom of the email.

Or, replace the %%user_defined_unsubscribe_link%% variable with the unsubscribe link.

Users click the link to access the unsubscribe page, select a reason, and submit.

Aurora SendCloud collects and processes unsubscribe information.

Tracking Domain Configuration 🌐

Default Domain:

Aurora SendCloud provides shared tracking domains.
⚠️ Data accuracy may be affected by other user behavior.

Recommended Solution:

🎯

Customized Tracking Domain: Enhance brand professionalism and ensure data independence.

🔒

HTTPS Encrypted Tracking: Avoid browser blocking and improve data accuracy.

Important Note:

Due to browser upgrades like Chrome, loading HTTP resources will be blocked.

It is recommended to upload an SSL certificate and enable HTTPS tracking.

Ensure the CNAME configuration in your DNS remains valid to prevent link failure.

Tracking On/Off Management 🔄
​​Smart Recommendations:

Tracking Type

Recommended Settings

Description

Open Tracking

Enable as needed

Helps understand email delivery performance

Click Tracking

Recommended

Key User Engagement Metrics

Unsubscribe Tracking

Highly Recommended

Prevents users from complaining directly to their email provider

Importance of Unsubscribe Tracking:

Provides legitimate unsubscribe channels to protect sender reputation

Collects unsubscribe reasons to aid content optimization

Complies with global privacy regulations (e.g., GDPR, CAN-SPAM)

Best Practices

💡

Data Accuracy Optimization:

Regularly monitor and track domain name resolution status

Promptly update SSL certificate validity periods

Monitor data fluctuations and identify causes

Privacy Compliance Recommendations:

Explanate tracking data usage in your privacy policy

Give users clear data control

Comply with local data protection regulations

Data Analysis Tips:

Evaluate effectiveness by combining open and click-through rates

Analyze user engagement over time

Optimize email subject lines and content strategies based on data

Troubleshooting

🔧

Common Problems:

❓ Clicking the link doesn't redirect.
✅ Check if the tracking domain CNAME configuration is effective.
❓ Open rate statistics are inaccurate.
✅ Verify that automatic image loading is not blocked. HTTPS is recommended.
❓ Unsubscribe link doesn't display.
✅ Verify that the template contains unsubscribe variables or code.
