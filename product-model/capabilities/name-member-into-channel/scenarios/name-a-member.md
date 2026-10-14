---
kind: primary
routes:
  web: Web
steps:
- text: The Rider picks a member under Name a member on a private voice channel
  kind: actor
  actor: rider
  entities:
  - entity: voice-channel
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::crew-settings
- text: The Product names the member into the channel
  kind: product
  actor: rider
  entities:
  - entity: channel-naming
    effect: creates
    facts:
    - Member
    - Channel
  - entity: voice-channel
    effect: reads
    facts:
    - Name
    - Private
  contexts:
    web:
      place: web::signed-in::crew-settings
references:
- kind: code
  role: implementation
  target: server/internal/channels/members.go#handleNameMember
---

# Name a member in

## Trigger

A private channel gains a rider.

## Outcome

The member may enter the channel.
