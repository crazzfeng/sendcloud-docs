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

### Trigger Conditions

* When a recipient marks an email as "spam" in their mail client
* Some mailbox providers (like QQ Mail and Gmail) provide complaints via FBL (Feedback Loop) reports in ARF format

### Example Scenarios

**Gmail User Example:**

* **Situation:** [abc@gmail.com](mailto:abc@gmail.com) receives your newsletter and clicks "Report spam"
* **Action:** Address automatically added to Complaint List
* **Duration:** 180 days validity period

**Corporate Email Example:**

* **Situation:** [aaa@company.com](mailto:aaa@company.com)'s IT admin reports bulk emails as spam
* **Action:** FBL report triggers automatic addition to Complaint List
* **Result:** All future sends to this domain flagged

### Handling Mechanism

* **Automatic Addition:** Reported addresses are automatically added to the Complaint List
* **Validity Period:** 180 days
* **Error Message:** Sending to addresses on this list returns "Blacklist:complaint (worker:address in complaint list)"

### Real-World Management Example

```
Scenario: Attempt to send to marketing@example.com (complained 45 days ago)
Result: Send blocked with error "Blacklist:complaint"
Status: Will remain blocked for 135 more days
```

### Management Best Practices

1. **Weekly Review:** Filter complaints from last 7 days to identify content/timing issues
2. **Segment Analysis:** Check if complaints cluster around specific campaigns
3. **List Hygiene:** Cross-reference with your CRM to update user preferences
4. **Manual Deletion:** Supported but generally not recommended

## Block List

### Function

* Manually upload specific email addresses or domains to block
* Sends to blocked addresses return error: "Blacklist: Block：(worker:address in block list)"

### Data Structure

| Field                | Description                |
| -------------------- | -------------------------- |
| Email Address/Domain | The blocked identifier     |
| Associated API_USER  | User who created the block |
| Creation Time        | When block was added       |
| Expiration Time      | When block expires         |

### Practical Implementation Examples

**Individual Address Blocking:**

<br />

```
Block: competitor@example.com
Reason: Prevent sensitive campaign data from reaching competitors
Expiration: Set to 365 days or permanent
Result: All sends automatically blocked
```

**Domain-Level Blocking:**

```
Block: @disposable-email.com
Reason: Block entire temporary email domain  
Result: All sends to *@disposable-email.com automatically blocked
Implementation: Upload single entry "@disposable-email.com"
```

**E-commerce Use Case:**

```
Scenario: E-commerce platform blocking test accounts
Action: Upload CSV with test@yourstore.com, demo@yourstore.com
Result: Prevents accidental marketing sends to internal test accounts
Management: Set 30-day expiration, renew as needed
```

### Use Cases

* Proactively block invalid or high-risk addresses
* Implement custom sending policies
* Prevent sends to competitors or test accounts
* Block temporary/disposable email domains

## Bounce List

### Trigger Mechanism

* Recipient address does not exist (mailbox provider returns "address does not exist")
* System automatically blocks subsequent sends
* Error returned: "Blacklist: Bounce(worker:address in bounce list)"

### Bounce Scenarios

**Immediate Hard Bounce Example:**

```
Send to: oldemployee@company.com
Provider Response: "550 5.1.1 User unknown"
System Action: Address immediately added to Bounce List
Next Attempt: Blocked with "Blacklist: Bounce" error
Cost: No charge for blocked attempts
```

**Gradual Retry Example (Non-Tencent):**

```
Address: typo-email@gmail.com
1st bounce: Wait 1 hour before retry
2nd bounce: Wait 4 hours  
3rd bounce: Wait 8 hours
4th bounce: Wait 1 day
5th bounce: Wait 2 days (continues doubling)
```

### Expiration Policies

| Mailbox Type              | Expiration Formula               | Maximum Duration |
| ------------------------- | -------------------------------- | ---------------- |
| **Tencent Mailboxes**     | 2^(n-1) days                     | 30 days          |
| **Non-Tencent Mailboxes** | 1h → 4h → 8h → 1d → 2^(n-1) days | 180 days         |

_n = Number of times a "non-existent address" bounce is received_

### Management Example

```
Query: Check bounce status for customer@startup.com
Result: "Bounced 3 times, blocked for 8 more hours"
Recommended Action: 
1. Verify address with customer via alternative method
2. Consider manual override if confirmed valid
3. Update customer record with correct address
```

### Key Benefits

* **Cost Savings:** Emails failing due to "Blacklist: Bounce" are not charged
* **Reputation Protection:** Automatically filters invalid addresses
* **Smart Retry:** Exponential backoff prevents hammering invalid addresses
* **Manual Override:** Supports querying and setting specific addresses to not be blocked

## Unsubscribe List

### Function

* Records time and reason when users unsubscribe
* Subsequent sends return error: "unsubscribe"
* Maintains compliance with email regulations

### Unsubscribe Scenarios

**Standard Newsletter Unsubscribe:**

```
User: newsletter-subscriber@email.com
Action: Clicks unsubscribe link in email footer
Reason Selected: "I don't want to receive such mail anymore"
System Response: Added to Unsubscribe List with timestamp
Future Sends: Automatically blocked
```

**Spam Report Unsubscribe:**

```
User: customer@domain.com  
Action: Marks email as spam AND unsubscribes
Reason: "This is spam"
Impact: Higher priority flag for content review
Recommended Response: Immediate campaign analysis
```

### Unsubscribe Reason Categories

| Reason                                          | Interpretation           | Action Required               |
| ----------------------------------------------- | ------------------------ | ----------------------------- |
| **"I don't want to receive such mail anymore"** | Normal unsubscribe       | Standard processing           |
| **"This is not my subscription"**               | List quality issue       | Review list sources           |
| **"This is spam"**                              | Content/sending issue    | Review content quality        |
| **"This is a fraudulent email"**                | Serious compliance issue | Investigate sending practices |

### Analysis Example

```
Weekly Unsubscribe Report:
- "Don't want mail": 85% (normal unsubscribes)
- "Not my subscription": 10% (investigate list sources)
- "This is spam": 4% (review content quality)  
- "Fraudulent": 1% (immediate investigation needed)

Action Items:
1. Review list acquisition methods for "not my subscription"
2. A/B test subject lines to reduce "spam" flags
3. Investigate any "fraudulent" reports immediately
```

## Best Practices

### Daily Monitoring Dashboard

```
Daily Suppression Report Example:
┌─────────────────────────────────────┐
│ New Complaints: 12 (0.08% of sends) │
│ New Bounces: 45 (0.3% of sends)     │
│ New Unsubscribes: 28 (0.19% sends)  │
│ Blocked Attempts: 156 emails        │
│ Cost Savings: $15.60                │
└─────────────────────────────────────┘
```

### Monthly Optimization Process

1. **Data Export:** Download all suppression lists
2. **Database Cleanup:** Remove bounced addresses from main database
3. **Complaint Analysis:** Review complaint reasons and timing
4. **Content Optimization:** Adjust campaigns based on suppression patterns
5. **Re-engagement Strategy:** Plan win-back campaigns for unsubscribed users

### Weekly Hygiene Workflow

```
Monday: Download weekend suppressions
Tuesday: Cross-reference with CRM data
Wednesday: Update customer preferences  
Thursday: Document patterns for optimization
Friday: Set calendar reminders for review dates
```

## User Management Guide

### Data Querying Examples

**Find Recent Complaints:**

```
Filter Settings:
- List Type: Complaint
- Date Range: Last 30 days
- Sort: Most recent first

Use Case: Identify recent content issues
Expected Results: List of complained addresses with timestamps
```

**Check Specific Customer Status:**

```
Search Query: "customer@important-client.com"
Results Display:
- Current Status: Bounced/Complained/Unsubscribed/Blocked
- Reason: Specific trigger reason
- Date Added: When suppression occurred
- Expiration: When block will lift (if applicable)
```

### Export and Analysis Use Cases

**Marketing Analysis Exports:**

* **Complaint Data:** Export to identify problematic subject lines and content
* **Bounce Data:** Export to clean master email database and improve list quality
* **Unsubscribe Reasons:** Export to improve email content strategy and timing

**Compliance Reporting:**

* Generate monthly suppression reports for stakeholders
* Track suppression trends for deliverability optimization
* Document suppression management for audit purposes

### Manual Management Guidelines

**When to Delete Entries:**

* **Complaints:** Generally avoid manual deletion
* **Bounces:** Consider deletion only after address verification
* **Blocks:** Regular review and cleanup of expired blocks
* **Unsubscribes:** Respect user choice, avoid deletion

**Setting Custom Expiration:**

```
Example: VIP Customer Recovery
Scenario: Important client's email bounced due to temporary server issue
Action: Override bounce block after confirming resolution
Process: Manual deletion from bounce list + verification
Follow-up: Monitor delivery success for next few sends
```
