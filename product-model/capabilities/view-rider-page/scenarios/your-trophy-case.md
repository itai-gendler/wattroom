---
kind: primary
routes:
  web: Web
steps:
- text: The Rider opens their own page
  kind: actor
  actor: rider
  entities: []
  contexts:
    web:
      place: web::signed-in::rider-page
- text: The Product shows their level and XP with where it came from, their medals, and every achievement with its progress
  kind: product
  actor: rider
  entities:
  - entity: rider
    effect: reads
    facts:
    - Level
    - Total XP
  - entity: trophy
    effect: reads
    facts:
    - Achievement
    - Earned on
    - XP paid
  - entity: medal
    effect: reads
    facts:
    - Kind
  contexts:
    web:
      place: web::signed-in::rider-page
references:
- kind: code
  role: implementation
  target: server/internal/gamify/api.go#Trophies
---

# Your own trophy case

## Trigger

A rider wonders how close they are to Crew Chief.

## Outcome

The rider reads their trophy case and progress.
