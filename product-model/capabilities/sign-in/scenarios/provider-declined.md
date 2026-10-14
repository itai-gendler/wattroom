---
kind: edge
routes:
  web: Web
steps:
- text: The Visitor cancels at the provider, or the provider cannot be reached
  kind: actor
  actor: visitor
  entities: []
  contexts:
    web:
      place: web::public::sign-in
- text: The Product says signing in did not work and offers to try again
  kind: product
  actor: visitor
  entities: []
  contexts:
    web:
      place: web::public::sign-in
references:
- kind: code
  role: implementation
  target: server/internal/auth/callback.go
---

# The provider says no

## Trigger

A person backs out at Google's consent page.

## Outcome

They stay signed out.
