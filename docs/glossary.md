# Glossary

| Term | Definition |
|---|---|
| **Willen** | Short name / internal brand for 特定非営利活動法人Willen |
| **Willen Federation** | External / international brand name used for donation pages and global outreach |
| **Committee** | Willen Committee = Super Admin group with full system access and Administrator licenses |
| **Experience Cloud** | Salesforce product for building customer/member portals — used as the portal layer |
| **LWC** | Lightning Web Components — Salesforce's modern JavaScript-based frontend framework |
| **Apex** | Salesforce's server-side programming language (Java-like syntax) |
| **SCIM** | System for Cross-domain Identity Management — used for Okta-based provisioning to Slack and Teams |
| **参照系 API** | Read-only API operations (e.g. balance inquiry, transaction history) |
| **更新系 API** | Write/update API operations (e.g. initiating bank transfers, cancelling transfers) |
| **バーチャル口座** | Virtual bank account — unique account per member/transaction for automatic payment reconciliation |
| **Pay.jp** | Japanese payment provider used for domestic Visa & Mastercard (Rule a) |
| **Omise** | Payment provider for JCB, Amex, bank transfer, and convenience store payments (Rule b) |
| **Stripe** | International payment provider for USD/EUR payments (Rule c) |
| **GMO Aozora** | GMO Aozora Net Bank — banking API provider for transfers and virtual accounts |
| **APPI** | Act on Protection of Personal Information (個人情報保護法) — Japan's primary data privacy law |
| **特定商取引法** | Act on Specified Commercial Transactions — requires disclosure page on all sales/payment pages |
| **MVP** | Minimum Viable Product — the first production release with core features only |
| **PCI DSS** | Payment Card Industry Data Security Standard — compliance framework for card data handling |
| **pkpass** | Apple Wallet pass file format used for event tickets |
| **DD** | Design Document — this document |
| **NPO** | Non-Profit Organisation — 特定非営利活動法人 in Japanese legal classification |
| **Org-visible** | Visibility level meaning: visible to all logged-in Willen members, but NOT the public internet |
| **C-to-B** | Consumer to Business — payment direction in the ordering system |
| **Webhook** | HTTP callback triggered by a payment event (e.g. GMO Aozora 入金明細通知) |
| **Token** | A payment provider-generated reference that replaces raw card data in storage |
