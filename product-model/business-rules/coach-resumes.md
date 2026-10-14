---
appliesTo:
- type: entity
  id: session
  effect: changes
  from: Paused
  to: Running
permits:
- related:
  - verb: coaches
    entity: rider
references:
- kind: code
  role: implementation
  target: server/internal/hub/channel_ride.go#refusalLocked
---

# Only the session's coach resumes it

The resumed timeline counts down three seconds and runs from where it stood.
