# License Request Workflow

## Flow

```
Member submits license request
        ↓
Workflow auto-routes to Willen Committee
(NO Department Manager involvement)
        ↓
Committee reviews
        ↓
    ┌─────────────────────────────────────────────┐
    │             Committee Decision              │
    ├─────────────────────────────────────────────┤
    │ ✅ APPROVE → status: Approved               │
    │ ❌ REJECT  → member notified, flow ends     │
    └─────────────────────────────────────────────┘
        ↓
── APPROVED ──────────────────────────────────────
        ↓
Member notified: request approved
        ↓
Admin provisions account in Okta
Status → Preparing
        ↓
Admin completes setup, confirms provisioning
Status → Delivered
        ↓
Member notified: license ready to use
```

## Status Definitions

| Status | Description | Actor |
|---|---|---|
| **Pending** | Request submitted, awaiting Committee review | System |
| **Approved** | Committee has approved the request | Committee |
| **Rejected** | Committee has rejected the request | Committee |
| **Preparing** | Admin is provisioning the account in Okta | Admin |
| **Delivered** | Account is live and ready for the member to use | Admin |

## Application Flow Detail

### ✅ Approved

- Committee approves request in Salesforce
- Status updated to **Approved**
- Member receives notification: *"Your license request has been approved and is being prepared."*
- License record in Salesforce updated with approval timestamp and approver

### 🔧 Preparing

- Admin manually provisions the account in Okta (or relevant service)
- Status updated to **Preparing**
- Member receives notification: *"Your account is being set up. You will be notified when it is ready."*
- Internal note added to the license record with provisioning details

### 📦 Delivered

- Admin confirms provisioning is complete
- Status updated to **Delivered**
- Member receives notification: *"Your license is ready. Please access it via the Okta Dashboard."*
- License record updated with delivery timestamp
- Member's license list in their profile updated

## Services Covered

Okta, Microsoft 365, Slack, OpenAI API, and others.

!!! warning
    The portal tracks requests and approvals only. All actual provisioning is done manually in Okta by an admin.

!!! info "No SSO links in portal"
    Members access their provisioned services via the **Okta Dashboard** — not through this portal.
