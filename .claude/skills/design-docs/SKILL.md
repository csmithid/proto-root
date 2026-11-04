---
name: design-docs
description: Apply when creating or editing the design docs (docs/WHY.md, docs/WHAT.md, docs/HOW.md) or running /sync-docs. Defines their structure, voice, and editing conventions.
---

# Design Doc Conventions

These conventions govern the three design docs. They mirror the team's Jira story
conventions so the prototype docs and the eventual stories read the same way.

## Voice and framing

- Never use the word "user." Refer to the person using the tool as "you." Example:
  "When you drop a waypoint..." not "When the user drops a waypoint..."
- Never use "As a user, I want..." framing. Use WHY/WHAT. The Why explains the
  motivation; the What explains the change.
- Plain, direct language. No filler, no preamble.
- When you fill a gap with an assumption, flag it in [square brackets] so it is easy to
  spot and review.

## docs/WHY.md

The reasoning layer. Sections:

- Problem - 2 to 4 sentences. What is broken, missing, or slow today, and who it affects.
- Context - background and constraints that shaped the approach.
- Principles - the design principles guiding decisions for this prototype.
- Decision log - one entry per notable decision: date, the decision, alternatives
  considered, and why this one. Append, do not overwrite. This is what engineers read to
  understand "why this way and not that way."

## docs/WHAT.md

The requirements layer (a lightweight PRD). Sections:

- Summary - 2 to 4 sentences describing the behavior, not the implementation. Use domain
  terms by name.
- Requirements - plain bullets (`-`, never `- [ ]`). Each one specific and observable:
  "When X happens, Y is the result." No vague terms like "appropriate" or "properly."
- Scope and non-scope - what this prototype covers and what it deliberately does not.
- Open questions (optional) - only if there are genuinely unresolved decisions.

Do not add acceptance criteria at the prototype stage.

## docs/HOW.md

The implementation layer. Sections:

- Architecture - structure and key components.
- State model - the core state and how it flows.
- Key interactions - the interactions that carry the design, described concretely.
- Real vs faked - which behaviors are load-bearing design decisions versus prototype
  shortcuts (mocked data, skipped validation, hard-coded paths). Engineers rely on this
  to know what to preserve and what to rebuild.
- Known gaps - tech debt and shortcuts worth flagging.

## Editing rules

- Edit in place. Change only the sections that actually changed this session. Do not
  regenerate a whole doc to update one part.
- Optional sections are optional. Omit them entirely if empty. Never leave placeholder or
  empty sections.
- Keep entries concise. These docs are read often and change often.
