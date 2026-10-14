---
actors:
- rider
access: authenticated
entryPoints:
- web: /home
- web: /c/{code}
- web: /crew/{id}
---

# Signed in

Signed-in riders take part in their crews, ride sessions and alone, keep their
workouts and read their rides. A crew's owner and admins also run its settings
and members from here.
