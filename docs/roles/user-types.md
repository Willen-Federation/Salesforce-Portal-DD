# User Types

## Role Overview

| Role | Salesforce License | Description |
|---|---|---|
| **Super Admin / Committee** | Salesforce Administrator License | Full access. Willen Committee members — create departments, manage all workflows, approve all requests. |
| **Department Manager** | Portal User License | Manages their department page(s), members, custom workflows, and announcements. |
| **General Member** | Portal User License | Access to own profile, events, resources, ordering, help center, and license requests. |
| **New Applicant** | Portal User License (Guest) | Application forms only. No internal access until approved. |
| **Donor / Sponsor** | Portal User License (Guest) | Donation pages and contribution forms only. |

## Key Notes

!!! important "Super Admin = Willen Committee"
    Super Admin and Willen Committee are the **same group**. Committee members have full Salesforce Administrator licenses and access to all system features.

!!! info "Multi-Department Membership"
    Members can belong to **multiple departments** simultaneously. Department assignments are managed through the HR Management module and reflected in the org tree view.

## Workflow Authority

| Actor | Can Do |
|---|---|
| **Willen Committee** | ALL standard workflow approvals, create departments, manage licenses |
| **Department Manager** | Create custom workflows scoped to their department only |
| **General Member** | Submit requests, register for events, upload resources |

## Portal Access by Role

| Feature | Super Admin | Dept Manager | Member | Applicant | Donor |
|---|---|---|---|---|---|
| Member profiles | ✅ Full | ✅ Dept only | ✅ Own only | ❌ | ❌ |
| HR / Org tree | ✅ | ✅ View | ✅ View | ❌ | ❌ |
| Application forms | ✅ Review | ✅ Review | ❌ | ✅ Submit | ❌ |
| Events | ✅ | ✅ | ✅ | ❌ | ❌ |
| Resources | ✅ | ✅ | ✅ | ❌ | ❌ |
| Ordering / Payments | ✅ | ✅ | ✅ | ❌ | ❌ |
| Donations | ✅ | ✅ | ✅ | ❌ | ✅ |
| Notifications | ✅ Send | ✅ Dept send | ✅ Receive | ❌ | ❌ |
| Dept pages | ✅ All | ✅ Own dept | ✅ View | ❌ | ❌ |
| Cases | ✅ All | ✅ | ✅ Own | ❌ | ❌ |
| License requests | ✅ Approve | ❌ | ✅ Request | ❌ | ❌ |
| Form builder | ✅ | ✅ | ❌ | ❌ | ❌ |
