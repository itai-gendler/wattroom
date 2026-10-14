---
appliesTo:
- type: capability
  id: leave-crew
- type: capability
  id: hand-crew-on
- type: capability
  id: delete-account
- type: entity
  id: crew
  facts:
  - Owner
references:
- kind: code
  role: implementation
  target: server/internal/crews/crew_ownership.go
- kind: doc
  role: intent
  target: docs/spec/roles.md
  title: 'Spec: roles and permissions'
---

# A crew always has exactly one owner

The owner cannot leave or be banned, hands the crew on deliberately, and on deleting their account the crew passes to its longest-standing admin, else its longest-standing member, never to anyone it banned.
