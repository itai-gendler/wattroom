---
entities:
- entity: crew
  shows:
  - Crew streak
  - Members
  - Name
  - Weekly board
- entity: crew-membership
  shows:
  - Joined on
  - Role
  collects:
  - Notify me
  - On the weekly board
- entity: medal
  shows:
  - Kind
- entity: session-recap
  shows:
  - Started at
  - Who was there
  - Workout
entryPoints:
- web: /crew/{id}/members
references:
- kind: code
  role: implementation
  target: web/src/routes/(app)/crew/[id]/members/+page.svelte
---

# Crew members

The crew's Members page: roster and roles, the ban list for its owner and admins, the crew streak and weekly board, the rider's own switches and the session recaps.
