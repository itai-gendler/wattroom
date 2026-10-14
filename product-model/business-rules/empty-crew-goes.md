---
appliesTo:
- type: capability
  id: leave-crew
- type: capability
  id: delete-channel
- type: entity
  id: crew
references:
- kind: code
  role: implementation
  target: server/internal/crews/crew_join.go#handleLeaveCrew
- kind: doc
  role: intent
  target: docs/spec/roles.md
  title: 'Spec: roles and permissions'
---

# A crew with nothing left in it goes

A crew with no channel and nobody in it but its owner is removed when its owner deletes its last channel or its last member leaves; never with a ban. A crew has no delete button.
