---
kind: edge
routes:
  web: Web
steps:
- text: A planned session is an hour away
  kind: condition
  unattended: true
  entities:
  - entity: planned-session
    effect: reads
    facts:
    - Starts at
  - entity: session
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::crew-schedule
- text: The Product reminds the members who keep Notify me on, leaving out anyone who said they are out
  kind: product
  entities:
  - entity: answer
    effect: reads
    facts:
    - Answer
  - entity: crew-membership
    effect: reads
    facts:
    - Notify me
  contexts:
    web:
      place: web::signed-in::crew-schedule
references:
- kind: doc
  role: intent
  target: docs/spec/crew.md
  title: 'Spec: planned sessions'
---

# The hour-before reminder

## Trigger

The time of a plan approaches.

## Outcome

Members who may still come get a reminder; a rider who said out is not reminded about it.
