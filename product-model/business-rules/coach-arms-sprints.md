---
appliesTo:
- type: entity
  id: session
  effect: changes
  facts:
  - Sprint moment
permits:
- related:
  - verb: coaches
    entity: rider
references:
- kind: code
  role: implementation
  target: server/internal/hub/channel_ride.go#refusalLocked
---

# Only the session's coach arms a sprint

Sprints arm only while a session runs, and never during a game, which runs its own.
