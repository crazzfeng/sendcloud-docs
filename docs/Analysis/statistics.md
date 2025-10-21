---
title: Statistics
excerpt: >-
  Aurora SendCloud's statistics covers the statistics of sending and tracking
  under different filter conditions and different dimensions.
deprecated: false
hidden: false
link:
  new_tab: false
metadata:
  robots: index
---
# Aurora SendCloud Email Statistics

<Image align="center" alt="Email Statistics Dashboard" border={false} caption="Email Statistics Dashboard" src="https://files.readme.io/4880c0cfb7250a8230597943b747944de1b37c3c84834bc61ecad65652eff51d-_20251016191511.png" />

Aurora SendCloud provides comprehensive email statistics to help you track the performance of your email campaigns. Monitor delivery rates, engagement metrics, and recipient behavior across different dimensions and time periods.

## Understanding Your Email Metrics

Track your email performance with these key metrics:

<Table align={["left","left"]}>
  <thead>
    <tr>
      <th>
        Metric
      </th>

      <th>
        Description
      </th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td>
        <strong>Requested</strong>
      </td>

      <td>
        Total number of email send requests submitted to Aurora SendCloud
      </td>
    </tr>

    <tr>
      <td>
        <strong>Delivered</strong>
      </td>

      <td>
        Emails successfully delivered to recipient inboxes<br />
        <em>Rate = Delivered ÷ Requested</em>
      </td>
    </tr>

    <tr>
      <td>
        <strong>Invalid Email</strong>
      </td>

      <td>
        Emails rejected due to invalid or malformed email addresses<br />
        <em>Rate = Invalid Email ÷ Requested</em>
      </td>
    </tr>

    <tr>
      <td>
        <strong>Soft Bounce</strong>
      </td>

      <td>
        Emails temporarily rejected (full mailbox, server issues, etc.)<br />
        <em>Rate = Soft Bounce ÷ Requested</em>
      </td>
    </tr>

    <tr>
      <td>
        <strong>Billing Counts</strong>
      </td>

      <td>
        Number of emails that count toward your account usage and billing
      </td>
    </tr>

    <tr>
      <td>
        <strong>Opens</strong>
      </td>

      <td>
        Total email opens, including multiple opens by the same recipient<br />
        <em>Rate = Opens ÷ Delivered</em>
      </td>
    </tr>

    <tr>
      <td>
        <strong>Unique Opens</strong>
      </td>

      <td>
        Number of individual recipients who opened the email at least once<br />
        <em>Rate = Unique Opens ÷ Delivered</em>
      </td>
    </tr>

    <tr>
      <td>
        <strong>Clicks</strong>
      </td>

      <td>
        Total link clicks, including multiple clicks by the same recipient<br />
        <em>Rate = Clicks ÷ Delivered</em>
      </td>
    </tr>

    <tr>
      <td>
        <strong>Unique Clicks</strong>
      </td>

      <td>
        Number of individual recipients who clicked at least one link<br />
        <em>Rate = Unique Clicks ÷ Delivered</em>
      </td>
    </tr>

    <tr>
      <td>
        <strong>Spam Reports</strong>
      </td>

      <td>
        Emails marked as spam by recipients<br />
        <em>Rate = Spam Reports ÷ Delivered</em>
      </td>
    </tr>

    <tr>
      <td>
        <strong>Unsubscribes</strong>
      </td>

      <td>
        Recipients who clicked unsubscribe links<br />
        <em>Rate = Unsubscribes ÷ Delivered</em>
      </td>
    </tr>
  </tbody>
</Table>

<br />

<Callout icon="📘" theme="info">
  Open, Click, Unsubscribe statistics can only be counted after you have opened the tracking switch.
</Callout>

### Tracking Statistics Example

<Callout icon="📊" theme="default">
  ### **Example Calculation**

  **Scenario:** You send emails to recipients X and Y. Both emails are successfully delivered.

  **Activity:**

  * Recipient X: Opens email 2 times, clicks link M twice, clicks link N once
  * Recipient Y: Opens email 3 times, clicks link M once, clicks link N twice

  **Results:**

  * **Opens:** 2 + 3 = **5 total opens**
  * **Unique Opens:** 1 + 1 = **2 unique recipients**
  * **Clicks:** 2 + 1 + 1 + 2 = **6 total clicks**
  * **Unique Clicks:** 1 + 1 = **2 unique recipients**
</Callout>

## Filtering Options

Analyze your email performance using these filtering dimensions:

| **Dimension**        | **Description**                                                                          |
| :------------------- | :--------------------------------------------------------------------------------------- |
| **Email Type**       | Filter by Trigger emails (transactional) or Batch emails (marketing)                     |
| **API_USER**         | View statistics for a specific API_USER                                                  |
| **Label**            | Filter by custom labels assigned to your email sends                                     |
| **Campaign**         | Analyze performance of specific email campaigns                                          |
| **Receiving Domain** | Break down results by recipient email providers' domains  (gmail.com , yahoo.com,  etc.) |
| **Request Period**   | Select the timeframe for your analysis (default: last 7 days)                            |
| **Send Tags**        | Filter by custom tags included in your API requests                                      |

## Grouping Options

Organize your email statistics data by selecting the most appropriate grouping method for your analysis needs. Each grouping option provides different insights into your email performance patterns.

<Cards columns={2}>
  <Card title="Group by Day" icon="calendar-day">
    **Default Option**
    
    Get detailed daily breakdowns of your email performance. Perfect for:
    - Monitoring recent campaign performance
    - Identifying daily sending patterns
    - Tracking immediate response to email sends
    - Analyzing short-term trends and fluctuations
    
    *Best for: Daily monitoring and immediate performance insights*
  </Card>

  <Card title="Group by Week" icon="calendar-week">
    **Weekly Trends**
    
    View performance aggregated by week to understand broader patterns. Ideal for:
    - Identifying weekly performance cycles
    - Comparing week-over-week improvements
    - Smoothing out daily variations
    - Planning weekly email schedules
    
    *Best for: Medium-term trend analysis and weekly reporting*
  </Card>

  <Card title="Group by Month" icon="calendar-alt">
    **Monthly Overview**
    
    Analyze long-term performance with monthly aggregations. Great for:
    - Executive reporting and high-level insights
    - Year-over-year performance comparisons
    - Seasonal trend identification
    - Budget and resource planning
    
    *Best for: Strategic planning and long-term performance review*
  </Card>

  <Card title="Group by Receiving Domain" icon="at">
    **Provider Analysis**
    
    Break down performance by email service providers. Essential for:
    - Understanding deliverability across different providers
    - Identifying provider-specific issues
    - Optimizing content for different email clients
    - Troubleshooting delivery problems
    
    *Best for: Deliverability optimization and provider-specific insights*
  </Card>
</Cards>

### Choosing the Right Grouping

Select your grouping method based on your specific analysis goals:

- **📊 Real-time Monitoring**: Use daily grouping to track immediate campaign performance
- **📈 Trend Analysis**: Choose weekly grouping to identify patterns and cycles  
- **📋 Executive Reporting**: Select monthly grouping for high-level strategic insights
- **🔧 Technical Troubleshooting**: Use domain grouping to diagnose deliverability issues

<Callout icon="💡" theme="success">
  **Pro Tip**: You can switch between different grouping options within the same report to gain multiple perspectives on your email performance data.
</Callout>