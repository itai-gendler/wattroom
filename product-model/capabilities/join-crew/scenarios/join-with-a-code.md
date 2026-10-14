---
kind: alternative
routes:
  web: Web
steps:
- text: The Rider enters a crew's code under Join a crew with a code
  kind: actor
  actor: rider
  entities:
  - entity: crew
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::home
- text: The Product opens that crew's door
  kind: product
  actor: rider
  entities:
  - entity: crew
    effect: reads
    facts:
    - Name
    - Icon
    - Picture
    - Weekly board
  contexts:
    web:
      place: web::signed-in::crew-door
- text: The Rider chooses Join
  kind: actor
  actor: rider
  entities: []
  contexts:
    web:
      place: web::signed-in::crew-door
- text: The Product makes the Rider a member of the crew
  kind: product
  actor: rider
  entities:
  - entity: crew-membership
    effect: creates
    facts:
    - Role
    - Joined on
    - Notify me
    - On the weekly board
  - entity: crew
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::crew-door
references:
- kind: code
  role: implementation
  target: web/src/lib/home/StartOrJoin.svelte
---

# Join with a code

## Trigger

A rider was told a crew's code rather than sent its link.

## Outcome

The rider is a Member of the crew.
