---
appliesTo:
- type: entity
  id: crew
  effect: removes
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
- related:
  - verb: has
    entity: crew-membership
  - verb: holds
    entity: rider
  when:
  - entity: crew-membership
    fact: Role
    is: Member
references:
- kind: code
  role: implementation
  target: server/internal/crews/crew_join.go#handleLeaveCrew
- kind: code
  role: implementation
  target: server/internal/channels/write.go#deleteChannel
---

# A crew is removed only from within, when nothing is left in it

Its owner deleting its last channel, its last member leaving, or its owner deleting their account with nobody else in it removes the crew.
