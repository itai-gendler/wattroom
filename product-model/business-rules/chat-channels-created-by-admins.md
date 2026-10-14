---
appliesTo:
- type: entity
  id: chat-channel
  effect: creates
permits:
- related:
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
    entity: crew
  - verb: has
    entity: crew-membership
  - verb: holds
    entity: rider
  when:
  - entity: crew-membership
    fact: Role
    is: Admin
references:
- kind: code
  role: implementation
  target: server/internal/channels/write.go#handleCreate
- kind: doc
  role: intent
  target: docs/spec/roles.md
  title: 'Spec: roles and permissions'
---

# Only the crew's owner or an admin creates chat channels

Channels are what a crew holds, so its owner and admins keep the list.
