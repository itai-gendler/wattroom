---
kind: primary
routes:
  web: Web
steps:
- text: The Rider chooses Hand the crew to a member and confirms
  kind: actor
  actor: rider
  entities:
  - entity: crew-membership
    as: next-owner
    effect: reads
    facts:
    - Role
  - entity: crew
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::crew-members
- text: The Product makes that member the crew's owner and the Rider an admin
  kind: product
  actor: rider
  entities:
  - entity: crew
    effect: changes
    facts:
    - Owner
  - entity: crew-membership
    as: next-owner
    effect: changes
    facts:
    - Role
  - entity: crew-membership
    as: previous-owner
    effect: changes
    facts:
    - Role
  contexts:
    web:
      place: web::signed-in::crew-members
references:
- kind: code
  role: implementation
  target: server/internal/crews/crew_ownership.go#handleTransferCrew
- kind: code
  role: implementation
  target: server/internal/crews/crew_ownership.go#makeOwner
---

# Hand the crew to a member

## Trigger

The owner is stepping back from running the crew.

## Outcome

The member owns the crew, and the previous owner is an Admin who may take that away themselves.
