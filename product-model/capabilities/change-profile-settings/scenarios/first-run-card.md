---
kind: alternative
routes:
  web: Web
steps:
- text: The Rider keeps the prefilled 200 W and 75 kg on Home's first-run card
  kind: actor
  actor: rider
  entities:
  - entity: rider
    effect: changes
    facts:
    - FTP source
    - Weight source
  contexts:
    web:
      place: web::signed-in::home
- text: The Product records the numbers as set by the Rider
  kind: product
  actor: rider
  entities: []
  contexts:
    web:
      place: web::signed-in::home
references:
- kind: code
  role: implementation
  target: server/internal/auth/me.go#handleUpdateMe
---

# Answer the first-run card

## Trigger

A new rider is asked for their FTP and weight.

## Outcome

Keeping the prefilled numbers is a valid answer; a rider who skips the card rides anyway.
