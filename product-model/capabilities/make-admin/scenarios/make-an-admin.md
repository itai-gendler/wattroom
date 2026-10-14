---
kind: primary
routes:
  web: Web
steps:
- text: The Rider chooses Make admin on a member
  kind: actor
  actor: rider
  entities:
  - entity: crew-membership
    as: target
    effect: reads
    facts:
    - Role
  contexts:
    web:
      place: web::signed-in::crew-members
- text: The Product makes the member a crew admin
  kind: product
  actor: rider
  entities:
  - entity: crew-membership
    as: target
    effect: changes
    facts:
    - Role
  - entity: crew
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::crew-members
- text: The member's open screens gain an admin's controls without reconnecting
  kind: product
  actor: rider
  entities: []
  contexts:
    web:
      place: web::signed-in::crew-members
references:
- kind: code
  role: implementation
  target: server/internal/crews/crew_write.go#handleSetCrewRole
---

# Make an admin

## Trigger

The owner wants help running the crew.

## Outcome

The member is an Admin of the crew.
