---
kind: primary
routes:
  web: Web
steps:
- text: The Rider chooses Take out beside a named member of a private chat channel
  kind: actor
  actor: rider
  entities:
  - entity: channel-naming
    effect: reads
    facts:
    - Member
  - entity: chat-channel
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::crew-settings
- text: The Product takes the naming away
  kind: product
  actor: rider
  entities:
  - entity: channel-naming
    effect: removes
  contexts:
    web:
      place: web::signed-in::crew-settings
references:
- kind: code
  role: implementation
  target: server/internal/channels/members.go#handleUnnameMember
---

# Take a member out

## Trigger

A member no longer belongs in a private channel.

## Outcome

They can no longer enter it.
