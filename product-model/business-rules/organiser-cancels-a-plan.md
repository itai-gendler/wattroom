---
appliesTo:
- type: entity
  id: planned-session
  effect: removes
permits:
- related:
  - verb: plans
    entity: rider
- related:
  - verb: keeps
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
  - verb: keeps
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
  target: server/internal/crews/crew_schedule.go
- kind: code
  role: implementation
  target: server/internal/channels/write.go#handleDelete
---

# A plan is cancelled by its planner or by the crew's owner or an admin

Cancelling tells the crew. Deleting a private voice channel cancels the plans in it, and the people who could ride them are told.
