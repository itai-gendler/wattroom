---
kind: primary
routes:
  web: Web
steps:
- text: The Rider chooses Move… on a plan and picks a new time
  kind: actor
  actor: rider
  entities:
  - entity: planned-session
    effect: changes
    facts:
    - Starts at
  contexts:
    web:
      place: web::signed-in::crew-schedule
- text: The Product clears the answers of those who said they are out, announces the move and tells the crew
  kind: product
  actor: rider
  entities:
  - entity: answer
    effect: removes
  - entity: crew
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::crew-schedule
references:
- kind: code
  role: implementation
  target: server/internal/crews/crew_schedule.go#handleCrewMove
---

# Move a plan

## Trigger

Tuesday clashes with a race on TV.

## Outcome

The plan has its new time, and the riders who had declined are asked again.

## Edge cases

- Moving a plan to the time it already has is not a move: no mail, no announcement, and the declines stand.
