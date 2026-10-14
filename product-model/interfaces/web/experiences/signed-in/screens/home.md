---
entities:
- entity: crew
  shows:
  - Invite code
  - Owner
- entity: rider
  collects:
  - FTP source
  - Weight source
entryPoints:
- web: /home
references:
- kind: code
  role: implementation
  target: web/src/routes/(app)/home/+page.svelte
- kind: code
  role: implementation
  target: web/src/lib/home/StartOrJoin.svelte
---

# Home

The between-rides overview: the set-up card while steps remain, this week's planned sessions across the rider's crews, and starting or joining a crew.
