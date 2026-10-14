---
kind: alternative
routes:
  web: Web
steps:
- text: The Rider chooses Out on a plan
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
- text: The Product counts the Rider among those who are out without naming them to the crew
  kind: product
  actor: rider
  entities:
  - entity: planned-session
    effect: reads
    facts:
    - Out
  - entity: crew
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::crew-schedule
references:
- kind: code
  role: implementation
  target: server/internal/crews/crew_schedule.go#tallyAnswers
---

# Say you are out

## Trigger

A member cannot make it.

## Outcome

The out count grows by one and the member is not reminded about the plan.
