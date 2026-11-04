---
description: Sync the WHY/WHAT/HOW design docs with what changed this session.
---

# Sync Design Docs

Bring the design docs back in line with what changed this session. Follow the conventions
in the `design-docs` skill.

Steps:

1. Review what changed this session: code edits, new behaviors, and any design decisions
   made in the conversation.
2. Compare that against the current `docs/WHY.md`, `docs/WHAT.md`, and `docs/HOW.md`.
3. Make targeted, in-place edits. Touch only the sections that actually changed. Do
   not rewrite sections that are still accurate.
   - WHY.md: add a decision-log entry for any notable choice made this session (date,
     decision, alternatives, rationale). Update Principles or Context only if they
     shifted.
   - WHAT.md: add, change, or remove requirements to match current behavior. Update
     scope and non-scope if the boundaries moved.
   - HOW.md: update Architecture, State model, and Key interactions to match the code.
     Keep "Real vs faked" honest about new shortcuts or newly-real behaviors.
4. Apply the targeted, in-place edits directly, then briefly note which docs changed and
   why. Do not ask for confirmation first.
5. Flag any place where the prototype and the docs disagree and you are unsure which is
   correct, rather than silently picking one.

Do not create or modify anything in Jira. These are local docs only.
