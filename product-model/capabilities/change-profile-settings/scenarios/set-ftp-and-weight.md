---
kind: primary
routes:
  web: Web
steps:
- text: The Rider enters their FTP and weight and saves
  kind: actor
  actor: rider
  entities:
  - entity: rider
    effect: changes
    facts:
    - FTP
    - FTP source
    - Weight
    - Weight source
  contexts:
    web:
      place: web::signed-in::profile-settings
- text: The Product scales every later workout to the new FTP and shows w/kg from now on
  kind: product
  actor: rider
  entities:
  - entity: workout
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::profile-settings
references:
- kind: code
  role: implementation
  target: server/internal/auth/me.go#handleUpdateMe
---

# Set FTP and weight

## Trigger

A rider knows their numbers.

## Outcome

The rider's FTP and weight are their own, marked as set by them.
