---
title: Query Address List Task
excerpt: >-
  Learn how to query the status and details of an address list email task using
  our API.
api:
  file: deliverlies.yaml
  operationId: query-task
hidden: false
link:
  new_tab: false
---
# Query Address List Task

This guide explains how to query the status and details of an address list email task. You can retrieve comprehensive information about your email tasks, including their current status, progress, and associated metadata.

## Overview

When you submit an email task to an address list, you can monitor its progress and retrieve detailed information using our query endpoints. This allows you to track the success of your email campaigns and troubleshoot any issues that may arise.

## What You Can Query

When querying an address list task, you can retrieve the following information:

<Cards columns="2">
  <Card title="Task Status" icon="info-circle">
    Current status of the email task (pending, processing, completed, failed)
  </Card>
  <Card title="Progress Metrics" icon="chart-line">
    Number of emails sent, delivered, bounced, and failed
  </Card>
  <Card title="Task Details" icon="list-ul">
    Creation date, completion date, and task configuration
  </Card>
  <Card title="Error Information" icon="exclamation-triangle">
    Details about any errors or issues encountered during processing
  </Card>
</Cards>

## Query Parameters

You can use various parameters to filter and customize your query results:

- **Task ID**: Specify the unique identifier of the email task
- **Date Range**: Filter tasks by creation or completion date
- **Status**: Filter by specific task statuses
- **Address List**: Filter by specific address lists

## Response Format

The API returns detailed information about your email tasks in a structured format, including:

<Accordion title="Task Information" icon="envelope">
- Task ID and name
- Associated address list details
- Current status and progress
- Timestamps for creation and completion
- Email content summary
</Accordion>

<Accordion title="Performance Metrics" icon="analytics">
- Total recipients processed
- Successful deliveries
- Bounce rate and types
- Open and click-through rates (if tracking enabled)
</Accordion>

<Accordion title="Error Details" icon="bug">
- Error codes and descriptions
- Failed recipient addresses
- Retry attempts and outcomes
- Troubleshooting recommendations
</Accordion>

## Best Practices

<Columns layout="auto">
  <Column>
    ### Monitoring Tasks
    - Check task status regularly for large campaigns
    - Set up automated monitoring for critical email tasks
    - Review error details to improve future campaigns
  </Column>
  
  <Column>
    ### Performance Optimization
    - Query tasks in batches to avoid rate limits
    - Use appropriate date ranges to limit response size
    - Cache frequently accessed task information
  </Column>
</Columns>

## Common Use Cases

Understanding task status and details is essential for:

1. **Campaign Monitoring**: Track the progress of ongoing email campaigns
2. **Performance Analysis**: Analyze delivery rates and engagement metrics
3. **Error Troubleshooting**: Identify and resolve issues with email delivery
4. **Compliance Reporting**: Generate reports for audit and compliance purposes
5. **Integration Management**: Synchronize task status with external systems

## Next Steps

Once you've mastered querying address list tasks, you can explore advanced features like:

- Setting up webhook notifications for task completion
- Implementing automated retry logic for failed tasks
- Creating custom dashboards for campaign monitoring
- Integrating task data with analytics platforms