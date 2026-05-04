# GMO Aozora Net Bank API

## Overview

GMO Aozora Net Bank provides a comprehensive banking API used for payment verification, outgoing transfers, virtual accounts, and real-time webhooks.

**API Reference:** [gmo-aozora.com/business/api-cooperation/apilineup.html](https://gmo-aozora.com/business/api-cooperation/apilineup.html)

## API Categories Used

### 口座 (Account) — 参照系

| API | Usage in Willen Portal |
|---|---|
| 口座一覧照会 | List all organisation bank accounts |
| 残高照会 | Check account balance |
| 入出金明細照会 | Deposit/withdrawal transaction history |
| 振込入金明細照会 | Verify incoming transfers (confirm donation/fee received) |

### 振込/振替 (Transfer) — 更新系

| API | Usage in Willen Portal |
|---|---|
| 振込依頼 | Execute outgoing transfers (ordering payouts, refunds) |
| 振込取消依頼 | Cancel pending transfers |
| 振込手数料事前照会 | Pre-check transfer fees before execution |
| 振込状況照会 | Check transfer status and history |
| 振込依頼結果照会 | Check processing status of transfer requests |

### 総合振込 (Bulk Transfer) — 更新系

| API | Usage in Willen Portal |
|---|---|
| 総合振込依頼 | Bulk payouts to multiple members simultaneously |
| 総合振込取消依頼 | Cancel bulk transfer requests |
| 総合振込手数料事前照会 | Pre-check bulk transfer fees |
| 総合振込状況照会 | Check bulk transfer status |

### 振込入金口座 (Virtual Accounts) — 参照系

| API | Usage in Willen Portal |
|---|---|
| 振込入金口座発行 | Issue virtual accounts per member/transaction |
| 振込入金口座入金明細照会 | Check payments to specific virtual accounts |
| 振込入金口座一覧照会 | List all issued virtual accounts |
| 振込入金口座状態変更 | Stop/resume/delete virtual accounts |
| 振込入金口座追加名義設定 | Set additional name on virtual account |

### イベント通知 (Webhooks)

| API | Usage in Willen Portal |
|---|---|
| 振込入金口座 入金明細通知 | Real-time notification when payment arrives at virtual account |
| 通知配信制御 | Control webhook delivery start/stop |
| 通知配信状況照会 | Check webhook delivery status |
| 振込入金口座 未送信明細取得 | Retrieve undelivered notifications after webhook downtime |

## Virtual Account Architecture

!!! tip "Key design pattern"
    Issue a **unique virtual account per member or per transaction**. This enables automatic payment reconciliation — Salesforce knows exactly which member or order a payment belongs to without manual matching.

```
New member approved / new order created
        ↓
GMO Aozora: 振込入金口座発行
        ↓
Unique virtual account issued
        ↓
Member/payer notified of their account details
        ↓
Member makes bank transfer to their virtual account
        ↓
Webhook: 振込入金口座 入金明細通知
        ↓
Salesforce: payment confirmed, record updated
```

## Payment Flow Types

=== "Incoming (参照系)"
    Used when the system **receives** payments:
    
    - Check if donations/fees have arrived
    - Verify virtual account payments
    - Reconcile bank statements
    - Monitor account balance

=== "Outgoing (更新系)"
    Used when the system **sends** payments:
    
    - Payout to member (ordering, refund)
    - Bulk salary/payment runs
    - Agent fee disbursement
    - Cancel pending transfers
