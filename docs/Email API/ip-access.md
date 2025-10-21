---
title: IP Access
excerpt: IP access control is a key feature that enhances account security.
deprecated: false
hidden: false
link:
  new_tab: false
metadata:
  robots: index
---
# IP Access

IP access control is a key security feature that enhances account protection. Once enabled, only IP addresses or IP ranges that you explicitly add to the allowlist can call Aurora SendCloud's email sending API or send emails via the SMTP service. All requests from non-allowed IP addresses are automatically blocked, effectively preventing unauthorized access and resource abuse caused by API key leaks.

## Configuring IP Allowlisting

To enable this feature:

1. Log in to the Aurora SendCloud console and navigate to the "IP Access Control" page under "Security Settings" or "Account Settings."

2. Switch the feature to "On."

### Adding an IP Allowlist

1. Click the "Add IP" button in the IP Allowlist section.

2. In the input box, you can add IP addresses using the following formats (one entry per row):

<Callout icon="👍">
  **Single IP**: xxx.xxx.xxx.xxx (e.g., 220.181.12.241)

  **IP Range**: xxx.xxx.xxx.xxx-xxx.xxx.xxx.xxx (e.g., 220.181.12.241-220.181.12.255)

  **IP Segment**: xxx.xxx.xxx.xxx/N (e.g., 220.181.12.0/24)
</Callout>

**Note**: Internal IP addresses are not allowed, including:

<Callout icon="❗️">
  * 192.168.0.0-192.168.255.255
  * 172.16.0.0-172.31.255.255
  * 10.0.0.0-10.255.255.255
</Callout>

3. Click "Confirm" to save. You can add multiple IP entries at once.

### Important Notes

<Callout icon="🚧">
  **Immediate Effect**: Rules take effect immediately after they are added or modified. Before enabling this feature, ensure that all legitimate sending server IP addresses (including those used in production and test environments) have been added to the allowlist. Failure to do so may result in service interruption due to IP blocking.

  **Caution**: To avoid locking yourself out, add all necessary IP addresses and confirm they are correct before turning on the main switch.
</Callout>

## Viewing Request IP Logs and Blocking History

Aurora SendCloud records API request logs for the past 30 days to help you manage and troubleshoot issues.

On the "IP Access Control" page, you can find the "Request IP History" or "Blocking History" tabs, where you can view:

* **Request IP Address**: The source IP address that initiated API or SMTP requests
* **Last Request Time**: The timestamp when this IP last initiated a request
* **Interception Count**: The number of times this IP was blocked due to not being on the allowlist after IP control was enabled

### Use Cases

**Security Audit**: By checking the request IP list, you can identify unknown or suspicious IP addresses attempting to call your API, which may indicate an API key leak.

**Troubleshooting**: If your sending service receives a "Request Rejected" error, verify that the sending server's IP address has been correctly added to the allowlist and identify issues based on the interception log.

## Best Practices

* **Principle of Least Privilege**: Only add the minimum number of IP addresses necessary for your business to the allowlist to minimize security risks
* **Regular Review**: Regularly review the request IP history and interception log, and promptly remove unused IP addresses
* **Pre-configuration**: Before enabling this feature, complete the allowlist configuration and testing to ensure business continuity
