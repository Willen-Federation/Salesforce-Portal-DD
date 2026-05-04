# Workflow System

## Overview

The Willen Member Portal uses Salesforce Flow and Apex-based workflows for all approval processes.

**Default rule:** ALL standard workflows route to **Willen Committee** by default.

Department Managers can create **custom workflows** scoped to their own department only.

## Workflow Routing Table

| Workflow Type | Routed To | Notes |
|---|---|---|
| New Member Application | Willen Committee | 5 outcomes: Approve, Reject, More Info, Interview, Waitlist |
| License Request | Willen Committee (Technology Staff) | Direct routing — no Department Manager involvement |
| Member Transfer / HR | Willen Committee | Org chart updates on schedule after approval |
| Offboarding | N/A (paper form only) | Admin manually triggers after receiving paper form |
| Payment / Donation (if review needed) | Willen Committee | For approvals requiring manual review |
| Help Center Case | Willen Committee | By case type: Technical, Billing, HR, General |
| Department Custom Workflow | Configurable by Dept Manager | Scoped to department only |
| Form Builder Submissions | Configurable per form | Set at form creation time |

## Custom Workflows

Department Managers can create workflows for:

- Department-specific approval processes
- Internal requests unique to their team
- Custom information collection with approval

Custom workflows are scoped to the department and cannot access org-wide data.

## Notification on Workflow Events

All workflow state changes trigger notifications via the [Notification Service](../modules/notifications.md):

| Event | Notified |
|---|---|
| Request submitted | Approver (Committee or custom) |
| Approved | Submitter |
| Rejected | Submitter (with reason) |
| More info requested | Submitter |
| Pending reminder | Approver (if overdue) |
