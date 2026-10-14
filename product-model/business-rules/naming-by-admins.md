---
appliesTo:
- type: entity
  id: channel-naming
  effect: creates
permits:
- related:
  - verb: names
    entity: voice-channel
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
  - verb: names
    entity: voice-channel
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
- related:
  - verb: names
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
  - verb: names
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
references:
- kind: code
  role: implementation
  target: server/internal/channels/members.go
- kind: doc
  role: intent
  target: docs/spec/roles.md
  title: 'Spec: roles and permissions'
---

# Only the crew's owner or an admin names members into private channels

A member's naming also goes when they leave the crew or are banned from it.
