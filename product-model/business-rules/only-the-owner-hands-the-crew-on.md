---
appliesTo:
- type: entity
  id: crew
  effect: changes
  facts:
  - Owner
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
references:
- kind: code
  role: implementation
  target: server/internal/crews/crew_ownership.go
- kind: doc
  role: intent
  target: docs/spec/roles.md
  title: 'Spec: roles and permissions'
---

# Only the crew's owner hands it on

The owner hands the crew to someone in it and not banned from it. The same happens without them when they delete their account: the crew passes to its longest-standing admin, by the day they joined, else its longest-standing member.
