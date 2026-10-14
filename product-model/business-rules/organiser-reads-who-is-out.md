---
appliesTo:
- type: entity
  id: planned-session
  effect: reads
  facts:
  - Who is out
  - Who has not answered
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
  target: server/internal/crews/crew_schedule.go#rosterOf
- kind: doc
  role: intent
  target: docs/spec/crew.md
  title: 'Spec: planned sessions'
---

# Only the organiser reads who is out and who has not answered

Who is in is named; who is out is a number. The planner, the crew's owner and its admins, who chase answers or call the session off, also read the names; nobody else is ever sent them.
