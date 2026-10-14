---
appliesTo:
- type: capability
  id: join-crew
- type: capability
  id: unban-from-crew
- type: entity
  id: crew-membership
  facts:
  - Role
references:
- kind: code
  role: implementation
  target: server/internal/crews/crew_join.go
- kind: doc
  role: intent
  target: docs/spec/roles.md
  title: 'Spec: roles and permissions'
---

# A ban keeps the seat, so it survives every way back in

A banned rider is refused at the door whatever code they hold; lifting the ban restores plain membership and nothing else.
