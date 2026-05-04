# Application Workflow

See [Application Forms](../modules/applications.md) for full details.

## Flow

```
Applicant submits form + payment
        ↓
Salesforce record + case created
        ↓
Willen Committee notified
        ↓
    ┌─────────────────────────────────────────────┐
    │             Committee Decision              │
    ├─────────────────────────────────────────────┤
    │ ✅ APPROVE → onboarding triggered           │
    │ ❌ REJECT → applicant notified, fee kept    │
    │ 📋 MORE INFO → applicant resubmits          │
    │ 📅 INTERVIEW → interview scheduled          │
    │ ⏳ WAITLIST → held for later review         │
    └─────────────────────────────────────────────┘
        ↓
Applicant notified of outcome
```

## Fee Policy

All application fees are **non-refundable** regardless of outcome.
