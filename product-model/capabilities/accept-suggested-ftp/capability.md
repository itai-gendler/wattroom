---
availability:
- place: web::signed-in
domain: rides
references:
- kind: code
  role: implementation
  target: server/internal/auth/me.go
- kind: code
  role: implementation
  target: web/src/routes/(app)/history/+page.svelte
---

# Use a suggested FTP

When the rider's best 20 minutes of the last 90 days say their FTP is set too low, the Product offers a new number where they look at their curve. The rider uses it or dismisses it; it is never applied by itself.
