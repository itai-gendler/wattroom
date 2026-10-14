---
appliesTo:
- type: entity
  id: chat-channel
  effect: reads
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
    is: Member
  - fact: Private
    is: false
- related:
  - verb: names
    entity: channel-naming
  - verb: holds
    entity: rider
references:
- kind: code
  role: implementation
  target: server/internal/channels/access.go#mayEnter
- kind: doc
  role: intent
  target: docs/spec/roles.md
  title: 'Spec: roles and permissions'
---

# Only those a channel admits enter chat channels

A member who is not banned enters an open channel. A private channel admits the crew's owner, its admins and the members named into it, and to anyone else it does not exist.
