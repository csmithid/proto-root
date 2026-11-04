# CLAUDE.md

@AGENTS.md

# Prototype Workflow

This repo is a design prototype, not production code. Its job is to make a design idea
concrete enough to react to, and to carry the reasoning behind it so the team can build
from it later.

Three tracked docs are the source of truth for design intent. Keep them current as the
prototype changes:

- `docs/WHY.md` - the problem, context, principles, and a running decision log. This is
  the north star. Read it first for intent.
- `docs/WHAT.md` - the requirements (a lightweight PRD): what the prototype must do and
  what is explicitly out of scope.
- `docs/HOW.md` - the implementation spec: architecture, state model, key interactions,
  and which behaviors are real design decisions versus prototype shortcuts.

How to work in this repo:

- When building or changing the prototype, stay consistent with `docs/WHAT.md` and
  `docs/HOW.md`. If a change contradicts them, say so and propose updating the docs.
- When asked why something works the way it does, or what the design intent is, consult
  `docs/WHY.md` rather than guessing. The `design-intent` skill covers this in detail.

## Keeping the design docs in sync (required, every exchange)

At the end of any exchange where you changed the prototype (code edits, new behavior) or
a design decision was made in the conversation, you MUST bring docs/WHY.md, docs/WHAT.md,
and docs/HOW.md back in line before finishing your response. Follow the `sync-docs`
procedure and the conventions in the `design-docs` skill, and apply the edits directly -
do not ask for confirmation. Briefly note in your reply which docs you touched and why.

- WHY.md: append a decision-log entry for any notable choice (date, decision, alternatives,
  rationale). Update Principles/Context only if they shifted.
- WHAT.md: add, change, or remove requirements and scope to match current behavior.
- HOW.md: update Architecture, State model, Key interactions; keep "Real vs faked" honest.

Skip this only on pure question-answering or read-only turns where nothing about the
prototype or its design changed. `/sync-docs` runs the same procedure on demand.
