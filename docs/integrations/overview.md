# Integrations

## Overview

Salesforce is the **central hub**. All integrations flow outward from Salesforce — not inward.

## Integration Map

| System | Purpose | Method | Notes |
|---|---|---|---|
| **Salesforce Nonprofit Edition** | Core platform / central hub | Native | Primary system of record |
| **Okta** | SSO + license management | SCIM or Salesforce API | Manual provisioning; portal handles request/tracking only |
| **Slack** | Notifications, dept invitations | Okta SCIM or Slack API | |
| **Microsoft 365 / Teams** | Notifications, license mgmt, dept invitations | Okta SCIM or Microsoft Graph API | |
| **Pay.jp** | Domestic Visa/Mastercard | REST API + tokenisation | Rule a |
| **Omise** | Domestic JCB, Amex, bank, convenience | REST API + tokenisation | Rule b |
| **Stripe** | International USD/EUR payments | REST API + tokenisation | Rule c |
| **GMO Aozora Net Bank** | Bank transfers, virtual accounts, webhooks | REST API (参照系 + 更新系) | See [GMO Aozora](../payments/gmo-aozora.md) |
| **Apple Wallet** | Event ticket passes | `.pkpass` format | Phase 2 |
| **Google Wallet** | Event ticket passes | Google Pay Passes API | Phase 2 |
| **WordPress (willen.jp)** | Existing public website | TBD | API integration or standalone |

## Okta Integration Detail

!!! important "Okta Dashboard remains separate"
    The portal does NOT replace the Okta Dashboard. It only adds a request/approval layer on top.

```
Portal (request) → Salesforce (record) → Committee (approve) → Admin (action in Okta)
```

Okta SCIM is used for automated provisioning where possible (Slack, Teams workspace memberships after approval).

## Slack / Teams Integration

- **Notifications:** Sent to member's personal Slack/Teams account
- **Department invitations:** Auto-added to department workspace/channel on department join
- **Method:** Okta SCIM provisioning (preferred) or direct API

## No AI Integration

!!! info
    OpenAI and other generative AI services are **not integrated** into the portal system itself. OpenAI accounts are managed as licenses within the [License Management](../modules/licenses.md) module only.
