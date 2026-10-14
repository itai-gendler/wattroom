---
appliesTo:
- type: entity
  id: chat-channel
  effect: changes
  facts:
  - Announcement
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
  target: server/internal/chat/channel_announcement.go
- kind: doc
  role: intent
  target: docs/spec/roles.md
  title: 'Spec: roles and permissions'
---

# Only the crew's owner or an admin puts up and takes down an announcement

A channel has one announcement: a line marked, which leads the channel and the crew's Board and outlives the 500-message prune.
