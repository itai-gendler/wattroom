---
kind: edge
routes:
  web: Web
steps:
- text: The Rider stops before two steps past the warm-up
  kind: actor
  actor: rider
  entities: []
  contexts:
    web:
      place: web::signed-in::ramp-test
- text: The Product offers no FTP at all, since a number from a warm-up is worse than none
  kind: product
  actor: rider
  entities: []
  contexts:
    web:
      place: web::signed-in::ramp-test
references:
- kind: doc
  role: intent
  target: docs/spec/stats.md
  title: 'Spec: ramp test'
---

# Too short to score

## Trigger

A rider abandons the test early.

## Outcome

No FTP is offered.
