---
appliesTo:
- type: capability-scenario
  id: hour-before-reminder
- type: entity
  id: answer
references:
- kind: doc
  role: intent
  target: docs/spec/crew.md
  title: 'Spec: planned sessions'
---

# A rider who said they are out is not reminded about the plan

The hour-before reminder goes to members who keep Notify me on and did not answer Out; a cancellation is news whatever anyone answered.
