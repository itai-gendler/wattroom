---
availability:
- place: web::signed-in
domain: board
references:
- kind: code
  role: implementation
  target: server/internal/crews/crew_pins.go#handleCreatePin
- kind: code
  role: implementation
  target: web/src/routes/(app)/crew/[id]/board/+page.svelte
---

# Pin something to the board

Any member pins a title and a block of lines to the crew's board.
