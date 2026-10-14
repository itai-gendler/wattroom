---
appliesTo:
- type: capability
  id: send-message
- type: entity
  id: message
references:
- kind: doc
  role: intent
  target: docs/spec/crew.md
  title: 'Spec: text channel chat'
---

# A chat channel keeps its last 500 messages

Every send lets older messages go, except the channel's announcement. A temporary line counts toward the 500 while it lives and is gone for everyone the moment its time runs out.
