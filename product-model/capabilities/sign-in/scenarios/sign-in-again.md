---
kind: alternative
routes:
  web: Web
steps:
- text: The Visitor chooses the provider they signed up with
  kind: actor
  actor: visitor
  entities: []
  contexts:
    web:
      place: web::public::sign-in
- text: The Product finds their account by the provider's identity and signs them in
  kind: product
  actor: visitor
  entities:
  - entity: rider
    effect: reads
    facts:
    - Sign-in methods
  contexts:
    web:
      place: web::public::sign-in
references:
- kind: code
  role: implementation
  target: server/internal/auth/callback.go
---

# Sign in with a provider again

## Trigger

A returning rider opens WattRoom on a new device.

## Outcome

The rider is signed in.
