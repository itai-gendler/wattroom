---
entities:
- entity: channel-naming
  shows:
  - Member
- entity: chat-channel
  shows:
  - Name
  collects:
  - Position
  - Private
- entity: crew
  shows:
  - Members
  - Name
  collects:
  - Icon
  - Listed in directory
  - Name
  - Picture
  - Weekly board
- entity: crew-membership
  shows:
  - Role
- entity: voice-channel
  shows:
  - Name
  - Private
  collects:
  - Name
  - Private
  - Sound pack
entryPoints:
- web: /crew/{id}/settings
references:
- kind: code
  role: implementation
  target: web/src/routes/(app)/crew/[id]/settings/+page.svelte
---

# Crew settings

The crew's settings, kept by its owner and admins: name, icon and picture, invite link, directory listing, weekly board and its channels.
