---
title: IP Access
excerpt: IP access control is a key feature that enhances account security.
deprecated: false
hidden: false
metadata:
  robots: index
---
# IP Access 

IP access control is a key feature that enhances account security. Once enabled, only IP addresses or IP ranges that you explicitly whitelist are allowed to call Aurora SendCloud's email sending API or send email via the SMTP service. All requests from non-whitelisted IP addresses are automatically blocked, effectively preventing unauthorized access and resource abuse caused by API key leaks.

Configuring IP Whitelisting

To enable this feature:

Log in to the Aurora SendCloud console and go to the "IP Access Control" page under "Security Settings" or "Account Settings."

Switch the feature to "On."

Adding an IP Whitelist:

Click the "Add IP" button in the IP Whitelist.
In the input box, you can add:
You can enter only one IP/IP range/IP segment in each row.
Format of single IP: xxx.xxx.xxx.xxx, e.g., 220.181.12.241.
Format of IP range: xxx.xxx.xxx.xxx-xxx.xxx.xxx.xxx, e.g., 220.181.12.241-220.181.12.255.
Format of IP segment: xxx.xxx.xxx.xxx/N, e.g., 220.181.12.0/24.
Internal IP addresses are not allowed, including 192.168.0.0-192.168.255.255, 172.16.0.0-172.16.0.0-172.31.255.255, 10.0.0.0-10.255.255.255.

Click Confirm to save. You can add multiple IP entries at once.

Important Note:

Immediate Effect: Rules take effect immediately after they are added or modified. Before enabling this feature, please ensure that all legitimate sending server IP addresses (such as those used in production and test environments) have been whitelisted. Failure to do so may result in service interruption due to IP blocking.

Caution: To avoid locking yourself out, it is recommended to add all necessary IP addresses and confirm that they are correct before turning on the main switch.

Viewing Request IP Logs and Blocking History

To help you manage and troubleshoot issues, Aurora SendCloud records API request logs for the past 30 days.

On the "IP Access Control" page, you can find the "Request IP History" or "Blocking History" tabs.
On this page, you can view:

Request IP Address: The source IP address that initiated API or SMTP requests.

Last Request Time: The time this IP last initiated a request.

Interception Count: The number of times this IP was blocked due to not being on the whitelist after IP control was enabled.

Use Scenarios:

Security Audit: By checking the request IP list, you can identify unknown or suspicious IP addresses attempting to call your API, which may indicate an API key leak.

Troubleshooting: If your sending service receives a "Request Rejected" error, verify here that the sending server's IP address has been correctly added to the whitelist and identify the issue based on the interception log.

Best Practices:

Principle of Least Privilege: Only add the minimum number of IP addresses necessary for your business to the whitelist to minimize security risks.

Regular Review: Regularly review the request IP history and interception log, and promptly remove unused IP addresses.
​​Pre-configuration:​​ Before you plan to enable this feature, complete the whitelist configuration and testing to ensure business continuity.
