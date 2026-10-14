---
appliesTo:
- type: capability
  id: view-crew-members
- type: entity
  id: session-recap
references:
- kind: code
  role: implementation
  target: server/internal/recap/recap.go
- kind: doc
  role: intent
  target: docs/spec/crew.md
  title: 'Spec: session recap retention'
---

# A session recap keeps presence and time only, for 90 days

Who was in the session's voice channel, when they arrived, how long they stayed and whether they rode, never watts or heart rate. Only current members who may enter the channel it ran in read it.
