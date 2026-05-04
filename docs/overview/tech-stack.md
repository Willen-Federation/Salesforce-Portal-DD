# Technology Stack

## Core Platform

| Layer | Technology | Notes |
|---|---|---|
| **Core CRM** | Salesforce Nonprofit Edition | Central hub and system of record |
| **Portal Layer** | Salesforce Experience Cloud (Build Your Own) | Fully custom LWC-based portal |
| **Backend Logic** | Apex | Server-side business logic, integrations |
| **Frontend** | Lightning Web Components (LWC) | Custom UI components |
| **Domain (Current)** | `willen.mysite.com` | Temporary |
| **Domain (Target)** | TBD — e.g. `portal.willen.jp` | To be configured |
| **Languages** | Japanese + English | Bilingual throughout |

## Mobile

| Platform | Type |
|---|---|
| **Web** | Responsive web (mobile-optimised) |
| **iOS** | Native app |
| **Android** | Native app |

## Payment Stack

| Provider | Usage | Region |
|---|---|---|
| **Pay.jp** | Visa, Mastercard | Domestic (JPY) |
| **Omise** | JCB, Amex, bank transfer, convenience store | Domestic (JPY) |
| **Stripe** | International cards | International (USD/EUR) |
| **GMO Aozora Net Bank API** | Bank-to-bank transfers, virtual accounts, payouts | JPY |

## Integrations

| System | Purpose |
|---|---|
| **Okta** | SSO, identity management, SCIM provisioning |
| **Slack** | Notifications, workspace invitations |
| **Microsoft 365 / Teams** | Notifications, license management |
| **Apple Wallet** | Event ticket passes (.pkpass) |
| **Google Wallet** | Event ticket passes (Google Pay Passes API) |
| **WordPress (willen.jp)** | Existing public website |

## Architecture Notes

!!! note "Salesforce as Central Hub"
    Salesforce is the **single source of truth** for all member data. Changes in Salesforce propagate outward to Slack, Teams, and Okta — not the other way around.

!!! warning "Okta Dashboard Separation"
    The portal does **NOT** include an app launcher or SSO links. Okta Dashboard remains the execution layer for service provisioning. The portal only handles request and approval workflows.
