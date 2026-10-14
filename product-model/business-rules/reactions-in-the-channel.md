---
appliesTo:
- type: entity
  id: message
  effect: changes
  facts:
  - Reactions
permits:
- related:
  - verb: holds
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
  - verb: holds
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
    is: Member
  - entity: chat-channel
    fact: Private
    is: false
- related:
  - verb: holds
    entity: chat-channel
  - verb: names
    entity: channel-naming
  - verb: holds
    entity: rider
references:
- kind: code
  role: implementation
  target: server/internal/chat/channel_edit.go#handleChannelReact
---

# Only someone a chat channel admits reacts to its messages

A reaction is the reacting rider's own, and the same tap takes it back.
