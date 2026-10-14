---
kind: primary
routes:
  web: Web
steps:
- text: The Rider writes a line in a chat channel and sends it
  kind: actor
  actor: rider
  entities:
  - entity: chat-channel
    effect: reads
    facts:
    - Name
  - entity: message
    effect: creates
    facts:
    - Text
    - Sent at
  contexts:
    web:
      place: web::signed-in::chat-channel
- text: The Product shows it to everyone in the channel, under the Rider's name
  kind: product
  actor: rider
  entities:
  - entity: message
    effect: reads
    facts:
    - Text
    - Sent at
  contexts:
    web:
      place: web::signed-in::chat-channel
references:
- kind: code
  role: implementation
  target: server/internal/chat/channel_post.go#handleChannelPost
---

# Send a line

## Trigger

A member has something to say to the crew.

## Outcome

The message is in the channel for everyone who may enter it.

## Edge cases

- A line over 500 characters is refused.
- Sending too fast is refused with a moment to wait.
