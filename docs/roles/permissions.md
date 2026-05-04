# Permissions Matrix

## Module-Level Permissions

| Module | Super Admin / Committee | Department Manager | General Member | Applicant / Donor |
|---|---|---|---|---|
| Membership Management | Full CRUD | Read dept members | Read/Edit own | ❌ |
| HR Management | Full CRUD | Read dept structure | Read only | ❌ |
| Application Forms | Review & approve | Review dept apps | ❌ | Submit own |
| Event Registration | Create & manage | Create dept events | Register | Register (public) |
| Resource Sharing | Full CRUD | Dept CRUD | Read + Upload | ❌ |
| Ordering & Fees | Full admin | View | Create orders | ❌ |
| Donations | Full admin | ❌ | Donate | Donate |
| Notification Service | Send all | Send to dept | Receive | ❌ |
| Org & Dept Pages | Full CRUD | Edit own dept | View | ❌ |
| Case Management | All cases | Own dept | Own cases | ❌ |
| License Management | Approve + manage | ❌ | Request | ❌ |
| Workflow Engine | All workflows | Custom dept only | ❌ | ❌ |
| Form Builder | Full | Build dept forms | Fill forms | Fill public forms |

## Profile Field Permissions

| Field | Visibility | Member Can Edit | Admin Can Edit |
|---|---|---|---|
| Full Name (JP + EN) | Org-visible | ✅ | ✅ |
| Nickname | Org-visible | ✅ | ✅ |
| Org Email | Org-visible | ❌ | ✅ |
| Profile Photo | Org-visible | ✅ | ✅ |
| Slack Account | Org-visible | ✅ | ✅ |
| Department / Team | Org-visible | ❌ | Via workflow |
| Role / Title | Org-visible | ❌ | ✅ |
| Join Date | Org-visible | ❌ | ✅ |
| Private Email | Private | ✅ | ✅ |
| Phone Number | Private | ✅ | ✅ |
| Address | Private | ✅ | ✅ |
| Birthday | Private | ✅ | ✅ |
| Emergency Contact | Private | ✅ | ✅ |
| Bank Account Info | Private | ✅ | ✅ |
| Credit Card Token | Private | Via payment UI | ✅ |
| Microsoft 365 Account | Admin only | ❌ | ✅ |
| License Assignments | Admin only | ❌ | ✅ |
| Member Status | Admin only | ❌ | ✅ |

!!! note
    **Org-visible** means visible to all logged-in Willen members — NOT the public internet.
