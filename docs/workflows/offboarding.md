# Offboarding Workflow

!!! danger "Paper Form Required"
    Offboarding **cannot be initiated online**. A physical paper resignation form must be submitted to the Committee.

## Flow

```
Member submits paper resignation form
        ↓
Admin receives paper form
        ↓
Admin triggers offboarding in Salesforce manually
        ↓
🤖 Automatic: Member status → Inactive
🤖 Automatic: Record archived (10-year retention)
🤖 Automatic: Committee notified
        ↓
👤 Manual: Admin deactivates Okta account
👤 Manual: Admin removes from Slack
👤 Manual: Admin removes Microsoft 365 license
```
