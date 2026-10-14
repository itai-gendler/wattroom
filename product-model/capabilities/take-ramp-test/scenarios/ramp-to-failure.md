---
kind: primary
routes:
  web: Web
steps:
- text: The Rider starts the ramp test and pedals until they cannot hold the target
  kind: actor
  actor: rider
  entities: []
  contexts:
    web:
      place: web::signed-in::ramp-test
- text: The Product ends the test once power stays under 75 % of the target for five seconds, and saves it as an unscored ride
  kind: product
  actor: rider
  entities:
  - entity: ride
    effect: creates
    facts:
    - Workout
    - Started at
    - Duration
    - Average power
    - Normalized power
    - Energy
    - Execution score
    - Scored
    - FTP at the ride
    - XP
    - Power curve
    - Samples
    - Ridden with
  contexts:
    web:
      place: web::signed-in::ramp-test
- text: 'The Product shows the FTP: 75 % of the best rolling minute'
  kind: product
  actor: rider
  entities:
  - entity: ride
    effect: reads
    facts:
    - Power curve
  contexts:
    web:
      place: web::signed-in::ramp-test
- text: The Rider saves the new FTP
  kind: actor
  actor: rider
  entities:
  - entity: rider
    effect: changes
    facts:
    - FTP
    - FTP source
  - entity: ride
    effect: changes
    facts:
    - FTP produced
  contexts:
    web:
      place: web::signed-in::ramp-test
references:
- kind: code
  role: implementation
  target: server/internal/rides/ftp_after.go#handleFtpAfter
---

# Ramp to failure and save the FTP

## Trigger

A rider has never measured their FTP, or thinks it has moved.

## Outcome

The rider's FTP is the measured one, marked as from a ramp, and their FTP trend shows the test's result that day.
