---
kind: primary
routes:
  web: Web
steps:
- text: The Rider opens a saved workout in the editor, changes its blocks and saves
  kind: actor
  actor: rider
  entities:
  - entity: workout
    effect: changes
    facts:
    - Name
    - Steps
    - Length
  contexts:
    web:
      place: web::signed-in::workout-editor
- text: The Product saves the change over the same workout
  kind: product
  actor: rider
  entities:
  - entity: workout
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::workout-editor
references:
- kind: code
  role: implementation
  target: server/internal/customworkouts/customworkouts.go#handleUpdate
---

# Change a saved workout

## Trigger

A rider makes their threshold intervals longer.

## Outcome

The saved workout has its new blocks.
