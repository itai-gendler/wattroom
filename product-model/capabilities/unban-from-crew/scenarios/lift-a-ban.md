---
kind: primary
routes:
  web: Web
steps:
- text: The Rider chooses Unban from the crew on the ban list
  kind: actor
  actor: rider
  entities:
  - entity: crew-membership
    as: target
    effect: reads
    facts:
    - Role
    - Joined on
  - entity: crew
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::crew-members
- text: The Product makes the rider a plain member again
  kind: product
  actor: rider
  entities:
  - entity: crew-membership
    as: target
    effect: changes
    facts:
    - Role
  contexts:
    web:
      place: web::signed-in::crew-members
references:
- kind: code
  role: implementation
  target: server/internal/crews/crew_write.go#handleSetCrewRole
---

# Lift a ban

## Trigger

The crew gives a banned rider another chance.

## Outcome

The rider is a Member and may enter the crew's open channels again.
