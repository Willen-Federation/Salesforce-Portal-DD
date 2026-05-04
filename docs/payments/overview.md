# Payment Overview

## Payment Provider Matrix

| Rule | Region | Currency | Methods | Provider |
|---|---|---|---|---|
| **a** | Domestic | JPY | Visa, Mastercard | **Pay.jp** |
| **b** | Domestic | JPY | JCB, Amex, Automated bank transfer (subscription), Manual bank transfer, Convenience store (コンビニ払い) | **Omise** + **GMO Aozora** |
| **c** | International | USD / EUR | International cards (Visa, Mastercard, etc.) | **Stripe** |
| **Payouts** | Domestic | JPY | Bank-to-bank transfers, bulk payouts | **GMO Aozora Net Bank API** |

## Provider Summary

| Provider | Usage | Custom Build? |
|---|---|---|
| **Pay.jp** | Domestic Visa & Mastercard | Standard API integration |
| **Omise** | Domestic JCB, Amex, bank transfer, convenience store | Standard API integration |
| **Stripe** | International payments (USD/EUR) | Standard API integration |
| **GMO Aozora Net Bank** | Bank transfers, virtual accounts, payouts, webhooks | Full API suite |
| **Custom (scratch)** | Future additional channels if needed | TBD |

## Payment Flows

=== "Application Fee"
    1. Applicant selects payment method on application form
    2. Pay.jp / Omise / GMO Aozora processes payment
    3. Salesforce records payment confirmation
    4. Application submitted to Committee queue

=== "Annual Membership Fee"
    1. Subscription created on member approval
    2. Annual charge via saved card token (Pay.jp) or automated bank transfer (Omise)
    3. Failure triggers notification and retry workflow
    4. Non-payment triggers membership review

=== "Donations (Domestic)"
    1. Donor selects amount and method
    2. For bank transfer: GMO Aozora virtual account issued per donation
    3. Webhook notifies Salesforce on payment receipt
    4. Donation record created, donor notified

=== "Donations (International)"
    1. Donor fills Willen Federation donation page (English)
    2. Stripe processes payment (USD/EUR)
    3. Salesforce records international donation
    4. Thank you notification sent

=== "Payouts to Members"
    1. Payout triggered in Salesforce (e.g. ordering refund)
    2. GMO Aozora 更新系 API executes bank transfer
    3. Transfer status tracked via 振込状況照会
    4. Member notified on completion

## Virtual Accounts (バーチャル口座)

GMO Aozora virtual accounts are issued per member or per transaction, enabling:

- **Automatic payment reconciliation** — no manual matching needed
- **Real-time notification** via Webhook when payment arrives
- **Per-transaction tracking** in Salesforce

See [GMO Aozora API](gmo-aozora.md) for full API details.
