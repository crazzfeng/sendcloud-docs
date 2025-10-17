---
title: Duration
deprecated: false
hidden: false
link:
  new_tab: false
metadata:
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

## Best Practices

<Accordion title="Performance Optimization Guide" icon="cog">

### Setting Up Monitoring

1. **Set Performance Benchmarks**: Define acceptable delivery times for different email types
2. **Monitor Regularly**: Check duration statistics weekly to catch performance issues early
3. **Track Improvements**: Monitor how infrastructure changes affect delivery times

### Troubleshooting Performance Issues

<Columns layout="auto">
  <Column>
    **Investigate Anomalies**: When emails consistently fall into slower gradients, investigate potential causes:
    
    * Check server load and capacity
    * Review sending reputation
    * Analyze domain-specific patterns
  </Column>
  <Column>
    **Optimize Based on Data**: Use domain-specific data to adjust sending strategies:
    
    * Adjust sending rates for specific providers
    * Implement retry logic for slow domains
    * Consider alternative routing for critical emails
  </Column>
</Columns>

### Selecting the Right View

Choose the grouping option that aligns with your specific monitoring needs:

* Use **Overall Performance** for general health checks
* Use **MP Analysis** when troubleshooting provider-specific issues  
* Use **Daily Trends** for identifying patterns and measuring improvements

</Accordion>