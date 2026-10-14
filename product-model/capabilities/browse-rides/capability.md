---
availability:
- place: web::signed-in
domain: rides
references:
- kind: code
  role: implementation
  target: web/src/routes/(app)/history/+page.svelte
- kind: code
  role: implementation
  target: server/internal/rides/rides.go#handleList
- kind: code
  role: implementation
  target: server/internal/progression/progression.go
---

# Browse your rides

A rider reads their ride history with their FTP trend and power curve over the last 90 days.
