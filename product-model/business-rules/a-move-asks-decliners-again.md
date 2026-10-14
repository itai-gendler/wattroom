---
appliesTo:
- type: capability
  id: move-planned-session
- type: entity
  id: answer
references:
- kind: code
  role: implementation
  target: server/internal/crews/crew_schedule.go#handleCrewMove
---

# Moving a plan to a new time clears its declines

The session that was turned down is not the session now planned. An "in" survives the move.
