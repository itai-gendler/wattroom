---
availability:
- place: web::signed-in
domain: crews
references:
- kind: code
  role: implementation
  target: server/internal/crews/crew_join.go#handleLeaveCrew
---

# Leave a crew

A member leaves a crew. Their seat goes with the private channels they were named into, and they drop out of its voice channels at once. The owner cannot leave: they hand the crew on first.
