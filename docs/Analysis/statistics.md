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
## Aurora SendCloud Email Statistics

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

Organize your email statistics data by selecting one of these grouping methods:

* **Group by Day** _(default)_ - Daily performance breakdown
* **Group by Week** - Weekly performance trends
* **Group by Month** - Monthly performance overview
* **Group by Receiving Domain** - Performance by email provider

Choose the grouping that best matches your reporting needs and analysis goals.
