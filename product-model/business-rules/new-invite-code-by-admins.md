---
appliesTo:
- type: entity
  id: crew
  effect: changes
  facts:
  - Invite code
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
  target: server/internal/crews/crew_write.go#handleRotateCrewCode
---

# Only the crew's owner or an admin makes a new invite code

Every member may share the crew's code, so a leak is the owner's and admins' to fix: the old code stops working at once.
