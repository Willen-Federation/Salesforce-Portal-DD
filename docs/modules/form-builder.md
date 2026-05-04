# Form Builder

**Phase:** 🟢 Phase 3

## Overview

The Form Builder allows admins and department managers to create custom forms for flexible fee and information collection — without requiring developer intervention for each new use case.

This replaces the need to hardcode individual payment forms for every new service or fee type.

## Features

| Feature | Detail |
|---|---|
| Custom Fields | Text, dropdown, date, number, file upload, checkbox, radio buttons |
| Payment Attachment | Optional or required payment per form — connects to full payment stack |
| Workflow Routing | Route submissions to specific approver or team |
| Access Control | Public (external access) or members only — configurable per form |
| Submission Notifications | Automatic notification to submitter and approver on submission |

## Use Cases

- Event-specific registration forms with custom questions
- Special project funding requests
- Software agent fee collection forms
- Ad-hoc payment collection
- Surveys and feedback forms
- OSS sponsorship applications

## Form Access Types

| Type | Who Can Access |
|---|---|
| **Internal** | Logged-in Willen members only |
| **Public** | Anyone — accessible without login |
| **Department** | Members of specific department(s) only |

## Payment Configuration

Forms can be configured with three payment modes:

| Mode | Behaviour |
|---|---|
| **No payment** | Information collection only — no payment fields shown |
| **Optional payment** | Member can choose to pay or skip |
| **Required payment** | Form cannot be submitted without completed payment |

### Payment Methods per Form

Each form independently selects which payment methods to enable:

| Method | Provider | Region | Currency |
|---|---|---|---|
| Visa / Mastercard | Pay.jp | Domestic | JPY |
| JCB / Amex | Omise | Domestic | JPY |
| Bank transfer | GMO Aozora (virtual account) | Domestic | JPY |
| Convenience store | Omise | Domestic | JPY |
| International card | Stripe | International | USD / EUR |

### Amount Configuration

| Setting | Options |
|---|---|
| **Fixed amount** | Admin sets a fixed price — customer pays that exact amount |
| **Customer-defined amount** | Customer enters their own amount (e.g. donations) |
| **Tiered options** | Admin defines 2–5 preset amounts for customer to choose from |
| **Minimum amount** | Set a floor for customer-defined amounts |

---

## Platform Fee Settings

Form creators can configure a **platform fee** to be charged to the customer on top of the base amount. This covers processing costs, service charges, or administrative fees.

### Fee Types

| Type | Description | Example |
|---|---|---|
| **Fixed fee** | A flat amount added to every transaction | ¥200 per submission |
| **Percentage fee** | A percentage of the base amount | 3% of payment amount |
| **Combined** | Fixed + percentage together | ¥100 + 2% |

### Fee Display Options

| Option | Behaviour |
|---|---|
| **Included (absorbed)** | Fee is built into the listed price — not shown separately to customer |
| **Added on top (passed to customer)** | Fee is shown as a line item — customer sees base + fee = total |
| **Shown as breakdown** | Full itemised receipt shown: base amount, platform fee, total |

### Fee Configuration Fields

```
Form Payment Settings
├── Payment mode: [ None | Optional | Required ]
├── Amount type: [ Fixed | Customer-defined | Tiered ]
├── Base amount: ¥ _____
│
├── Platform Fee
│   ├── Enable platform fee: [ On | Off ]
│   ├── Fee type: [ Fixed | Percentage | Combined ]
│   ├── Fixed amount: ¥ _____
│   ├── Percentage: _____%
│   ├── Fee display: [ Absorbed | Added on top | Itemised ]
│   └── Fee label: ____________  (e.g. "Service fee", "Processing fee")
│
└── Payment methods: [ ✅ Pay.jp | ✅ Omise | ✅ GMO Aozora | ✅ Stripe ]
```

### Example — OSS Sponsorship Form

| Item | Amount |
|---|---|
| Sponsorship amount (customer-defined) | ¥10,000 |
| Platform fee (3%) | ¥300 |
| **Total charged** | **¥10,300** |

### Example — Event Application with Fixed Fee

| Item | Amount |
|---|---|
| Application fee (fixed) | ¥5,000 |
| Processing fee (¥150 flat) | ¥150 |
| **Total charged** | **¥5,150** |

!!! info "Payment provider fees"
    Platform fees configured here are **Willen's own service fees** and are separate from the payment provider's own transaction fees (Pay.jp, Omise, Stripe rates). Provider fees are handled at the integration layer and are not configurable per form.

!!! tip "Recommended for external forms"
    For public-facing donation and contribution forms, enabling an itemised fee display builds trust with international donors by showing exactly what they are paying for.
