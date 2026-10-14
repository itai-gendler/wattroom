---
appliesTo:
- type: entity
  id: planned-session
  effect: changes
  to: Started
permits:
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
    is: Member
references:
- kind: code
  role: implementation
  target: server/internal/crews/crew_schedule.go#handleCrewStarted
---

# A planned session is started by a member the plan's voice channel admits

Start now opens the session with whoever pressed it as coach, the planner's workout picked; a plan is started once.
