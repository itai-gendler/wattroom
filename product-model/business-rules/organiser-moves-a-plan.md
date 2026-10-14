---
appliesTo:
- type: entity
  id: planned-session
  effect: changes
  facts:
  - Starts at
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
  target: server/internal/crews/crew_schedule.go#mayRearrange
- kind: doc
  role: intent
  target: docs/spec/roles.md
  title: 'Spec: roles and permissions'
---

# A plan is moved by its planner or by the crew's owner or an admin

Any member plans; rearranging is the organiser's.
