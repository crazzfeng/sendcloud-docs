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

<Tabs>
  <Tab title="Configuration">
    ## Getting Started

    <Cards columns="2">
      <Card title="Enable IP Access Control" icon="shield-alt">
        1. Log in to the Aurora SendCloud console
        2. Navigate to "IP Access Control" under "Security Settings"
        3. Switch the feature to "On"
      </Card>
      <Card title="Add IP Addresses" icon="plus-circle">
        1. Click the "Add IP" button in the IP Allowlist section
        2. Enter IP addresses in the supported formats
        3. Click "Confirm" to save
      </Card>
    </Cards>

    ## Supported IP Address Formats

    <Accordion title="IP Address Format Examples" icon="list">
      You can add IP addresses using the following formats (one entry per row):

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
    </Accordion>

    ## Important Warnings

    <Callout icon="🚧">
      **Immediate Effect**: Rules take effect immediately after they are added or modified. Before enabling this feature, ensure that all legitimate sending server IP addresses (including those used in production and test environments) have been added to the allowlist. Failure to do so may result in service interruption due to IP blocking.

      **Caution**: To avoid locking yourself out, add all necessary IP addresses and confirm they are correct before turning on the main switch.
    </Callout>
  </Tab>

  <Tab title="Monitoring & Logs">
    ## Request IP Logs and Blocking History

    Aurora SendCloud records API request logs for the past 30 days to help you manage and troubleshoot issues.

    <Cards columns="1">
      <Card title="Access Monitoring Dashboard" icon="chart-line">
        On the "IP Access Control" page, navigate to the "Request IP History" or "Blocking History" tabs to view detailed logs and analytics.
      </Card>
    </Cards>

    <Accordion title="Available Log Information" icon="database">
      <Columns layout="auto">
        <Column>
          **Request IP Address**
          
          The source IP address that initiated API or SMTP requests
        </Column>
        <Column>
          **Last Request Time**
          
          The timestamp when this IP last initiated a request
        </Column>
        <Column>
          **Interception Count**
          
          The number of times this IP was blocked due to not being on the allowlist
        </Column>
      </Columns>
    </Accordion>

    ## Common Use Cases

    <Cards columns="2">
      <Card title="Security Audit" icon="search">
        Check the request IP list to identify unknown or suspicious IP addresses attempting to call your API, which may indicate an API key leak.
      </Card>
      <Card title="Troubleshooting" icon="tools">
        If your sending service receives a "Request Rejected" error, verify that the sending server's IP address has been correctly added to the allowlist.
      </Card>
    </Cards>
  </Tab>

  <Tab title="Best Practices">
    ## Security Recommendations

    <Cards columns="1">
      <Card title="Principle of Least Privilege" icon="lock">
        Only add the minimum number of IP addresses necessary for your business to the allowlist to minimize security risks.
      </Card>
      <Card title="Regular Review" icon="sync-alt">
        Regularly review the request IP history and interception log, and promptly remove unused IP addresses from your allowlist.
      </Card>
      <Card title="Pre-configuration Testing" icon="check-circle">
        Before enabling this feature, complete the allowlist configuration and testing to ensure business continuity and avoid service interruptions.
      </Card>
    </Cards>

    <Accordion title="Implementation Checklist" icon="clipboard-check">
      - [ ] Identify all production and test environment IP addresses
      - [ ] Add all necessary IP addresses to the allowlist
      - [ ] Test API connectivity from all approved IP addresses
      - [ ] Enable IP access control
      - [ ] Monitor logs for any unexpected blocks
      - [ ] Set up regular review schedule for IP allowlist
    </Accordion>
  </Tab>
</Tabs>