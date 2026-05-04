# Event Registration

**Phase:** 🟡 Phase 2

## Overview

Full event management system with QR code tickets, digital wallet passes, and venue check-in functionality.

## Features

| Feature | Detail |
|---|---|
| Event Types | Internal, External, Online, Hybrid |
| Paid Events | Yes — via Pay.jp, Omise, Stripe (same payment stack) |
| Capacity Limits | Configurable per event |
| External Registration | Yes — non-members can register for public events |
| QR Code Tickets | Generated per registrant upon registration/payment |
| Check-in System | QR scan check-in at venue, recorded in Salesforce |
| Apple Wallet Pass | Yes — `.pkpass` format issued automatically |
| Google Wallet Pass | Yes — Google Pay Passes API |

## Event Types

| Type | Who Can Register |
|---|---|
| Internal | Members only |
| External (public) | Members + external individuals |
| Online | Members + external |
| Hybrid | Members + external (separate ticket types) |

## Event Ticket Flow

```
Register + pay (if paid event)
        ↓
Confirmation notification sent via email/Slack
        ↓
QR ticket generated
        ↓
Apple Wallet Pass / Google Wallet Pass issued
        ↓
At event: QR scanned → Check-in recorded in Salesforce
```

## Payment Methods for Tickets

Same payment stack as the rest of the portal:

- **Pay.jp** — Domestic Visa/Mastercard
- **Omise** — Domestic JCB, Amex, bank transfer, convenience store
- **Stripe** — International (USD/EUR) for external participants

## Wallet Passes

=== "Apple Wallet"
    - Format: `.pkpass`
    - Contains: Event name, date, time, location, QR code, Willen branding
    - Issued: Automatically after registration confirmation
    - Updates: Pass can be updated if event details change

=== "Google Wallet"
    - API: Google Pay Passes API
    - Contains: Same fields as Apple pass
    - Issued: Automatically after registration confirmation
    - Updates: Supported via Google Wallet API

## Check-in System

- Admin/staff scan QR codes at venue entrance
- Check-in status recorded in real-time in Salesforce
- Dashboard shows attendance count per event
- Supports offline mode for poor connectivity venues
