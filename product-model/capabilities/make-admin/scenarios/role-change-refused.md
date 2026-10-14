---
kind: validation
routes:
  web: Web
steps:
- text: The Rider asks to change the role of the crew's owner, of themselves, or of someone not in the crew
  kind: actor
  actor: rider
  entities:
  - entity: crew
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::crew-members
- text: 'The Product refuses: the owner cannot be demoted or banned, a rider cannot change their own role, and a role is only for someone already in the crew'
  kind: product
  actor: rider
  entities:
  - entity: crew
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::crew-members
references:
- kind: code
  role: implementation
  target: server/internal/crews/crew_write.go#handleSetCrewRole
---

# The owner or yourself as the target

## Trigger

An admin targets someone a role cannot apply to.

## Outcome

No role changes.
