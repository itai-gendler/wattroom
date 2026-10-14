---
appliesTo:
- type: entity
  id: session
  effect: removes
permits:
- related:
  - verb: coaches
    entity: rider
- related:
  - verb: runs
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
  - verb: runs
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
references:
- kind: code
  role: implementation
  target: server/internal/hub/session.go
---

# A countdown or a pick is cleared by the coach, or by the crew's owner or an admin

Nothing was ridden, so nothing is saved.
