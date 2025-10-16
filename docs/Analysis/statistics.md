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
<Image align="center" alt="Email Statistics" border={false} caption="Email Statistics" src="https://files.readme.io/4880c0cfb7250a8230597943b747944de1b37c3c84834bc61ecad65652eff51d-_20251016191511.png" />

# Email Statistics Metrics

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
        Requested
      </td>

      <td>
        The number of email requests received by Aurora SendCloud.
      </td>
    </tr>

    <tr>
      <td>
        Delivered
      </td>

      <td>
        The number of emails successfully delivered.
        Ratio = Delivered/Requested.
      </td>
    </tr>

    <tr>
      <td>
        Invalid Email
      </td>

      <td>
        The number of emails that failed delivery due to invalid email addresses.
        Ratio = Invalid Email/Requested.
      </td>
    </tr>

    <tr>
      <td>
        Soft Bounce
      </td>

      <td>
        The number of emails that were temporarily rejected after delivery attempt. Ratio = Soft Bounce/Requested.
      </td>
    </tr>

    <tr>
      <td>
        Billing Counts
      </td>

      <td>
        The number of emails that will be charged to your account.
      </td>
    </tr>

    <tr>
      <td>
        Open
      </td>

      <td>
        The total number of email opens. Each open is counted individually without deduplication.
        Ratio = Open/Delivered.
      </td>
    </tr>

    <tr>
      <td>
        Unique Open
      </td>

      <td>
        The number of unique recipients who opened the email. Each email is counted only once per recipient.
        Ratio = Unique Open/Delivered.
      </td>
    </tr>

    <tr>
      <td>
        Click
      </td>

      <td>
        The total number of email clicks. Each click is counted individually without deduplication.
        Ratio = Click/Delivered.
      </td>
    </tr>

    <tr>
      <td>
        Unique Click
      </td>

      <td>
        The number of unique recipients who clicked any link in the email. Each link in an email is counted only once per recipient.
        Ratio = Unique Click/Delivered.
      </td>
    </tr>

    <tr>
      <td>
        Report Spam
      </td>

      <td>
        The number of emails reported as spam by recipients.
        Ratio = Spam/Delivered.
      </td>
    </tr>

    <tr>
      <td>
        Unsubscribe
      </td>

      <td>
        The number of recipients who clicked the unsubscribe link in the email.
        Ratio = Unsubscribe/Delivered.
      </td>
    </tr>
  </tbody>
</Table>

<br />

> 📘 Tracking Statistics Example
>
> You send an email to recipients X and Y, and both emails are delivered successfully.
> Recipient X opens the email twice and clicks link M twice and link N once.
> Recipient Y opens the email 3 times and clicks link M once and link N twice.
>
> The resulting statistics would be:
> * Open: 2 + 3 = 5
> * Unique Open: 1 + 1 = 2
> * Click: 2 + 1 + 1 + 2 = 6
> * Unique Click: 1 + 1 + 1 + 1 = 4

<br />

# Email Statistics Dimensions

Here are the dimensions you can use to filter and analyze your email statistics.

| Dimension        | Description                                                                                                      |
| :--------------- | :--------------------------------------------------------------------------------------------------------------- |
| Email Type       | Filter by Trigger or Batch emails. The email type is determined by the API_USER type used to send the emails. |
| API_USER         | Filter by a specific API_USER that was used to send emails.                                                         |
| Label            | Filter by a specific label that was used to send emails.                                                             |
| Campaign         | Filter by a specific campaign that is currently sending or has completed sending.                                |
| Receiving Domain | Filter by the recipient's email provider domain (e.g., gmail.com, yahoo.com).                              |
| Request Period   | The time period when you requested Aurora SendCloud to send emails. Defaults to the last 7 days.    |
| Send Tags        | Filter by the tags used in the API request.                                                                               |

# Email Statistics Categories

Email sending and tracking statistics can be grouped into 4 categories for analysis:

* **Group by day** (default)
* **Group by week**
* **Group by month**
* **Group by receiving domain**

<br />