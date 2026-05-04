# Payment Providers

## Pay.jp

- **Website:** [pay.jp](https://pay.jp/)
- **Usage:** Domestic Visa & Mastercard (Rule a)
- **Tokenisation:** Yes — card tokens stored in Salesforce, never raw card data
- **Subscriptions:** Supported for recurring annual membership fees
- **Currency:** JPY only

## Omise

- **Website:** [omise.co](https://www.omise.co/)
- **Usage:** Domestic JCB, Amex, bank transfer, convenience store payments (Rule b)
- **Tokenisation:** Yes — card tokens stored in Salesforce
- **Bank Transfer:** Automated (subscription) and manual
- **Convenience Store:** Supported (コンビニ払い)
- **Currency:** JPY

## Stripe

- **Website:** [stripe.com](https://stripe.com/)
- **Usage:** International payments — USD and EUR (Rule c)
- **Tokenisation:** Yes — via Stripe Elements
- **Subscriptions:** Supported
- **Currency:** USD, EUR (multi-currency)
- **Use Case:** Willen Federation international donation pages, international contributor fees

## GMO Aozora Net Bank API

- **Website:** [gmo-aozora.com](https://gmo-aozora.com/)
- **Usage:** Bank transfers (参照系 + 更新系), virtual accounts, payouts, webhooks
- **Currency:** JPY
- **See:** [GMO Aozora API Reference](gmo-aozora.md) for full API details

## PCI DSS

See [PCI DSS Compliance](pci-dss.md) for how all providers are used to maintain compliance.
