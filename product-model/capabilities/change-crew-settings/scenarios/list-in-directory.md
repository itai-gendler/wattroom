---
kind: alternative
routes:
  web: Web
steps:
- text: The Rider turns on In the directory, or Weekly board
  kind: actor
  actor: rider
  entities:
  - entity: crew
    effect: changes
    facts:
    - Listed in directory
    - Weekly board
  contexts:
    web:
      place: web::signed-in::crew-settings
- text: The Product lists the crew for every signed-in rider, or starts showing its weekly board, which its door then discloses
  kind: product
  actor: rider
  entities:
  - entity: crew
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::crew-settings
references:
- kind: code
  role: implementation
  target: server/internal/crews/crew_write.go#handleUpdateCrew
---

# List the crew and turn on its weekly board

## Trigger

A crew wants new riders, or a friendly weekly ranking.

## Outcome

The crew is findable in the directory, or keeps a weekly board.
