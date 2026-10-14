---
kind: alternative
routes:
  web: Web
steps:
- text: The Rider chooses Out on a plan they said they were in for
  kind: actor
  actor: rider
  entities:
  - entity: answer
    effect: changes
    facts:
    - Answer
  contexts:
    web:
      place: web::signed-in::crew-schedule
- text: The Product moves the Rider from who is in to the out count
  kind: product
  actor: rider
  entities:
  - entity: planned-session
    effect: reads
    facts:
    - Who is in
    - Out
  contexts:
    web:
      place: web::signed-in::crew-schedule
references:
- kind: code
  role: implementation
  target: server/internal/crews/crew_schedule.go#handleCrewRsvp
---

# Change your mind

## Trigger

A member's plans change.

## Outcome

Their answer is Out; changing back is one more tap.
