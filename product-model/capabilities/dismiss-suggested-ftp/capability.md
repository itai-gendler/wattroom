---
availability:
- place: web::signed-in
domain: rides
references:
- kind: code
  role: implementation
  target: web/src/lib/suggestion-decline.ts
- kind: code
  role: implementation
  target: web/src/routes/(app)/history/+page.svelte
---

# Dismiss a suggested FTP

The rider dismisses a suggested FTP. Nothing changes on the account; this device does not offer that number again.
