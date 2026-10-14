---
kind: person
acts: external
relations:
- entity: crew-membership
  verb: holds
  cardinality: one-to-many
- entity: channel-naming
  verb: holds
  cardinality: one-to-many
- entity: session
  verb: coaches
  cardinality: one-to-many
- entity: planned-session
  verb: plans
  cardinality: one-to-many
- entity: answer
  verb: gives
  cardinality: one-to-many
- entity: message
  verb: writes
  cardinality: one-to-many
- entity: ride
  verb: owns
  cardinality: one-to-many
- entity: workout
  verb: owns
  cardinality: one-to-many
- entity: trophy
  verb: earns
  cardinality: one-to-many
references:
- kind: code
  role: implementation
  target: server/internal/auth/me.go
- kind: code
  role: implementation
  target: server/internal/store/db/models.go#User
- kind: doc
  role: intent
  target: docs/spec/stats.md
  title: 'Spec: the rider''s two numbers, XP'
---

# Rider

A person with a WattRoom account. Every rider can found and join crews, ride in sessions and alone, and keep workouts; what they may do inside a crew follows the role their crew membership holds.

## Information kept

- **Display name** — the name every crew and session shows, 1–60 characters
- **Picture** — the rider's avatar
- **Sign-in methods** — the Google, GitHub or Strava identities and the passkeys the account signs in with
- **FTP** — functional threshold power in watts, 50–600; every workout target is a fraction of it
- **FTP source** — Default, Manual or Ramp: nobody has chosen the number yet, the rider set it, or a ramp test measured it
- **Weight** — in kilograms, 30–200; the denominator of every w/kg
- **Weight source** — Default or Manual
- **Threshold heart rate** — the rider's LTHR in beats per minute, 100–210, when they set one
- **Time zone** — the zone the rider's browser reported; their days, streaks and clock trophies start there, UTC until one is reported
- **Total XP** — lifetime experience points: ride XP, voice presence, session voice bonuses and trophies
- **Level** — derived from Total XP; level n needs 500 × n^1.6 XP
- **Suggested FTP** — offered when 95 % of the best 20 minutes in the last 90 days beats the FTP by more than 2 %
