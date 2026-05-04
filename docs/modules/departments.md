# Organisation & Department Pages

**Phase:** 🟡 Phase 2

## Overview

Each department has its own page within the portal, managed by the Department Manager. The organisation structure is visualised as a Slack-style expandable tree.

## Features

| Feature | Detail |
|---|---|
| Organisation Tree | Slack-style expandable/collapsible view of entire org |
| Department Info | Description, mission, manager contact info |
| Tools & Links | Department-specific links to internal/external tools |
| Department Resources | Department-scoped documents and files |
| Members List (Tree) | Hierarchical list with avatars and status indicators |
| Announcements | Department-specific news and updates |
| Department Notifications | Send personalised notifications to dept members |
| Auto-Invitations | Auto-invite new members to Slack channels and Teams via Okta SCIM |
| Department Creation | Super Admin / Committee only |

## Org Tree Features

- **Expandable/collapsible** — click to expand/collapse like Slack sidebar
- **Member avatars** — profile photos shown inline
- **Status indicators** — active/inactive visible at a glance
- **Click-through** — click any member → view their profile
- **Search** — filter/search members within the tree

## Department Notification with Excel

Department managers can send personalised notifications to their team using Excel import:

1. Prepare Excel with member-specific data columns
2. Upload to notification tool
3. System inserts personalised fields into each member's message
4. Delivered via email, Slack, and Teams

## Auto-Invitation

When a new member joins a department:

```
Member joins department (approved in Salesforce)
        ↓
Auto-invite triggered
        ↓
    Via Okta SCIM (preferred)
    OR
    Via Salesforce API (if Slack/Microsoft API available)
        ↓
Member added to department Slack channel + Teams group
```
