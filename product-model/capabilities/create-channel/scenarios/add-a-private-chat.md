---
kind: alternative
routes:
  web: Web
steps:
- text: The Rider names a new chat channel and makes it private
  kind: actor
  actor: rider
  entities:
  - entity: chat-channel
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::crew-settings
- text: The Product adds it, admitting only the owner and admins until someone is named into it
  kind: product
  actor: rider
  entities:
  - entity: chat-channel
    effect: creates
    facts:
    - Name
    - Position
    - Private
  contexts:
    web:
      place: web::signed-in::crew-settings
references:
- kind: code
  role: implementation
  target: server/internal/channels/write.go#handleCreate
---

# Add a private chat channel

## Trigger

The admins want a channel of their own.

## Outcome

The private chat channel exists and nobody else sees it.
