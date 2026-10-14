---
availability:
- place: web::signed-in
domain: board
references:
- kind: code
  role: implementation
  target: server/internal/crews/crew_pins.go#handleUpdatePin
---

# Edit a pin

Any member edits a pin's title and lines.
