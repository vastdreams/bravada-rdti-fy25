# Integrations

> **Scope**: OneDrive, Outlook (V1); Xero (V2); others future  
> **Status**: 🔴 TODO  
> **Version**: V1.0 → V2.0

---

## Current State

Not fully specified. OneDrive/Outlook implied; others TBD.

---

## Problem

Data lives in customer systems (OneDrive, Outlook, Xero). Without integration, users duplicate effort and lose traceability.

---

## Solution

Minimal, secure connections to customer systems to store files/emails in-place and sync key financial objects.

---

## Invariants

1. Customer owns data; stored in their OneDrive/Outlook/Xero  
2. Access via OAuth; tokens encrypted at rest, never logged  
3. Only minimum scopes requested  
4. On disconnect, stop syncing and clear tokens  
5. File storage happens in customer OneDrive (not Quotech servers)

---

## V1 Core Integrations

| System | Purpose | Scopes |
|--------|---------|--------|
| OneDrive (Graph) | Files/folders per job | `Files.ReadWrite.All`, `offline_access` |
| Outlook (Graph) | Email capture/send | `Mail.ReadWrite`, `Mail.Send`, `offline_access` |

### OneDrive Capabilities
- Create job folder structure  
- Upload/download files  
- List folders/files  
- Store PDFs (POs, invoices, QA)  
- Watch for changes (webhooks)

### Outlook Capabilities
- Capture inbound emails to jobs  
- Send emails from Quotech (captured)  
- Save attachments to OneDrive  
- Watch inbox (webhooks)

---

## V2 Extended

| System | Purpose | Scopes |
|--------|---------|--------|
| Xero | Invoices/bills sync | `accounting.transactions`, `offline_access` |
| Simpro (import) | Migration | TBD |

### Xero Flows
| Event | Action |
|-------|--------|
| Invoice created/approved | Push to Xero (draft/sent) |
| Payment in Xero | Pull status → mark paid |
| Supplier bill received | Push to Xero |

---

## Connection Management UI

| Connection | Fields |
|------------|--------|
| OneDrive | Connected user, root path, last sync, reconnect/disconnect |
| Outlook | Connected user, monitored folders, last sync |
| Xero (V2) | Org connected, last sync, scope |

---

## Error Handling

| Error | Handling |
|-------|---------|
| Token expired | Refresh with refresh_token |
| Rate limit | Backoff + retry |
| Quota exceeded | Alert admin |
| Webhook failure | Retry + alert |

---

## Open Questions

| Question | Status |
|----------|--------|
| SharePoint support? | 🔴 TBD |
| Google Workspace timeline? | 🔴 TBD |
| Real-time vs batch for Xero? | 🔴 TBD |

---

## Acceptance Criteria

### V1
- [ ] Connect OneDrive via OAuth; manage job folders
- [ ] Upload/download files; store PDFs
- [ ] Connect Outlook; capture inbound emails; send from Quotech
- [ ] Save attachments to OneDrive; index for search
- [ ] Token refresh and error handling

### V2
- [ ] Connect Xero via OAuth
- [ ] Push invoices to Xero; pull payment status
- [ ] Push supplier bills to Xero
- [ ] Import starter data from Simpro (jobs/quotes/clients)

