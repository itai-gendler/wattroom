---
appliesTo:
- type: capability
  id: browse-schedule
- type: entity
  id: planned-session
references:
- kind: code
  role: implementation
  target: server/internal/crews/crew_schedule.go
---

# A plan naming a private channel exists only for those who may enter that channel

Planning, reading and starting such a plan all ask the channel's door.
