# Module Overview

The Willen Member Portal is composed of **14 modules** across three development phases.

## Module List

| # | Module | Phase | Description |
|---|---|---|---|
| 1 | [Membership Management](membership.md) | 🔴 MVP | Member profiles, Salesforce as source of truth, synced to Slack/Teams/Okta |
| 2 | [HR Management](hr.md) | 🔴 MVP | Org structure, department management, member transfers, org tree |
| 3 | [Application Forms](applications.md) | 🔴 MVP | New member applications, fee collection, 5-outcome approval workflow |
| 4 | [Event Registration](events.md) | 🟡 Phase 2 | Event management with QR codes, Apple/Google Wallet passes |
| 5 | [Resource Sharing](resources.md) | 🟡 Phase 2 | Documents, templates, tools, knowledge base, files with versioning |
| 6 | [Ordering & Fee Collection](ordering.md) | 🟡 Phase 2 | C-to-B payment collection for OSS fees, software agent fees, donations |
| 7 | Donations & Grants | 🟡 Phase 2 | Domestic and international donations (included in Ordering module) |
| 8 | Payment Integration | 🔴 MVP | Pay.jp, Omise, Stripe, GMO Aozora — see [Payments](../payments/overview.md) |
| 9 | Workflow & Approvals | 🔴 MVP | Request and approval flows — see [Workflows](../workflows/overview.md) |
| 10 | [Notification Service](notifications.md) | 🔴 MVP | Multi-channel personalised notifications with mail merge |
| 11 | [Org & Department Pages](departments.md) | 🟡 Phase 2 | Org structure, department info, tools, announcements |
| 12 | [Case Management & Help Center](cases.md) | 🟡 Phase 2 | Private member support cases, FAQ, knowledge base |
| 13 | [License Management](licenses.md) | 🔴 MVP | Track and request service licenses (Okta, Microsoft, Slack, OpenAI etc.) |
| 14 | [Form Builder](form-builder.md) | 🟢 Phase 3 | Dynamic form generator for custom fee and info collection |

## Phase Summary

=== "🔴 MVP"
    - Membership Management
    - HR Management
    - Application Forms + Workflow
    - License Management
    - Notification Service
    - Payment Integration (Pay.jp, Omise, GMO Aozora setup)
    - Annual Membership Fee / Subscriptions

=== "🟡 Phase 2"
    - Event Registration + QR + Wallet passes
    - Department Pages + Org tree
    - Resource Sharing
    - Help Center + Cases
    - Ordering & Donations
    - Stripe (International payments)

=== "🟢 Phase 3"
    - Form Builder
    - Native Mobile App (iOS & Android)
    - Advanced integrations
    - Custom domain migration
