# Membership Management

**Phase:** 🔴 MVP

## Overview

Salesforce is the **single source of truth** for all member data. Member profiles are created and edited in Salesforce, and changes are synced outward to Slack, Microsoft Teams, and Okta.

## Member Profile Fields

| Field | Visibility | Editable By | Notes |
|---|---|---|---|
| Full Name (JP + EN) | 🏢 Org-visible | Member | |
| Nickname | 🏢 Org-visible | Member | |
| Org Email | 🏢 Org-visible | Admin only | Assigned after approval |
| Profile Photo | 🏢 Org-visible | Member | |
| Slack Account | 🏢 Org-visible | Member | |
| Department / Team | 🏢 Org-visible | Admin / HR workflow | Can belong to multiple departments |
| Role / Title | 🏢 Org-visible | Admin only | |
| Join Date | 🏢 Org-visible | Admin only | |
| Private Email | 🔒 Private | Member | |
| Phone Number | 🔒 Private | Member | |
| Address | 🔒 Private | Member | |
| Birthday | 🔒 Private | Member | |
| Emergency Contact | 🔒 Private | Member | |
| Bank Account Info | 🔒 Private | Member | For GMO Aozora payout (更新系 API) |
| Credit Card Token | 🔒 Private | Member (via payment UI) | Token only — never raw card data |
| Microsoft 365 Account | 👤 Admin only | Admin only | |
| License Assignments | 👤 Admin only | Admin only | Related list of all service licenses |
| Member Status | 👤 Admin only | Admin only | Active / Inactive |

!!! info "Visibility definitions"
    - **🏢 Org-visible** — visible to all logged-in Willen members (internal only, NOT public internet)
    - **🔒 Private** — visible to the member themselves + admins/committee
    - **👤 Admin only** — visible to committee/admins only

!!! warning "Gender field excluded"
    Gender is intentionally not collected. This is a deliberate decision for inclusivity.

!!! danger "PCI DSS — Card Data"
    Raw card numbers are **NEVER** stored in Salesforce. Only payment provider tokens (Pay.jp, Omise, Stripe) are stored. This keeps the system outside PCI DSS scope.

## Data Sync

Member profile changes in Salesforce propagate to:

- **Okta** — via SCIM provisioning or manual admin action
- **Slack** — via Okta SCIM or Slack API
- **Microsoft 365 / Teams** — via Okta SCIM or Microsoft Graph API

## Multi-Department Membership

Members can belong to **multiple departments** simultaneously. The `Department_Member__c` junction object handles these relationships.
