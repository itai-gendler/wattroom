---
kind: alternative
routes:
  web: Web
steps:
- text: The Rider starts a workout and cancels during the count-in
  kind: actor
  actor: rider
  entities:
  - entity: workout
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::ride-alone
- text: The Product goes back to the setup with the trainer still paired and saves nothing
  kind: product
  actor: rider
  entities: []
  contexts:
    web:
      place: web::signed-in::ride-alone
references:
- kind: doc
  role: intent
  target: docs/spec/roles.md
  title: 'Spec: a ride alone'
---

# Change your mind during the count-in

## Trigger

The rider picked the wrong workout.

## Outcome

Nothing was ridden, so nothing is saved.
