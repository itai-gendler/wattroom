---
kind: validation
routes:
  web: Web
steps:
- text: The Rider opens the page of someone they share no channel with and are not friends with
  kind: actor
  actor: rider
  entities: []
  contexts:
    web:
      place: web::signed-in::rider-page
- text: The Product says there is no such rider
  kind: product
  actor: rider
  entities: []
  contexts:
    web:
      place: web::signed-in::rider-page
references:
- kind: code
  role: implementation
  target: server/internal/gamify/api.go
---

# A stranger's page

## Trigger

A rider guesses another rider's address.

## Outcome

Nothing about that rider is shown.
