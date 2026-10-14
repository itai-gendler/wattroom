---
kind: alternative
routes:
  web: Web
steps:
- text: The Rider, who planned the session or is the crew's owner or an admin, chooses Show names
  kind: actor
  actor: rider
  entities:
  - entity: planned-session
    effect: reads
    facts:
    - Who is out
    - Who has not answered
  - entity: crew
    effect: reads
    facts: []
  - entity: session
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::crew-schedule
- text: The Product lists who is out and who has not answered
  kind: product
  actor: rider
  entities: []
  contexts:
    web:
      place: web::signed-in::crew-schedule
references:
- kind: code
  role: implementation
  target: server/internal/crews/crew_schedule.go#rosterOf
---

# The organiser reads the names

## Trigger

An organiser wants to know whom to chase before deciding to hold the session.

## Outcome

The organiser reads the names; nobody else is ever sent them.
