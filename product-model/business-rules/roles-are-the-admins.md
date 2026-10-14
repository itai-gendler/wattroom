---
appliesTo:
- type: entity
  id: crew-membership
  effect: changes
  facts:
  - Role
permits:
- related:
  - verb: has
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
  - verb: has
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
  target: server/internal/crews/crew_write.go#handleSetCrewRole
- kind: doc
  role: intent
  target: docs/spec/roles.md
  title: 'Spec: roles and permissions'
---

# Only the crew's owner or an admin makes admins, makes members, bans and unbans

A role is only for someone already in the crew, a ban may come before they are, nobody changes their own role, and the owner is never the target: the owner cannot be demoted, removed or banned.
