---
kind: validation
routes:
  web: Web
steps:
- text: The Rider enters an empty name or one over 60 characters
  kind: actor
  actor: rider
  entities: []
  contexts:
    web:
      place: web::signed-in::crew-settings
- text: The Product refuses it and keeps the old name
  kind: product
  actor: rider
  entities: []
  contexts:
    web:
      place: web::signed-in::crew-settings
references:
- kind: code
  role: implementation
  target: server/internal/channels/write.go#cleanName
---

# A channel name that is not one

## Trigger

An admin clears a channel's name.

## Outcome

The channel keeps its name.
