---
appliesTo:
- type: entity
  id: session
  effect: changes
  to: Paused
permits:
- related:
  - verb: coaches
    entity: rider
references:
- kind: code
  role: implementation
  target: server/internal/hub/channel_ride.go#refusalLocked
- kind: doc
  role: intent
  target: docs/spec/roles.md
  title: 'Spec: roles and permissions'
---

# Only the session's coach pauses it

Being the crew's owner or an admin does not make anyone coach. A game keeps its own clock and does not pause.
