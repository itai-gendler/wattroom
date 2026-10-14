---
appliesTo:
- type: entity
  id: voice-channel
  effect: removes
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
  target: server/internal/channels/write.go#handleDelete
- kind: doc
  role: intent
  target: docs/spec/roles.md
  title: 'Spec: roles and permissions'
---

# Only the crew's owner or an admin deletes voice channels

Deleting a channel takes everything in it for everyone, with no undo, so it is the owner's and admins' act.
