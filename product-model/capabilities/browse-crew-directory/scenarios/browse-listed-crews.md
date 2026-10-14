---
kind: primary
routes:
  web: Web
steps:
- text: The Rider opens Find a crew
  kind: actor
  actor: rider
  entities:
  - entity: crew
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::crew-directory
- text: The Product lists the crews that are listed in the directory, a page at a time
  kind: product
  actor: rider
  entities:
  - entity: crew
    effect: reads
    facts:
    - Name
    - Icon
    - Picture
    - Listed in directory
  contexts:
    web:
      place: web::signed-in::crew-directory
- text: The Rider opens one crew
  kind: actor
  actor: rider
  entities:
  - entity: crew
    effect: reads
    facts:
    - Name
  contexts:
    web:
      place: web::signed-in::crew-directory
- text: The Product opens that crew's door
  kind: product
  actor: rider
  entities:
  - entity: crew
    effect: reads
    facts:
    - Name
    - Icon
    - Picture
    - Weekly board
  contexts:
    web:
      place: web::signed-in::crew-door
references:
- kind: code
  role: implementation
  target: server/internal/crews/crew_directory.go
---

# Browse listed crews

## Trigger

A rider without a crew looks for one to ride with.

## Outcome

The rider stands at a listed crew's door, where they may join it.
