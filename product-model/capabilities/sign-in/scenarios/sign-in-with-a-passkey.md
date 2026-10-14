---
kind: alternative
routes:
  web: Web
steps:
- text: The Visitor chooses Sign in with a passkey and confirms on their device
  kind: actor
  actor: visitor
  entities: []
  contexts:
    web:
      place: web::public::sign-in
- text: The Product matches the passkey to its account and signs the person in
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
  target: server/internal/auth/passkey.go
---

# Sign in with a passkey

## Trigger

A rider who added a passkey signs in without a provider.

## Outcome

The rider is signed in.
