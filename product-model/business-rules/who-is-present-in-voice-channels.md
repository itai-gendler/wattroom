---
appliesTo:
- type: entity
  id: voice-channel
  effect: changes
  facts:
  - Riders present
permits:
- related:
  - verb: holds
    entity: crew
  - verb: has
    entity: crew-membership
  - verb: holds
    entity: rider
  when:
  - entity: crew-membership
    fact: Role
    is: Owner
- related:
  - verb: holds
    entity: crew
  - verb: has
    entity: crew-membership
  - verb: holds
    entity: rider
  when:
  - entity: crew-membership
    fact: Role
    is: Admin
- related:
  - verb: holds
    entity: crew
  - verb: has
    entity: crew-membership
  - verb: holds
    entity: rider
  when:
  - entity: crew-membership
    fact: Role
    is: Member
  - fact: Private
    is: false
- related:
  - verb: names
    entity: channel-naming
  - verb: holds
    entity: rider
- unattended: true
references:
- kind: code
  role: implementation
  target: server/internal/channels/access.go#mayEnter
- kind: code
  role: implementation
  target: server/internal/hub/channel_presence.go
---

# Only those a voice channel admits are present in it

Entering, leaving, being moved, banned or shut out of a channel made private all change who is present; each passes the channel's door.
