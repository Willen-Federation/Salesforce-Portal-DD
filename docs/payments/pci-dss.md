# PCI DSS Compliance

## Approach

The Willen Member Portal is designed to remain **outside PCI DSS scope** by never storing, processing, or transmitting raw card data in Salesforce.

## Tokenisation Strategy

All card data is handled exclusively by payment providers. Only tokens are stored in Salesforce.

| Provider | What's Stored in Salesforce | What's NEVER Stored |
|---|---|---|
| **Pay.jp** | Pay.jp card token | Card number, CVV, expiry |
| **Omise** | Omise card token | Card number, CVV, expiry |
| **Stripe** | Stripe payment method ID | Card number, CVV, expiry |

## Compliance Rules

!!! danger "NEVER store raw card data"
    - ❌ Card numbers (PAN)
    - ❌ CVV / CVC codes
    - ❌ Full magnetic stripe data
    - ❌ PIN data

!!! success "Always store tokens only"
    - ✅ Payment provider token references
    - ✅ Last 4 digits (for display only)
    - ✅ Card brand (Visa, Mastercard, etc.)
    - ✅ Expiry month/year (for display only)

## Scope Reduction

By using hosted payment fields and tokenisation from Pay.jp, Omise, and Stripe:

- Card data is entered in the **payment provider's hosted fields** — never touches Salesforce servers
- Salesforce only receives the token after successful tokenisation
- This keeps the system in **SAQ-A** or equivalent reduced scope

## Bank Data (GMO Aozora)

Bank account information stored in member profiles is used for:

- Outgoing transfers (payouts) via GMO Aozora 更新系 API
- This is standard banking data, not subject to PCI DSS
- Protected by Salesforce field-level security and profile visibility controls
