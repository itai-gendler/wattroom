---
appliesTo:
- type: entity
  id: message
  effect: changes
  facts:
  - Text
  - Edited
permits:
- related:
  - verb: writes
    entity: rider
references:
- kind: code
  role: implementation
  target: server/internal/chat/channel_edit.go#handleChannelEdit
- kind: doc
  role: intent
  target: docs/spec/crew.md
  title: 'Spec: text channel chat'
---

# Only a message's author edits it, for as long as it exists

There is no time window: the channel's 500-message bound is the bound. Editing someone else's words is not a power anyone has.
