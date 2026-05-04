# HR Management

**Phase:** 🔴 MVP

## Overview

The HR Management module handles the organisational structure of Willen, including department management, member transfers, and the visual org tree.

## Features

- Organisation tree structure (Slack-style expandable/collapsible view)
- Department creation and management (by Super Admin / Committee)
- Member transfers between departments via approval workflow
- Multiple department membership supported
- Scheduled org chart updates (configurable: daily / weekly), with manual override

## Org Tree View

The member list displays as a **Slack-style org tree** with:

- Expandable/collapsible department nodes
- Member profile photos shown inline
- Active/inactive status indicators
- Click-through to member profile
- Search/filter within org tree

### Example Structure

```
🏢 特定非営利活動法人Willen
├── 📁 理事会 (Board)
│   ├── ⭐ 草間暁 (理事長)
│   └── ⭐ 龍見隆太郎 (理事長)
├── 📁 Department A
│   ├── ⭐ Manager Name
│   ├── 👤 Member Name
│   └── 👤 Member Name
│       └── 📁 Sub-department
│           └── 👤 Member Name
└── 📁 Department B
    ├── ⭐ Manager Name
    └── 👤 Member Name
```

## Org Chart Update Schedule

| Mode | Behaviour |
|---|---|
| **Scheduled (default)** | Org chart updates at configured interval (daily or weekly) after transfer approval |
| **Manual override** | Admin can force immediate update if needed |

## Member Transfer Workflow

```
Member or Manager submits transfer request
        ↓
Willen Committee notified
        ↓
Committee approves / rejects
        ↓
On approval: org chart updated on next schedule run
        ↓
Member notified
```

## Offboarding

!!! danger "Paper Form Required"
    Offboarding **cannot** be initiated online. Members must submit a **paper resignation form**.

| Step | Action | Type |
|---|---|---|
| 1 | Member submits paper resignation form to Committee | Manual (paper) |
| 2 | Admin receives paper form and triggers offboarding in Salesforce | Manual (admin) |
| 3 | Member status set to Inactive in Salesforce | 🤖 Automatic |
| 4 | Member record archived (10-year retention) | 🤖 Automatic |
| 5 | Willen Committee notified | 🤖 Automatic |
| 6 | Okta account deactivation | 👤 Manual (admin in Okta) |
| 7 | Slack workspace removal | 👤 Manual (admin) |
| 8 | Microsoft 365 license removal | 👤 Manual (admin) |
