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

## Payment Integration

Forms can be configured with:

- **No payment** — information collection only
- **Optional payment** — member can choose to pay
- **Required payment** — form cannot be submitted without payment

Payment methods available via the full payment stack (Pay.jp, Omise, Stripe).
