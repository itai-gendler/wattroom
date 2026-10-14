---
kind: alternative
routes:
  web: Web
steps:
- text: The Rider opens the page of someone they share a channel with
  kind: actor
  actor: rider
  entities: []
  contexts:
    web:
      place: web::signed-in::rider-page
- text: The Product shows that rider's level, total XP, medals and earned trophies, without their progress counts
  kind: product
  actor: rider
  entities:
  - entity: trophy
    effect: reads
    facts:
    - Achievement
    - Earned on
  - entity: medal
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::rider-page
references:
- kind: code
  role: implementation
  target: server/internal/gamify/api.go
---

# A crew-mate's page

## Trigger

A member admires a crew-mate's Sufferfest Survivor.

## Outcome

The member reads what the crew already sees.
