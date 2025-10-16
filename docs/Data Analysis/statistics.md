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
<Table align={["left","left"]}>
  <thead>
    <tr>
      <th style={{ textAlign: "left" }}>
        Metric
      </th>

      <th style={{ textAlign: "left" }}>
        Description
      </th>
    </tr>
  </thead>

  <tbody>
    <tr>
      <td style={{ textAlign: "left" }}>
        Requested
      </td>

      <td style={{ textAlign: "left" }}>
        Number of requests received by Aurora SendCloud.
      </td>
    </tr>

    <tr>
      <td style={{ textAlign: "left" }}>
        Delivered
      </td>

      <td style={{ textAlign: "left" }}>
        Number of successfully delivered emails. 
        Ratio=Delivered/Requested.
      </td>
    </tr>

    <tr>
      <td style={{ textAlign: "left" }}>
        Invalid Email
      </td>

      <td style={{ textAlign: "left" }}>
        Number of failed delivery emails. 
        Ratio=Invalid Email/Requested.
      </td>
    </tr>

    <tr>
      <td style={{ textAlign: "left" }}>
        Soft Bounce
      </td>

      <td style={{ textAlign: "left" }}>
        Number of emails that were returned after successful delivery. Ratio=Soft Bounce/Requested.
      </td>
    </tr>

    <tr>
      <td style={{ textAlign: "left" }}>
        Billing Counts
      </td>

      <td style={{ textAlign: "left" }}>
        Number of emails with Delivered, Soft Bounce, Address Format Error, Address Does Not Exist, Spam, and Sender/Recipient Rejected.
      </td>
    </tr>

    <tr>
      <td style={{ textAlign: "left" }}>
        Open
      </td>

      <td style={{ textAlign: "left" }}>
        Number of email opens. 
        Ratio=Open/Delivered.
      </td>
    </tr>

    <tr>
      <td style={{ textAlign: "left" }}>
        Unique Open
      </td>

      <td style={{ textAlign: "left" }}>
        Number of recipients who opened the email. 
        Ratio=Unique Open/Delivered.
      </td>
    </tr>

    <tr>
      <td style={{ textAlign: "left" }}>
        Click
      </td>

      <td style={{ textAlign: "left" }}>
        Number of email clicks. 
        Ratio=Click/Delivered.
      </td>
    </tr>

    <tr>
      <td style={{ textAlign: "left" }}>
        Unique Click
      </td>

      <td style={{ textAlign: "left" }}>
        Number of recipients who clicked the email. 
        Ratio=Unique Click/Delivered
      </td>
    </tr>

    <tr>
      <td style={{ textAlign: "left" }}>
        Report Spam
      </td>

      <td style={{ textAlign: "left" }}>
        Number of emails reported as spam. 
        Ratio=Spam/Delivered.
      </td>
    </tr>

    <tr>
      <td style={{ textAlign: "left" }}>
        Unsubscribe
      </td>

      <td style={{ textAlign: "left" }}>
        Number of emails that users clicked to unsubscribe. 
        Ratio=Unsubscribe/Delivered.
      </td>
    </tr>
  </tbody>
</Table>

<br />
