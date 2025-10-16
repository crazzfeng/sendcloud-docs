---
title: Statistics
excerpt: >-
  Aurora SendCloud's statistics covers the statistics of sending and tracking
  under different filter conditions and different dimensions.
deprecated: false
hidden: false
metadata:
  robots: index
---
<Image align="center" alt="Email Statistics" border={false} caption="Email Statistics" src="https://files.readme.io/4880c0cfb7250a8230597943b747944de1b37c3c84834bc61ecad65652eff51d-_20251016191511.png" />

# Metrics of Sending and Tracking Statistics

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
        Ratio=Delivered/Requested.
      </td>
    </tr>

    <tr>
      <td>
        Invalid Email
      </td>

      <td>
        Number of failed delivery emails.
        Ratio=Invalid Email/Requested.
      </td>
    </tr>

    <tr>
      <td>
        Soft Bounce
      </td>

      <td>
        Number of emails that were returned after successful delivery. Ratio=Soft Bounce/Requested.
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
        Number of email opens. Each open is counted, without deduplication.
        Ratio=Open/Delivered.
      </td>
    </tr>

    <tr>
      <td>
        Unique Open
      </td>

      <td>
        The number of recipients who opened the email is counted, and one email only counts once.
        Ratio=Unique Open/Delivered.
      </td>
    </tr>

    <tr>
      <td>
        Click
      </td>

      <td>
        Number of email clicks. Each click is counted, without deduplication.
        Ratio=Click/Delivered.
      </td>
    </tr>

    <tr>
      <td>
        Unique Click
      </td>

      <td>
        The number of recipients who clicked a specific link in the email is counted, and one link in an email only counts once.
        Ratio=Unique Click/Delivered
      </td>
    </tr>

    <tr>
      <td>
        Report Spam
      </td>

      <td>
        Number of emails reported as spam.
        Ratio=Spam/Delivered.
      </td>
    </tr>

    <tr>
      <td>
        Unsubscribe
      </td>

      <td>
        Number of emails that users clicked to unsubscribe.
        Ratio=Unsubscribe/Delivered.
      </td>
    </tr>
  </tbody>
</Table>

<br />

> 📘 The example of tracking statistics
>
> You sent a mail to X and Y respectively and both were delivered.
> X has opened twice, and clicks the M link twice, and clicks the N link once.
> Y has opened 3 times, and click the M link once and click N link twice.
>
> * Open: 2 + 3 = 5
> * Unique Open: 1 + 1 = 2
> * Click: 2 + 1 + 1 + 2 = 6
> * Unique Click: 1 + 1 + 1 + 1 = 4

<br />

# &#x20;Dimensions of Statistics

Here are the dimensions by which you can perform filtering and screening.

| Dimension        | Description                                                                                                      |
| :--------------- | :--------------------------------------------------------------------------------------------------------------- |
| Email Type       | You can choose Trigger or Batch. The email type is decided by the type of API_USER that you used to send emails. |
| API_USER         | You can choose an API_USER that was used to send emails.                                                         |
| Label            | You can choose a label that was used to send emails.                                                             |
| Campagin         | You can choose a campaign that is in the process of sending or has been finished.                                |
| Receiving Domain | You can enter the mail provider's domain to search, such as gmail.com or yahoo.com.                              |
| Request Period   | It is the time period that you requested Aurora SendCloud to send emails. By default, it is the last 7 days .    |
| Send Tags        | The tags used for the API request.                                                                               |

# Categorys of Statistics

The sending and tracking statistics can be grouped by 4 categories that you can choose in the filter.

* Group by day (defualt)
* Group by week
* Group by month
* Group by receiving doamin

<br />
