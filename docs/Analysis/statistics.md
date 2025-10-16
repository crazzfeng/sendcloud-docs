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
        Number of requests received by Aurora SendCloud.
      </td>
    </tr>

    <tr>
      <td>
        Delivered
      </td>

      <td>
        Number of successfully delivered emails.
        Ratio = Delivered/Requested.
      </td>
    </tr>

    <tr>
      <td>
        Invalid Email
      </td>

      <td>
        Number of emails that failed delivery.
        Ratio = Invalid Email/Requested.
      </td>
    </tr>

    <tr>
      <td>
        Soft Bounce
      </td>

      <td>
        Number of emails that were returned after successful delivery. Ratio = Soft Bounce/Requested.
      </td>
    </tr>

    <tr>
      <td>
        Billing Counts
      </td>

      <td>
        Number of emails that will be charged.
      </td>
    </tr>

    <tr>
      <td>
        Open
      </td>

      <td>
        Number of email opens. Each open is counted without deduplication.
        Ratio = Open/Delivered.
      </td>
    </tr>

    <tr>
      <td>
        Unique Open
      </td>

      <td>
        Number of recipients who opened the email. Each email is counted only once per recipient.
        Ratio = Unique Open/Delivered.
      </td>
    </tr>

    <tr>
      <td>
        Click
      </td>

      <td>
        Number of email clicks. Each click is counted without deduplication.
        Ratio = Click/Delivered.
      </td>
    </tr>

    <tr>
      <td>
        Unique Click
      </td>

      <td>
        Number of recipients who clicked a specific link in the email. Each link in an email is counted only once per recipient.
        Ratio = Unique Click/Delivered.
      </td>
    </tr>

    <tr>
      <td>
        Report Spam
      </td>

      <td>
        Number of emails reported as spam.
        Ratio = Spam/Delivered.
      </td>
    </tr>

    <tr>
      <td>
        Unsubscribe
      </td>

      <td>
        Number of emails from which users clicked to unsubscribe.
        Ratio = Unsubscribe/Delivered.
      </td>
    </tr>
  </tbody>
</Table>

<br />

> 📘 Tracking Statistics Example
>
> You send an email to recipients X and Y, and both emails are delivered successfully.
> X opens the email twice and clicks link M twice and link N once.
> Y opens the email 3 times and clicks link M once and link N twice.
>
> * Open: 2 + 3 = 5
> * Unique Open: 1 + 1 = 2
> * Click: 2 + 1 + 1 + 2 = 6
> * Unique Click: 1 + 1 + 1 + 1 = 4

<br />

# Email Statistics Dimensions

Here are the dimensions you can use for filtering and screening your statistics.

| Dimension        | Description                                                                                                      |
| :--------------- | :--------------------------------------------------------------------------------------------------------------- |
| Email Type       | Choose between Trigger or Batch. The email type is determined by the API_USER type used to send emails. |
| API_USER         | Choose an API_USER that was used to send emails.                                                         |
| Label            | Choose a label that was used to send emails.                                                             |
| Campaign         | Choose a campaign that is currently sending or has finished sending.                                |
| Receiving Domain | Enter the email provider's domain to search, such as gmail.com or yahoo.com.                              |
| Request Period   | The time period when you requested Aurora SendCloud to send emails. Defaults to the last 7 days.    |
| Send Tags        | The tags used for the API request.                                                                               |

# Email Statistics Categories

The sending and tracking statistics can be grouped into 4 categories that you can select in the filter:

* Group by day (default)
* Group by week
* Group by month
* Group by receiving domain

<br />