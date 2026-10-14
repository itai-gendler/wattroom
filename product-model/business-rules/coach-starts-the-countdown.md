---
appliesTo:
- type: entity
  id: session
  effect: changes
  to: Counting in
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

# Only the session's coach starts its countdown

The coach is whoever picked the workout, until it is handed on.
