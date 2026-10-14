---
appliesTo:
- type: entity
  id: session
  effect: changes
  facts:
  - Riders in the ride
permits:
- related:
  - verb: runs
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
  - verb: runs
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
  - verb: runs
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
    is: Member
  - entity: voice-channel
    fact: Private
    is: false
- related:
  - verb: runs
    entity: voice-channel
  - verb: names
    entity: channel-naming
  - verb: holds
    entity: rider
references:
- kind: code
  role: implementation
  target: server/internal/hub/channel_ride.go#refusalLocked
---

# Only someone the session's voice channel admits joins or leaves its ride

Joining is explicit, and each rider joins and leaves for themselves; the coach may run the timeline from the side.
