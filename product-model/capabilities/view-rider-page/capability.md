---
availability:
- place: web::signed-in
references:
- kind: code
  role: implementation
  target: web/src/routes/(app)/u/[id]/+page.svelte
- kind: code
  role: implementation
  target: server/internal/gamify/api.go
- kind: code
  role: implementation
  target: server/internal/riders/riders.go
---

# View a rider's page

A rider opens their own page or a crew-mate's: level and lifetime energy, medals from crews they share, and the trophy case. Another rider's page shows only to people who share a channel with them, or are their friends.
