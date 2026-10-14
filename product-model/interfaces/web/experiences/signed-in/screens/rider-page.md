---
entities:
- entity: crew
  shows:
  - Name
- entity: medal
  shows:
  - Kind
- entity: rider
  shows:
  - Level
  - Total XP
- entity: trophy
  shows:
  - Achievement
  - Earned on
  - XP paid
entryPoints:
- web: /u/{id}
references:
- kind: code
  role: implementation
  target: web/src/routes/(app)/u/[id]/+page.svelte
---

# Rider page

A rider's page: level, energy, medals from shared crews and their trophy case.
