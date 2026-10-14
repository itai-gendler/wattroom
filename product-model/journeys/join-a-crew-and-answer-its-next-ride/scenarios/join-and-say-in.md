---
kind: primary
result: achieved
routes:
  web: Web
steps:
- text: The Rider opens the crew's invite link and chooses Join
  kind: actor
  actor: rider
  capability: join-crew
  entities:
  - entity: crew
    effect: reads
    facts:
    - Name
    - Weekly board
  contexts:
    web:
      place: web::signed-in::crew-door
- text: The Product makes the Rider a member and opens the crew's Home with its next planned session
  kind: product
  actor: rider
  capability: join-crew
  entities:
  - entity: crew-membership
    effect: creates
    facts:
    - Role
    - Joined on
    - Notify me
    - On the weekly board
  - entity: planned-session
    effect: reads
    facts:
    - Workout
    - Starts at
    - Who is in
  - entity: crew
    effect: reads
    facts: []
  - entity: session
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::crew-home
- text: The Rider chooses In on the next planned session
  kind: actor
  actor: rider
  capability: answer-planned-session
  entities:
  - entity: answer
    effect: creates
    facts:
    - Answer
  - entity: planned-session
    effect: reads
    facts: []
  - entity: session
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::crew-home
references:
- kind: code
  role: implementation
  target: web/src/routes/(app)/c/[code]/+page.svelte
- kind: code
  role: implementation
  target: web/src/lib/session/PlanCard.svelte
---

# Join and say you are in

## Trigger

A friend sends a rider the crew's link a few days before ride night.

## Outcome

The rider is in the crew and named among those who are in for its next ride.
