---
title: Duration
deprecated: false
hidden: false
link:
  new_tab: false
metadata:
  title: >-
    Email Delivery Duration Analytics - Monitor Performance & Speed | Aurora
    SendCloud
  description: >-
    Track email delivery performance with comprehensive duration analytics.
    Monitor delivery times, identify bottlenecks, and optimize your email
    infrastructure for faster delivery.
  keywords:
    - email delivery
    - email delivery analytics
    - email delivery speed
    - email performance monitoring
    - email delivery duration
    - email infrastructure optimization
    - transactional email delivery
    - bulk email delivery
    - email delivery metrics
    - email analytics dashboard
  robots: index
---
# Email Delivery Duration Analytics

<Image align="center" alt="Time Consumption" border={false} caption="Time Consumption" src="https://files.readme.io/43b733cb72e1907e0a1279bc481e92a7cff9dc5767e91b3b02b34addbba18225-image.png" />

Email delivery speed is a critical performance metric that directly impacts user experience and business operations. For time-sensitive communications like registration confirmations, password resets, and transaction alerts, every second counts.

The Duration feature in Aurora SendCloud provides comprehensive analytics on email delivery times, helping you monitor and optimize your email infrastructure's performance.

## Why Email Delivery Speed Matters

<Cards columns={2}>
  <Card title="User Experience" icon="users">
    **Better User Experience**: Users receive critical information promptly

    **Higher Engagement**: Quick delivery improves open and click-through rates
  </Card>

  <Card title="Business Impact" icon="chart-line">
    **Reduced Support Tickets**: Timely notifications prevent user confusion

    **Improved Conversion**: Faster transactional emails lead to better conversion rates
  </Card>
</Cards>

## Time Measurement Gradients

Aurora SendCloud uses different time gradients based on email type to provide relevant performance insights:

<Tabs>
  <Tab title="Trigger Emails">
    Real-time, automated emails triggered by user actions:

    * **0s–3s** - Excellent performance
    * **3s–10s** - Good performance
    * **10s–1min** - Acceptable performance
    * **1min–5min** - Slow performance
    * **More than 5min** - Poor performance requiring attention
  </Tab>

  <Tab title="Batch Emails">
    Scheduled or bulk emails sent to multiple recipients:

    * **0–10min** - Excellent performance
    * **10min–1h** - Good performance
    * **1h–3h** - Acceptable performance
    * **3h–24h** - Slow performance
    * **More than 24h** - Poor performance requiring investigation
  </Tab>
</Tabs>

<br />

## Filtering Options

Analyze your email performance using these filtering dimensions:

| **Dimension**        | **Description**                                                                          |
| :------------------- | :--------------------------------------------------------------------------------------- |
| **Email Type**       | Filter by Trigger emails (transactional) or Batch emails (marketing)                     |
| **API_USER**         | View statistics for a specific API_USER                                                  |
| **Receiving Domain** | Break down results by recipient email providers' domains  (gmail.com , yahoo.com,  etc.) |
| **Request Period**   | Select the timeframe for your analysis (default: last 7 days)                            |

## Analytics and Grouping Options

Customize your duration analysis with these powerful grouping options:

<Cards columns={3}>
  <Card title="Overall Performance" icon="chart-bar">
    **Group by null** *(default)*

    View the complete performance distribution across all time gradients. This overview helps you understand your general delivery performance and identify patterns.
  </Card>

  <Card title="MP Analysis" icon="envelope">
    **Group by Receiving Domain**

    Analyze performance by email providers (Gmail, Outlook, Yahoo, etc.). This view helps you identify which providers may be causing delivery delays and optimize accordingly.
  </Card>

  <Card title="Daily Trends" icon="calendar-alt">
    **Group by Day**

    Review daily performance trends to identify peak times, system issues, or improvements over time. Perfect for monitoring the impact of infrastructure changes.
  </Card>
</Cards>

<br />

**Selecting the Right View**

Choose the grouping option that aligns with your specific monitoring needs:

* Use **Overall Performance** for general health checks
* Use **MP Analysis** when troubleshooting provider-specific issues
* Use **Daily Trends** for identifying patterns and measuring improvements
