# Custom Objects

## Proposed Custom Objects

| Object API Name | Purpose |
|---|---|
| `Willen_Member__c` | Extended member profile (supplements Contact/Account) |
| `Department__c` | Department records with parent-child hierarchy |
| `Department_Member__c` | Junction object for member-department (multi-dept support) |
| `License_Request__c` | Service license requests and approval tracking |
| `Member_Transfer__c` | HR transfer requests between departments |
| `Application__c` | New member and external applicant applications |
| `Payment_Transaction__c` | Payment records across all providers |
| `Virtual_Account__c` | GMO Aozora virtual account assignments |
| `Subscription__c` | Recurring payment subscriptions |
| `Event__c` | Event records |
| `Event_Registration__c` | Event registrations with QR code references |
| `Resource__c` | Shared resources and documents |
| `Resource_Version__c` | Version history for resources |
| `Notification_Log__c` | Notification send history and delivery status |
| `Form_Builder__c` | Custom form definitions |
| `Form_Submission__c` | Form submission records |
| `Wallet_Pass__c` | Apple/Google Wallet pass records |

## Key Relationships

```
Account (Org)
  └── Contact (Member) ─── Willen_Member__c (extended profile)
        └── Department_Member__c (many-to-many)
              └── Department__c (hierarchy)

Application__c → Contact (on approval)
License_Request__c → Contact + License type
Payment_Transaction__c → Contact + related record
Event__c → Event_Registration__c → Contact
```

## Standard Objects Used

| Standard Object | Usage |
|---|---|
| `Account` | Organisation accounts |
| `Contact` | Member records |
| `Case` | Help center cases |
| `Task` / `Event` | Activities |
| `ContentDocument` | File attachments |
