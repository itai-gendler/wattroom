---
entities:
- entity: crew
  shows:
  - Icon
  - Members
  - Name
  - Picture
  - Weekly board
- entity: crew-membership
  shows:
  - Role
entryPoints:
- web: /c/{code}
references:
- kind: code
  role: implementation
  target: web/src/routes/(app)/c/[code]/+page.svelte
- kind: code
  role: implementation
  target: server/internal/crews/crew_join.go#handleCrewDoor
---

# Crew door

What an invite link opens onto: the crew's name and mark, whether it keeps a weekly board, and Join.
