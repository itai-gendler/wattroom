---
appliesTo:
- type: capability
  id: create-channel
- type: entity
  id: chat-channel
- type: entity
  id: voice-channel
references:
- kind: code
  role: implementation
  target: server/internal/channels/write.go#capOf
- kind: doc
  role: intent
  target: docs/spec/roles.md
  title: 'Spec: roles and permissions'
---

# A crew holds at most 20 chat channels and 10 voice channels

A new crew opens with one of each; the ceilings are refused naming the number and saying to delete one.
