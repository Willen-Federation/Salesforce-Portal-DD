# Application Forms

**Phase:** 🔴 MVP

## Overview

The application system handles new member applications, external contributor onboarding, and donor registrations. All applications flow through Salesforce case management with a multi-outcome approval workflow.

## Application Types

| Type | Form | Payment Required |
|---|---|---|
| New Member | Full member application | ✅ Yes (non-refundable) |
| OSS Contributor | Contributor application | Optional |
| Donor / Sponsor | Donation form | ✅ Yes (donation amount) |
| External Org | Organisation application | Optional |

## New Member Application Form

| # | Field | Visibility (after approval) | Required |
|---|---|---|---|
| 1 | Full Name (Japanese + English) | 🏢 Org-visible | ✅ |
| 2 | Nickname | 🏢 Org-visible | ❌ |
| 3 | Private Email | 🔒 Private | ✅ |
| 4 | Phone Number | 🔒 Private | ✅ |
| 5 | Address | 🔒 Private | ✅ |
| 6 | Birthday | 🔒 Private | ✅ |
| 7 | Emergency Contact | 🔒 Private | ✅ |
| 8 | Skills / Expertise | 🏢 Org-visible | ❌ |
| 9 | Motivation / Reason for Joining | 👤 Admin only | ✅ |
| 10 | How did you hear about Willen? | 👤 Admin only | ❌ |
| 11 | Agreement to Terms & Conditions | 👤 Admin only | ✅ |
| 12 | Payment (Application Fee) | 👤 Admin only | ✅ |

!!! note "Gender not collected"
    Gender is intentionally excluded from all forms for inclusivity reasons.

## Application Fee

!!! warning "Non-refundable in ALL cases"
    The application fee is collected and retained regardless of the outcome — approved, rejected, waitlisted, or expired.

**Accepted payment methods:**

| Method | Provider |
|---|---|
| Credit card (Visa, Mastercard) | Pay.jp |
| Credit card (JCB, Amex) | Omise |
| Bank transfer | GMO Aozora virtual account |
| Prepaid / e-money | Omise |
| Convenience store | Omise |

## Approval Flow

```
Applicant submits form + payment
        ↓
Salesforce record created automatically
        ↓
Willen Committee notified
        ↓
    ┌───────────────────────────────────────┐
    │         Committee Decision            │
    ├───────────────────────────────────────┤
    │ ✅ APPROVE                            │
    │ ❌ REJECT — applicant notified        │
    │ 📋 REQUEST MORE INFO → resubmit       │
    │ 📅 SCHEDULE INTERVIEW → re-review     │
    │ ⏳ WAITLIST → reviewed later          │
    └───────────────────────────────────────┘
        ↓
Final decision → applicant notified
```

## Upon Approval — Automatic Actions

| Action | Type |
|---|---|
| Welcome notification sent to applicant | 🤖 Automatic |
| Member profile created in Salesforce | 🤖 Automatic |
| Bank transfer virtual account registered (GMO Aozora) | 🤖 Automatic |
| Credit card token registered for subscription | 🤖 Automatic |

## Upon Approval — Manual Actions

| Action | Type |
|---|---|
| Okta account setup | 👤 Manual (admin) |
| Slack workspace invitation | Via Okta SCIM or Salesforce API |
| Microsoft 365 invitation | Via Okta SCIM or Microsoft Graph API |
