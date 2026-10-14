---
availability:
- place: web::signed-in
references:
- kind: code
  role: implementation
  target: server/internal/auth/auth.go#Register
- kind: code
  role: implementation
  target: web/src/lib/account.svelte.ts
---

# Sign out

A rider signs out of WattRoom on this device.
