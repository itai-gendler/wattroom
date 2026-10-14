---
appliesTo:
- type: entity
  id: message
  effect: removes
permits:
- related:
  - verb: writes
    entity: rider
- related:
  - verb: holds
    entity: chat-channel
  - verb: holds
    entity: crew
  - verb: has
    entity: crew-membership
  - verb: holds
    entity: rider
  when:
  - entity: crew-membership
    fact: Role
    is: Owner
- related:
  - verb: holds
    entity: chat-channel
  - verb: holds
    entity: crew
  - verb: has
    entity: crew-membership
  - verb: holds
    entity: rider
  when:
  - entity: crew-membership
    fact: Role
    is: Admin
- unattended: true
references:
- kind: code
  role: implementation
  target: server/internal/chat/channel_edit.go#handleChannelDelete
- kind: doc
  role: intent
  target: docs/spec/roles.md
  title: 'Spec: roles and permissions'
---

# A message is deleted by its author or by the crew's owner or an admin

The Product also removes a temporary line when its time runs out, and lines past the channel's last 500.
