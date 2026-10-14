---
kind: alternative
routes:
  web: Web
steps:
- text: The Rider chooses Ban from the crew on another rider's page
  kind: actor
  actor: rider
  entities:
  - entity: crew
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::rider-page
- text: The Product records a ban for a rider the crew has never had
  kind: product
  actor: rider
  entities:
  - entity: crew-membership
    effect: creates
    facts:
    - Role
    - Joined on
  - entity: crew
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::rider-page
references:
- kind: code
  role: implementation
  target: server/internal/crews/crew_write.go#handleSetCrewRole
---

# Ban someone not yet in the crew

## Trigger

An admin keeps a known troublemaker out before they arrive.

## Outcome

The rider is on the ban list and is refused at the crew's door.
