---
id: wattroom
summary: 'Group indoor cycling in the browser: a crew with chat and voice channels rides one structured workout or game together, each smart trainer at its own rider''s FTP.'
category: fitness
tags:
- indoor-cycling
- group-workouts
- smart-trainer
- voice-chat
- self-hosted
authors:
- name: Natron
  url: https://natron.io
license: AGPL-3.0-only
languages:
- en
limitations:
- Riding needs a smart trainer that speaks Bluetooth FTMS and Chrome or Edge on a computer or Android phone, or the desktop app; in Safari, Firefox and on an iPhone people take part in the crew and the call but do not ride.
- 'Everything is behind sign-in: people sign in with Google, GitHub or Strava, or with a passkey added to their account.'
- 'A voice channel runs one session at a time, and a session rides its workout as planned: nobody skips a block or adds a minute.'
- Medals are awarded only when at least three riders finish a session.
- Rides are private to their rider by default.
references:
- kind: doc
  role: intent
  target: README.md
  title: README
- kind: doc
  role: intent
  target: WATTROOM.md
  title: Product and architecture decisions
- kind: doc
  role: intent
  target: docs/SPEC.md
  title: Product spec index
---

# WattRoom

WattRoom is a web app where a crew of indoor cyclists trains together. A crew
is a place rather than an event: it has chat channels for the week and voice
channels for ride night. Anyone in a voice channel starts a session, picks a
structured workout or one of seven game modes, and every rider's smart trainer
holds that rider's own share of their FTP, so riders of very different
strength ride the same intervals side by side. The crew plans rides on a
shared schedule, and every ride is saved with its power, medals, XP and
trophies. Riders also ride alone, build and import workouts, and measure their
FTP with a ramp test.

## Intent

In the project's own words, "your crew rides one structured workout together,
every smart trainer on its own rider's FTP, with voice built in. No virtual
world: your watts are the game." Indoor
training is boring alone, and WattRoom answers it "with your crew": "a place,
not an event", where "anyone in the voice channel starts a workout"; workouts
"written in percentages of FTP", so "the 180 W rider and the 320 W rider ride
the same intervals side by side, and it hurts both of them the same"; game
modes "decided by watts alone and measured on each rider's own FTP, so the
smallest engine in the crew can win"; and "rides that count", with a power
curve, XP and trophies, private by default.
