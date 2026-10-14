---
availability:
- place: web::signed-in
domain: board
references:
- kind: code
  role: implementation
  target: server/internal/crews/crew_pins.go#handleDeletePin
---

# Unpin

Any member takes a pin off the crew's board, with an undo.
