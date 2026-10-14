---
kind: alternative
routes:
  web: Web
steps:
- text: The Rider taps the answer they already gave
  kind: actor
  actor: rider
  entities:
  - entity: answer
    effect: removes
  contexts:
    web:
      place: web::signed-in::crew-schedule
- text: The Product counts the Rider as not answered again
  kind: product
  actor: rider
  entities:
  - entity: planned-session
    effect: reads
    facts:
    - Unanswered
  contexts:
    web:
      place: web::signed-in::crew-schedule
references:
- kind: code
  role: implementation
  target: server/internal/crews/crew_schedule.go#handleCrewRsvp
---

# Take your answer back

## Trigger

A member is no longer sure.

## Outcome

The member has not answered.
