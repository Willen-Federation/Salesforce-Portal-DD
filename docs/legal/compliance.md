# Legal & Compliance

## Legal Entity

| Context | Name to Use |
|---|---|
| Internal portal, member-facing | **Willen** |
| External/international pages | **Willen Federation** |
| Legal documents, contracts, 特定商取引法 | **特定非営利活動法人Willen** |

## 特定商取引法に基づく表示

Legal disclosure page: [https://www.willen.jp/terms-policy/](https://www.willen.jp/terms-policy/)

This must be referenced and linked in **all payment flows** throughout the portal.

## 個人情報保護法 (APPI)

Japan's Act on Protection of Personal Information applies to all member data:

- Privacy policy must be displayed on all forms collecting personal data
- Members must consent to data collection
- Data access and deletion rights must be honoured
- 10-year data retention policy applies to archived member records

## Data Retention

| Data Type | Retention Period |
|---|---|
| Active member records | Indefinite (while active) |
| Archived member records (after offboarding) | **10 years** |
| Payment transaction records | As required by law |
| Application records | TBD |

## Payment Compliance

| Requirement | Approach |
|---|---|
| **PCI DSS** | Out of scope — tokenisation only. See [PCI DSS](../payments/pci-dss.md) |
| **特定商取引法** | Disclosure page linked in all payment flows |
| **Refund Policy** | Application fees: non-refundable. Other fees: TBD. |

## Offboarding Legal Requirement

!!! danger
    Member resignation **must be submitted on paper**. Online offboarding is not permitted. This is a legal/organisational requirement.

## Non-Functional Compliance Requirements

| Requirement | Detail |
|---|---|
| **Availability** | Best effort (no SLA commitment) |
| **Languages** | Japanese + English (bilingual) |
| **Accessibility** | TBD |
| **Data Location** | Salesforce data centres (region TBD) |
