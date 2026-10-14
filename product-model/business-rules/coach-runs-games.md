---
appliesTo:
- type: entity
  id: session
  effect: changes
  facts:
  - Game mode
permits:
- related:
  - verb: coaches
    entity: rider
references:
- kind: code
  role: implementation
  target: server/internal/hub/channel_ride.go#refusalLocked
---

# Only the session's coach starts or ends a game inside it

With no session running, whoever starts a game opens a session for it and is its coach.
