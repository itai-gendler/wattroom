---
appliesTo:
- type: entity
  id: crew
  effect: changes
  facts:
  - Name
  - Icon
  - Picture
  - Listed in directory
  - Weekly board
permits:
- related:
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
  target: server/internal/crews/crew_write.go#handleUpdateCrew
- kind: doc
  role: intent
  target: docs/spec/roles.md
  title: 'Spec: roles and permissions'
---

# Only the crew's owner or an admin changes its name, look, listing and board

The crew's name, icon, picture, directory listing and weekly board are kept by its owner and admins; members read them.
