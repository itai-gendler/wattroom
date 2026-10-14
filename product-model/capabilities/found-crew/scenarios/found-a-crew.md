---
kind: primary
routes:
  web: Web
steps:
- text: The Rider names a new crew under Start a crew
  kind: actor
  actor: rider
  entities:
  - entity: crew
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::home
- text: The Product creates the crew with a fresh six-character invite code, owned by the Rider, unlisted and without a weekly board
  kind: product
  actor: rider
  entities:
  - entity: crew
    effect: creates
    facts:
    - Name
    - Invite code
    - Owner
    - Listed in directory
    - Weekly board
  - entity: crew-membership
    effect: creates
    facts:
    - Role
    - Joined on
    - Notify me
    - On the weekly board
    with: crew
  - entity: chat-channel
    effect: creates
    facts:
    - Name
    - Position
    - Private
    with: crew
  - entity: voice-channel
    effect: creates
    facts:
    - Name
    - Position
    - Private
    - Sound pack
    with: crew
  contexts:
    web:
      place: web::signed-in::home
- text: The Product opens the new crew's Home with its invite code to share
  kind: product
  actor: rider
  entities:
  - entity: crew
    effect: reads
    facts:
    - Name
    - Invite code
  contexts:
    web:
      place: web::signed-in::crew-home
references:
- kind: code
  role: implementation
  target: server/internal/crews/crew_found.go#handleFoundCrew
- kind: code
  role: implementation
  target: server/internal/channels/write.go#OpenFirst
---

# Found a crew

## Trigger

A rider wants a place of their own for their riding friends.

## Outcome

The rider owns a crew whose membership names them Owner, with an open chat channel and an open voice channel called Lounge, and lands on its Home.
