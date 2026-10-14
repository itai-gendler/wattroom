---
kind: primary
routes:
  web: Web
steps:
- text: The Rider opens the crew's Members page
  kind: actor
  actor: rider
  entities:
  - entity: crew
    effect: reads
    facts:
    - Name
    - Members
    - Crew streak
    - Weekly board
  contexts:
    web:
      place: web::signed-in::crew-members
- text: The Product shows the roster the Rider may see, with roles, join days and medals won in the crew
  kind: product
  actor: rider
  entities:
  - entity: crew-membership
    effect: reads
    facts:
    - Role
    - Joined on
  - entity: medal
    effect: reads
    facts:
    - Kind
  - entity: crew
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::crew-members
- text: The Product shows the recaps of the last 90 days' sessions in channels the Rider may enter
  kind: product
  actor: rider
  entities:
  - entity: session-recap
    effect: reads
    facts:
    - Workout
    - Started at
    - Who was there
  - entity: session
    effect: reads
    facts: []
  contexts:
    web:
      place: web::signed-in::crew-members
references:
- kind: code
  role: implementation
  target: server/internal/crews/crew_members.go
- kind: code
  role: implementation
  target: server/internal/store/queries/crews.sql#ListCrewPeople
---

# Read the Members page

## Trigger

A member wants to see who rides in the crew and who came to last week's sessions.

## Outcome

The member reads the roster, the streak and the recaps they may read.

## Edge cases

- While the weekly board is on, the page ranks the week of every member who stays on it.
- A recap of a session in a private channel shows only to the people who may enter that channel.
