---
title: Suppressions
excerpt: >-
  The Suppression feature intelligently filters out problematic email addresses,
  improving overall deliverability and protecting sender reputation. 
deprecated: false
hidden: false
link:
  new_tab: false
metadata:
  title: 'Email Suppression Lists: Boost Deliverability & Sender Reputation'
  description: >-
    Manage email suppression lists effectively with complaint, bounce, block,
    and unsubscribe handling. Improve deliverability and protect sender
    reputation automatically.
  keywords:
    - email suppression
    - email deliverability
    - bounce management
    - complaint handling
  robots: index
---
The system automatically manages four core lists: Complaint List, Block List, Bounce List, and Unsubscribe List.

## Complaint List

**Trigger Conditions:**

* When a recipient marks an email as "spam" in their mail client
* Some mailbox providers (like QQ Mail and Gmail) provide complaints via FBL (Feedback Loop) reports in ARF format

**Example Scenarios:**
* **Gmail User**: John@gmail.com receives your newsletter and clicks "Report spam" → Address automatically added to Complaint List
* **Corporate Email**: sarah.jones@company.com's IT admin reports bulk emails as spam → FBL report triggers automatic addition

**Handling Mechanism:**

* Reported addresses are automatically added to the Complaint List
* **Validity Period:** 180 days
* Sending to addresses on this list during the validity period returns the error: "Blacklist:complaint (worker:address in complaint list)"

**Real-World Example:**
```
Attempt to send to: marketing@example.com (complained 45 days ago)
Result: Send blocked with error "Blacklist:complaint (worker:address in complaint list)"
Status: Will remain blocked for 135 more days
```

**Management Suggestions:**

* Filter complaint data by time period
* Manual deletion is supported but **generally not recommended**
* Avoid sending to complained users to prevent further negative perception

**Example Management Workflow:**
1. **Weekly Review**: Filter complaints from last 7 days to identify content/timing issues
2. **Segment Analysis**: Check if complaints cluster around specific campaigns
3. **List Hygiene**: Cross-reference with your CRM to update user preferences

## Block List

**Function:**

* Manually upload specific email addresses or domains to block
* Sends to blocked addresses return the error: "Blacklist: Block：(worker:address in block list)"

**List Data Includes:**

* Email Address / Domain
* Associated API_USER
* Creation Time, Expiration Time

**Practical Examples:**

**Individual Address Blocking:**
```
Block: competitor-research@rival.com
Reason: Prevent sensitive campaign data from reaching competitors
Expiration: Set to 365 days or permanent
```

**Domain-Level Blocking:**
```
Block: @disposable-email.com
Reason: Block entire temporary email domain
Result: All sends to *@disposable-email.com automatically blocked
```

**Use Cases:**

* Proactively block invalid or high-risk addresses
* Implement custom sending policies

**Example Implementation:**
```
Scenario: E-commerce platform blocking test accounts
Action: Upload CSV with test@yourstore.com, demo@yourstore.com
Result: Prevents accidental marketing sends to internal test accounts
```

## Bounce List

**Trigger Mechanism:**

* Recipient address does not exist (mailbox provider returns "address does not exist")
* System automatically blocks subsequent sends, returning: "Blacklist: Bounce(worker:address in bounce list)"

**Real-World Bounce Examples:**

**Immediate Bounce:**
```
Send to: oldemployee@company.com
Response: "550 5.1.1 User unknown"
Action: Address immediately added to Bounce List
Next attempt: Blocked with "Blacklist: Bounce" error
```

**Gradual Escalation Example (Non-Tencent):**
```
typo-email@gmail.com bounces:
1st bounce: Wait 1 hour before retry
2nd bounce: Wait 4 hours  
3rd bounce: Wait 8 hours
4th bounce: Wait 1 day
5th bounce: Wait 2 days (continues doubling up to 180 days)
```

**Expiration Rules:**

| Mailbox Type              | Expiration Policy                | Max Duration |
| ------------------------- | -------------------------------- | ------------ |
| **Tencent Mailboxes**     | 2^(n-1) days                     | 30 days      |
| **Non-Tencent Mailboxes** | 1h → 4h → 8h → 1d → 2^(n-1) days | 180 days     |

_n = Number of times a "non-existent address" bounce is received for that mailbox._

**Key Advantages:**

* Emails failing due to "Blacklist: Bounce" are **not charged**
* Effectively filters invalid addresses, helping maintain sending reputation
* Supports querying and setting specific addresses to not be blocked

**Management Example:**
```
Query: Check bounce status for customer@startup.com
Result: "Bounced 3 times, blocked for 8 more hours"
Action: Verify with customer, potentially override block if confirmed valid
```

## Unsubscribe List

**Description:**

* Records the time and reason provided by users who unsubscribe
* Subsequent sends to unsubscribed addresses return the invalid reason: "unsubscribe"

**Example Unsubscribe Scenarios:**

**Standard Unsubscribe:**
```
User: newsletter-subscriber@email.com
Action: Clicks unsubscribe link in email footer
Reason Selected: "I don't want to receive such mail anymore"
Result: Added to Unsubscribe List with timestamp and reason
```

**Spam Report Unsubscribe:**
```
User: customer@domain.com  
Action: Marks email as spam and unsubscribes
Reason: "This is spam"
Impact: Higher priority flag for content review
```

**Unsubscribe Reason Categories:**

* **I don't want to receive such mail anymore**
* **This is not my subscription** 
* **This is spam**
* **This is a fraudulent email**

**Management Examples:**

**Reason Analysis:**
```
Weekly Report:
- "Don't want mail": 85% (normal unsubscribes)
- "Not my subscription": 10% (check list sources)
- "This is spam": 4% (review content quality)
- "Fraudulent": 1% (investigate sending practices)
```

**Value:**

* Respects user choice and maintains brand reputation
* Avoids unnecessary sends, reducing costs

## 💡Best Practices

**Data Monitoring:**

* Regularly review list data to analyze sending quality
* Monitor complaint rates and optimize sending strategies accordingly

**Example Monitoring Dashboard:**
```
Daily Suppression Report:
- New Complaints: 12 (0.08% of sends)
- New Bounces: 45 (0.3% of sends)  
- New Unsubscribes: 28 (0.19% of sends)
- Blocked Attempts Prevented: 156 emails
```

**Sending Optimization:**

* Use the Bounce List to clean your address database
* Respect unsubscribed users; avoid aggressive remarketing
* Handle complained addresses carefully to protect sender reputation

**Example Optimization Process:**
1. **Monthly Cleanup**: Export bounce list, remove addresses from main database
2. **Complaint Analysis**: Review complaint reasons, adjust content/frequency
3. **Re-engagement**: Create win-back campaigns for unsubscribed users (with proper opt-in)

**List Management:**

* Use the custom Block List feature judiciously
* Understand the expiration policies for different lists
* Establish a proactive address hygiene process

**Example Hygiene Workflow:**
```
Weekly Process:
1. Download new suppressions from all lists
2. Cross-reference with CRM data
3. Update customer preferences where applicable
4. Document patterns for campaign optimization
5. Set calendar reminders for manual review dates
```

## User Guide

**Data Querying:**

* Filter entries by email address and time range
* View detailed trigger reasons and timestamps

**Example Query Scenarios:**
```
Query 1: Find all complaints from last 30 days
Filter: List=Complaint, Date Range=2024-01-15 to 2024-02-15
Use Case: Identify recent content issues

Query 2: Check specific customer status  
Search: "customer@important-client.com"
Result: Shows if blocked, reason, and expiration date
```

**List Management:**

* Export list data for analysis
* Manually delete specific entries (use cautiously)

**Example Export Use Cases:**
```
Marketing Analysis:
- Export complaint data → Identify problematic subject lines
- Export bounce data → Clean master email database  
- Export unsubscribe reasons → Improve email content strategy

Compliance Reporting:
- Generate monthly suppression reports for stakeholders
- Track suppression trends for deliverability optimization
```