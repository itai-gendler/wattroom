---
appliesTo:
- type: capability
  id: move-rider-to-channel
- type: entity
  id: voice-channel
references:
- kind: code
  role: implementation
  target: server/internal/channels/move.go#handleMove
- kind: doc
  role: intent
  target: docs/spec/roles.md
  title: 'Spec: roles and permissions'
---

# Only the crew's owner or an admin moves a rider between voice channels, never one who is pedalling

The move walks the rider through the destination's door, so a private destination must admit them; a rider riding stays put, since a move would end their ride.
