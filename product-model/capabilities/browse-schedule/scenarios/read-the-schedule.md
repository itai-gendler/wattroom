---
kind: primary
routes:
  web: Web
steps:
- text: The Rider opens the crew's Schedule
  kind: actor
  actor: rider
  entities:
  - entity: crew
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::crew-schedule
- text: The Product lists the upcoming planned sessions the Rider may see, earliest first, and those planned first ahead of later ones at the same time
  kind: product
  actor: rider
  entities:
  - entity: planned-session
    effect: reads
    facts:
    - Workout
    - Starts at
    - Voice channel
    - Who is in
    - Out
    - Unanswered
  - entity: session
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::crew-schedule
references:
- kind: code
  role: implementation
  target: server/internal/crews/crew_schedule.go
- kind: code
  role: implementation
  target: web/src/lib/session/rsvp.ts#rsvpSummary
---

# Read the schedule

## Trigger

A member checks what the crew is riding this week.

## Outcome

The member reads every plan they may see, as "4 in — Ada, Kim · 2 out · 9 unanswered".

## Edge cases

- A plan naming a private channel does not appear for anyone who may not enter that channel.
