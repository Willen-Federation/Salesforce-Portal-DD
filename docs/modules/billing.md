# Billing System

**Phase:** 🟡 Phase 2

## Overview

The Billing System handles the full lifecycle of invoices and payments for Willen members — from PDF generation through to payment collection, case closure, and notification. It supports both **manual** (admin-triggered) and **automated** (system-triggered) workflows.

---

## Billing Lifecycle

```
Billing event triggered (manual or automatic)
        ↓
Invoice record created in Salesforce
        ↓
PDF invoice generated
        ↓
Invoice sent to member (email + portal notification)
        ↓
    ┌─────────────────────────────────────────────┐
    │           Payment Status                    │
    ├─────────────────────────────────────────────┤
    │ ✅ PAID    → Case closed → Member notified  │
    │ ⏳ PENDING → Reminder sent on schedule      │
    │ ❌ OVERDUE → Escalation workflow triggered  │
    │ 🚫 VOID    → Cancelled → Member notified    │
    └─────────────────────────────────────────────┘
```

---

## Invoice Status Definitions

| Status | Description |
|---|---|
| **Draft** | Invoice created but not yet sent to member |
| **Sent** | Invoice delivered to member, awaiting payment |
| **Pending** | Payment in progress (bank transfer initiated, awaiting confirmation) |
| **Paid** | Payment confirmed and reconciled |
| **Overdue** | Payment not received by due date |
| **Void** | Invoice cancelled — member notified |
| **Closed** | Case closed after confirmed payment |

---

## PDF Invoice Generation

### Contents of Generated Invoice PDF

| Section | Fields |
|---|---|
| **Header** | 特定非営利活動法人Willen logo, invoice number, issue date, due date |
| **Billed To** | Member full name, org email, address |
| **Billed From** | 特定非営利活動法人Willen, address, contact, registration number |
| **Line Items** | Description, quantity, unit price, subtotal per line |
| **Fee Breakdown** | Platform fee (if applicable), tax (if applicable) |
| **Total** | Total amount due, currency |
| **Payment Instructions** | Bank transfer details (virtual account), credit card link, convenience store code |
| **Legal Footer** | 特定商取引法に基づく表示 reference, payment terms |

### PDF Generation Method

| Option | Description |
|---|---|
| **Salesforce + Apex** | Generated server-side using Apex, stored as ContentDocument |
| **Template-based** | Admin-configurable invoice templates per billing type |
| **Bilingual** | Japanese and English versions generated on demand |
| **Storage** | Stored in Salesforce Files (ContentDocument) linked to Invoice record |

---

## Manual Billing Workflow

Admin or Committee manually initiates billing for a specific member or group.

```
Admin selects member(s) → fills billing details
        ↓
System creates Invoice record (Draft)
        ↓
Admin reviews PDF preview
        ↓
Admin clicks "Send Invoice"
        ↓
PDF attached and sent to member via:
  📧 Email (private email address)
  💬 Slack notification
  🔔 Portal notification
        ↓
Invoice status → Sent
        ↓
Admin monitors payment status in Salesforce
        ↓
On payment confirmed → Admin marks Paid → Case closed → Member notified
```

### Manual Billing Use Cases

- One-off service fees
- Special project billing
- Corrected or adjusted invoices
- Agent fee billing to external organisations
- Donation receipts (non-payment acknowledgement)

---

## Automated Billing Workflow

System automatically generates and sends invoices based on triggers.

### Trigger Types

| Trigger | Example |
|---|---|
| **Subscription renewal** | Annual membership fee due date approaching |
| **Event registration** | Member registers for paid event |
| **Application approval** | New member approved — initial fee due |
| **Form submission** | Form Builder submission with required payment |
| **Ordering** | OSS support fee or software agent fee |
| **Schedule** | Monthly/quarterly billing runs |

### Automated Flow

```
Trigger event fires (e.g. membership renewal date)
        ↓
Salesforce Flow creates Invoice record automatically
        ↓
PDF generated and attached
        ↓
Invoice sent to member automatically:
  📧 Email with PDF attachment
  💬 Slack notification with payment link
  🔔 Portal notification
        ↓
Invoice status → Sent
        ↓
        ├── Payment received via Pay.jp / Omise / GMO Aozora / Stripe
        │         ↓
        │   Payment webhook → Salesforce updated
        │         ↓
        │   Status → Paid → Case auto-closed → Member notified ✅
        │
        └── No payment by due date
                  ↓
            Status → Overdue
                  ↓
            Reminder notification sent (Day 1, Day 7, Day 14)
                  ↓
            Escalation to Willen Committee if unresolved
```

---

## Payment Methods for Billing

All payment providers are available for billing payments:

| Method | Provider | Region | Currency |
|---|---|---|---|
| Visa / Mastercard | Pay.jp | Domestic | JPY |
| JCB / Amex | Omise | Domestic | JPY |
| Bank transfer (virtual account) | GMO Aozora | Domestic | JPY |
| Convenience store | Omise | Domestic | JPY |
| International card | Stripe | International | USD / EUR |
| Automated bank transfer | Omise (subscription) | Domestic | JPY |

### Payment Confirmation

| Method | Confirmation Mechanism |
|---|---|
| Credit card | Immediate — Pay.jp / Omise / Stripe webhook |
| Bank transfer | GMO Aozora Webhook: 振込入金口座 入金明細通知 |
| Convenience store | Omise webhook on payment completion |
| Automated bank transfer | Omise subscription event |

---

## Case Management Integration

Each invoice is linked to a **Salesforce Case** for tracking and resolution.

### Case Lifecycle

| Stage | Case Status | Action |
|---|---|---|
| Invoice created | Open | Case created, linked to invoice |
| Invoice sent | In Progress | Awaiting payment |
| Payment received | Resolved | Payment confirmed, case ready to close |
| Case closed (manual) | Closed | Admin reviews and closes manually |
| Case closed (auto) | Closed | System auto-closes on payment confirmation |
| Member notified | Closed | Notification sent confirming closure |

### Manual Case Closure

Admin reviews the payment, verifies amount, and manually closes the case:

```
Admin opens case in Salesforce
        ↓
Reviews payment confirmation details
        ↓
Clicks "Close Case"
        ↓
Selects closure reason (Paid / Waived / Void)
        ↓
System sends closure notification to member
        ↓
Case status → Closed
```

### Automated Case Closure

On payment webhook received from payment provider:

```
Payment webhook received (Pay.jp / GMO Aozora / Stripe etc.)
        ↓
Salesforce Flow triggered
        ↓
Invoice status → Paid
        ↓
Linked case → Resolved → auto-close after X hours (configurable)
        ↓
Member notified automatically
```

!!! info "Configurable auto-close delay"
    Auto-closure delay is configurable per billing type (e.g. immediate for credit card, 24h delay for bank transfer to allow for manual review).

---

## Member Notifications

### Notification Events

| Event | Channel | Content |
|---|---|---|
| Invoice issued | Email + Slack + Portal | Invoice PDF attached, payment instructions, due date |
| Payment reminder (overdue) | Email + Slack | Reminder with payment link, days overdue |
| Payment confirmed | Email + Slack + Portal | Receipt confirmation, amount paid, case reference |
| Case closed | Email + Portal | Closure confirmation, invoice reference |
| Invoice voided | Email + Portal | Void notice with reason |

### Notification Templates

All notification templates are bilingual (JP/EN) and support mail merge fields:

| Variable | Example output |
|---|---|
| `{member_name}` | 田中太郎 / Taro Tanaka |
| `{invoice_number}` | INV-2026-001234 |
| `{amount}` | ¥10,000 |
| `{due_date}` | 2026-06-30 |
| `{payment_method}` | 銀行振込 / Bank transfer |
| `{case_number}` | CASE-00001234 |

---

## Invoice Record Fields (Salesforce)

| Field | Type | Description |
|---|---|---|
| Invoice Number | Auto-number | INV-YYYY-XXXXXX |
| Member | Lookup (Contact) | Billed member |
| Invoice Date | Date | Date issued |
| Due Date | Date | Payment deadline |
| Line Items | Related list | Individual charges |
| Subtotal | Currency | Before fees/tax |
| Platform Fee | Currency | Willen service fee |
| Total | Currency | Final amount due |
| Currency | Picklist | JPY / USD / EUR |
| Payment Method | Picklist | Card / Bank / Convenience / International |
| Payment Provider | Picklist | Pay.jp / Omise / GMO Aozora / Stripe |
| Payment Reference | Text | Provider transaction ID |
| Status | Picklist | Draft / Sent / Pending / Paid / Overdue / Void / Closed |
| PDF | File (ContentDocument) | Generated invoice PDF |
| Linked Case | Lookup (Case) | Associated support/billing case |
| Billing Type | Picklist | Membership / Event / OSS Fee / Agent Fee / Donation / Other |
| Notes | Long text | Internal admin notes |

---

## Reporting & Dashboard

| Report | Description |
|---|---|
| Outstanding invoices | All Sent/Overdue invoices with aging |
| Monthly revenue | Paid invoices grouped by month and type |
| Overdue tracking | Members with overdue invoices, days outstanding |
| Payment method breakdown | Revenue by payment provider |
| Case closure rate | Avg time from invoice sent to case closed |
