---
kind: edge
routes:
  web: Web
steps:
- text: A temporary line's time runs out
  kind: condition
  unattended: true
  entities:
  - entity: message
    effect: reads
    facts:
    - Disappears at
  contexts:
    web:
      place: web::signed-in::chat-channel
- text: The Product removes it for everyone at once, with its reactions, and leaves nothing in its place
  kind: product
  entities:
  - entity: message
    effect: removes
  contexts:
    web:
      place: web::signed-in::chat-channel
references:
- kind: doc
  role: intent
  target: docs/spec/crew.md
  title: 'Spec: temporary lines'
---

# A temporary line runs out

## Trigger

The timer a sender set on a line reaches its end.

## Outcome

No reader is served the line again and the account export no longer carries it.
