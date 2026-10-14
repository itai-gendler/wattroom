---
kind: primary
routes:
  web: Web
steps:
- text: The Rider chooses In on a plan
  kind: actor
  actor: rider
  entities:
  - entity: answer
    effect: creates
    facts:
    - Answer
  contexts:
    web:
      place: web::signed-in::crew-schedule
- text: The Product adds the Rider's name to who is in
  kind: product
  actor: rider
  entities:
  - entity: planned-session
    effect: reads
    facts:
    - Who is in
    - Out
    - Unanswered
  contexts:
    web:
      place: web::signed-in::crew-schedule
references:
- kind: code
  role: implementation
  target: server/internal/crews/crew_schedule.go#handleCrewRsvp
---

# Say you are in

## Trigger

A member will be there on Tuesday.

## Outcome

The member is named among those who are in.
