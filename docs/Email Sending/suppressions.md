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
  robots: index
---
# Suppressions

The Suppression feature intelligently filters out problematic email addresses, improving overall deliverability and protecting sender reputation. The system automatically manages four core lists: Complaint List, Block List, Bounce List, and Unsubscribe List.

## Complaint List 🚩

**Trigger Conditions:**
- When a recipient marks an email as "spam" in their mail client
- Some mailbox providers (like QQ Mail and Gmail) provide complaints via FBL (Feedback Loop) reports in ARF format

**Handling Mechanism:**
- Reported addresses are automatically added to the Complaint List
- **Validity Period:** 180 days
- Sending to addresses on this list during the validity period returns the error: "Blacklist:complaint (worker:address in complaint list)"

**Management Suggestions:**
- 📅 Filter complaint data by time period
- 🗑️ Manual deletion is supported but **generally not recommended**
- ⚠️ Avoid sending to complained users to prevent further negative perception

## Block List 🚫

**Function:**
- Manually upload specific email addresses or domains to block
- Sends to blocked addresses return the error: "Blacklist: Block：(worker:address in block list)"

**List Data Includes:**
- 📧 Email Address / Domain
- 👤 Associated API_USER
- ⏰ Creation Time, Expiration Time

**Use Cases:**
- Proactively block invalid or high-risk addresses
- Implement custom sending policies

## Bounce List 📮

**Trigger Mechanism:**
- Recipient address does not exist (mailbox provider returns "address does not exist")
- System automatically blocks subsequent sends, returning: "Blacklist: Bounce(worker:address in bounce list)"

**Expiration Rules:**

| Mailbox Type | Expiration Policy | Max Duration |
|--------------|-------------------|--------------|
| **Tencent Mailboxes** 🐧 | 2^(n-1) days | 30 days |
| **Non-Tencent Mailboxes** 🌍 | 1h → 4h → 8h → 1d → 2^(n-1) days | 180 days |

*n = Number of times a "non-existent address" bounce is received for that mailbox.*

**Key Advantages:**
- 💰 Emails failing due to "Blacklist: Bounce" are **not charged**
- 📊 Effectively filters invalid addresses, helping maintain sending reputation
- ⚙️ Supports querying and setting specific addresses to not be blocked

## Unsubscribe List ✋

**Description:**
- Records the time and reason provided by users who unsubscribe
- Subsequent sends to unsubscribed addresses return the invalid reason: "unsubscribe"

**Unsubscribe Reason Categories:**
- 🚫 **I don't want to receive such mail anymore**
- ❓ **This is not my subscription**
- 🗑️ **This is spam**
- ⚠️ **This is a fraudulent email**

**Value:**
- Respects user choice and maintains brand reputation
- Avoids unnecessary sends, reducing costs

## Best Practices 💡

**Data Monitoring:**
- Regularly review list data to analyze sending quality
- Monitor complaint rates and optimize sending strategies accordingly

**Sending Optimization:**
- Use the Bounce List to clean your address database
- Respect unsubscribed users; avoid aggressive remarketing
- Handle complained addresses carefully to protect sender reputation

**List Management:**
- Use the custom Block List feature judiciously
- Understand the expiration policies for different lists
- Establish a proactive address hygiene process

## User Guide 🛠️

**Data Querying:**
- Filter entries by email address and time range
- View detailed trigger reasons and timestamps

**List Management:**
- Export list data for analysis
- Manually delete specific entries (use cautiously)