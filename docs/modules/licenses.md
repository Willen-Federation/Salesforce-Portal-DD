# License Management

**Phase:** 🔴 MVP

## Overview

The portal manages the **request and approval workflow** for service licenses. Okta Dashboard remains the execution layer for actual provisioning — the portal only handles tracking and workflow.

!!! warning "No SSO links in portal"
    The portal does NOT include an app launcher or service links. Okta Dashboard handles that separately. This is intentional.

## Services Tracked

| Service | Purpose |
|---|---|
| Okta | SSO and identity accounts |
| Microsoft 365 | Teams, email, Office licenses |
| Slack | Workspace memberships |
| OpenAI API | API access licenses |
| Others | Additional services as needed |

## License Request Flow

```
Member submits license request
        ↓
Workflow auto-routes to Willen Committee
        ↓
Committee approves / rejects
        ↓
Member notified of decision
        ↓
Admin manually provisions in Okta
```

!!! note "No Department Manager involvement"
    License requests go **directly** to Willen Committee (Technology Staff). Department Managers are not in this approval chain.

## License Deletion Flow

```
Member or admin requests license removal
        ↓
Workflow routes to Willen Committee
        ↓
Committee approves
        ↓
Admin manually removes in Okta/service
        ↓
License record updated in Salesforce
```

## License Dashboard

Admins and Committee members can view:

- All active licenses per member
- Pending license requests
- License history and changes
- Services without active licenses
