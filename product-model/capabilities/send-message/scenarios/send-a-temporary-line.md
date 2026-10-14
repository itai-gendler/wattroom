---
kind: alternative
routes:
  web: Web
steps:
- text: The Rider sets the composer's timer to 1 hour, 24 hours or 7 days and sends a line
  kind: actor
  actor: rider
  entities:
  - entity: message
    effect: creates
    facts:
    - Text
    - Sent at
    - Disappears at
  contexts:
    web:
      place: web::signed-in::chat-channel
- text: The Product shows the line with how long it has left; the timer stays set for the lines that follow
  kind: product
  actor: rider
  entities:
  - entity: message
    effect: reads
    facts:
    - Disappears at
  contexts:
    web:
      place: web::signed-in::chat-channel
references:
- kind: doc
  role: intent
  target: docs/spec/crew.md
  title: 'Spec: temporary lines'
---

# Send a temporary line

## Trigger

A member shares something that should not stay, such as a door code for tonight.

## Outcome

The line is temporary and says when it goes.
