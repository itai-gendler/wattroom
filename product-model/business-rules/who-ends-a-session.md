---
appliesTo:
- type: entity
  id: session
  effect: changes
  to: Ended
permits:
- related:
  - verb: coaches
    entity: rider
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
- unattended: true
references:
- kind: code
  role: implementation
  target: server/internal/hub/channel_ride.go#refusalLocked
- kind: code
  role: implementation
  target: server/internal/hub/session_end.go#endAbandonedSessionLocked
- kind: doc
  role: intent
  target: docs/spec/roles.md
  title: 'Spec: roles and permissions'
---

# A session is ended by its coach, or by the crew's owner or an admin

Ending somebody else's session is the one lever the owner and admins hold over it, because an abandoned one holds the channel shut. The Product ends a session when its timeline runs out, and a paused one nobody has been in for 10 minutes.
