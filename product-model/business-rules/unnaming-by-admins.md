---
appliesTo:
- type: entity
  id: channel-naming
  effect: removes
permits:
- related:
  - verb: names
    entity: voice-channel
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
  - verb: names
    entity: voice-channel
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
  - verb: names
    entity: chat-channel
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
  - verb: names
    entity: chat-channel
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
    entity: rider
references:
- kind: code
  role: implementation
  target: server/internal/channels/members.go
- kind: code
  role: implementation
  target: server/internal/crews/crew_join.go#handleLeaveCrew
---

# Only the crew's owner or an admin takes members out of private channels, and a member's naming goes when they leave

Leaving the crew takes the leaver's namings with their seat; otherwise only the owner and admins take a member out.
