---
kind: alternative
routes:
  web: Web
steps:
- text: The Rider finishes the ramp test and does not save the number
  kind: actor
  actor: rider
  entities: []
  contexts:
    web:
      place: web::signed-in::ramp-test
- text: The Product keeps the Rider's FTP as it was; the test stays in their history
  kind: product
  actor: rider
  entities:
  - entity: rider
    effect: reads
    facts:
    - FTP
  contexts:
    web:
      place: web::signed-in::ramp-test
references:
- kind: doc
  role: intent
  target: docs/spec/stats.md
  title: 'Spec: ramp test'
---

# Keep the FTP you had

## Trigger

The result looks wrong to the rider.

## Outcome

The FTP is unchanged.
