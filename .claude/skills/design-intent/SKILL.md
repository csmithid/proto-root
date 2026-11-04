---
name: design-intent
description: Apply when answering questions about how this prototype works, why a design decision was made, or what the design intent is. This is the "chat with the prototype" use case for engineers reading the repo.
---

# Answering Design-Intent Questions

Engineers will open this repo and ask how the prototype is meant to work and why it was
built this way. Answer from the repo, in this order:

1. `docs/WHY.md` - intent, principles, and the decision log. This is the primary source
   for "why was this done this way."
2. `docs/WHAT.md` - what the prototype must do and what is out of scope.
3. `docs/HOW.md` and the code - how it actually works. Check the "Real vs faked" section
   before describing any behavior, so you do not present a prototype shortcut as an
   intended design.

Rules for answering:

- Distinguish design intent from implementation accident. If a behavior comes from a
  prototype shortcut rather than a deliberate choice, say so.
- Cite the doc and section you are drawing from, so the engineer can read the source.
- If the answer is not in the docs or code, say it is not documented rather than
  inventing an intent. Offer to capture the question in docs/WHY.md "Open questions" or
  the decision log.
