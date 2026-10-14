---
availability:
- place: web::signed-in
domain: crews
references:
- kind: code
  role: implementation
  target: server/internal/crews/crew_join.go
- kind: code
  role: implementation
  target: web/src/routes/(app)/c/[code]/+page.svelte
---

# Join a crew

A rider follows a crew's invite link, or enters its six-character code, and joins at the crew's door. The door shows the crew's name and mark, and says whether the crew keeps a weekly board, before anyone walks in.
