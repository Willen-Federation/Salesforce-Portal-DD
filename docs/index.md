# Willen Member Portal — Design Document

<span class="confidential">CONFIDENTIAL</span> &nbsp; Version 1.0 — Draft &nbsp; 2026

---

> **Empower Every Person and Every Organization to Achieve More**
>
> — 特定非営利活動法人Willen

---

## What is this?

This is the official System Design Document (DD) for the **Willen Member Portal** — a comprehensive digital platform built on **Salesforce Nonprofit Edition**, designed to serve as the central hub for all organisational operations of 特定非営利活動法人Willen.

## Two Interfaces, One Platform

| Interface | Brand | Audience |
|---|---|---|
| **Internal Portal** | Willen | Current members and committee |
| **External Portal** | Willen Federation | New applicants, donors, and international sponsors |

## Key Features at a Glance

=== "Membership & HR"
    - Member profiles with bilingual (JP/EN) support
    - Org tree view (Slack-style)
    - Department management
    - Member transfers and HR workflows

=== "Applications & Onboarding"
    - Online application forms with payment
    - 5-outcome approval workflow
    - Auto-provisioning via Okta/Slack

=== "Payments"
    - **Pay.jp** — Domestic Visa/Mastercard
    - **Omise** — JCB, Amex, bank transfer, convenience store
    - **Stripe** — International (USD/EUR)
    - **GMO Aozora Net Bank API** — Bank transfers & virtual accounts

=== "Events"
    - Event registration with QR tickets
    - Apple Wallet & Google Wallet passes
    - Check-in system

=== "Notifications"
    - Email, Slack, Teams delivery
    - Personalised mail merge
    - Excel import for bulk sends

=== "Integrations"
    - Okta SSO & license management
    - Slack & Microsoft 365
    - GMO Aozora Net Bank
    - Apple/Google Wallet

## Document Structure

<div class="grid cards" markdown>

- :material-account-group: **[Users & Roles](roles/user-types.md)**
  
    User types, licenses, and permission structure

- :material-view-module: **[Modules](modules/overview.md)**
  
    All 14 system modules in detail

- :material-credit-card: **[Payments](payments/overview.md)**
  
    Payment providers, GMO Aozora API, PCI DSS compliance

- :material-source-branch: **[Workflows](workflows/overview.md)**
  
    Approval flows for all operations

- :material-connection: **[Integrations](integrations/overview.md)**
  
    All 11 external system integrations

- :material-database: **[Architecture](architecture/salesforce.md)**
  
    Salesforce setup and custom objects

- :material-rocket-launch: **[Roadmap](roadmap/phases.md)**
  
    MVP → Phase 2 → Phase 3

- :material-scale-balance: **[Legal & Compliance](legal/compliance.md)**
  
    APPI, 特定商取引法, PCI DSS

</div>

---

## Organisation

| Item | Detail |
|---|---|
| **Legal Name** | 特定非営利活動法人Willen |
| **Short Name** | Willen |
| **International Name** | Willen Federation |
| **Website** | [https://willen.jp/](https://willen.jp/) |
| **Location** | 〒158-0082 東京都世田谷区等々力4-21-3 |
| **GitHub** | [https://github.com/Willen-Federation](https://github.com/Willen-Federation) |

---

*特定非営利活動法人Willen © 2026. All rights reserved.*
