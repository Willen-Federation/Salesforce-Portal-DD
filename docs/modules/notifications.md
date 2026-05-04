# Notification Service

**Phase:** 🔴 MVP

## Overview

A full internal mailing and messaging system with personalised delivery to each member's registered channels. Not a simple broadcast — every notification can be personalised per recipient.

## Features

| Feature | Detail |
|---|---|
| Announcement Sending | Organisation-wide or targeted group/department broadcast |
| Individual Sending | Personalised messages to specific members |
| Mail Merge | Auto-insert member name and personal info into message body |
| Excel Import | Upload Excel file with custom fields per member for bulk personalised sends |
| Custom Fields | Any Excel column can be embedded as a variable in the message body |
| File Attachments | Attach files such as Excel (.xlsx) and ZIP files |
| Department Notifications | Department-scoped notifications to department members only |
| Delivery Channels | Email, Slack, Microsoft Teams |

## Delivery Channels

```
Notification created in Salesforce
        ↓
    ┌─────────────────────────────────────┐
    │  Delivered to each member's         │
    │  individually registered contact:   │
    │                                     │
    │  📧 Private email address           │
    │  💬 Slack personal account          │
    │  🟦 Microsoft Teams account         │
    └─────────────────────────────────────┘
```

!!! important "Individual routing"
    Notifications are routed to each member's **own registered contact information**, not to channel webhooks. Members who don't check one channel will still receive via another.

## Mail Merge with Excel

This enables personalised bulk messaging powered by Excel data:

1. Admin creates notification template with variables: `{name}`, `{amount}`, `{due_date}`, etc.
2. Upload Excel file with one row per member containing their custom data
3. System merges data and sends personalised message to each member
4. Ideal for: fee notices, renewal reminders, event invitations with personal details

### Excel Template Example

| email | name | amount | due_date |
|---|---|---|---|
| member1@example.com | 田中太郎 | ¥5,000 | 2026-06-01 |
| member2@example.com | Taro Yamada | ¥3,000 | 2026-06-01 |

## Notification Types

| Type | Trigger |
|---|---|
| Announcement | Manual send by admin or dept manager |
| Event Reminder | Automated — X days before event |
| Fee Notice | Manual or scheduled (subscription renewal) |
| Workflow Update | Automated — on workflow status change |
| Welcome Message | Automated — on new member approval |
| System Alert | Automated — on system events |
