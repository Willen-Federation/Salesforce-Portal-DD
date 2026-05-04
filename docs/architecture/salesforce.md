# Salesforce Setup

## Platform Configuration

| Item | Detail |
|---|---|
| **Edition** | Salesforce Nonprofit Edition |
| **Portal Layer** | Experience Cloud — Build Your Own (fully custom) |
| **Development** | Custom Apex + Lightning Web Components (LWC) |
| **Domain (Current)** | `willen.mysite.com` |
| **Domain (Target)** | TBD — e.g. `portal.willen.jp` |
| **Existing Org** | Building on existing Salesforce org |

## Experience Cloud

The portal uses Salesforce Experience Cloud in **"Build Your Own"** mode, meaning:

- No out-of-the-box template limitations
- Fully custom LWC-based UI
- Custom Apex controllers for all backend logic
- Full control over branding, layout, and UX

## License Model

| Role | License |
|---|---|
| Willen Committee / Super Admin | Salesforce (full) Administrator License |
| All other users | Experience Cloud Portal User License |

## Development Stack

```
Frontend:  Lightning Web Components (LWC)
           JavaScript / HTML / CSS
           Salesforce Lightning Design System (SLDS)

Backend:   Apex (server-side logic)
           Salesforce Flow (workflow automation)
           Platform Events (real-time events)
           Named Credentials (external API auth)
           
APIs:      REST API integrations via Apex callouts
           Webhook receivers (GMO Aozora)
           OAuth 2.0 for external services
```
