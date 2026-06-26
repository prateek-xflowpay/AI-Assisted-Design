# Selected for Validate Design — Invoicing Flow (Round 2)

Converged 2026-06-24 · Prateek. Driver: **too many steps / drop-off**.

Designer's lead choice: **Model B (Command-bar / conversational)**. Carried with Model A as its
coupled fallback — B's own flow degrades to a blank form, and A is the safe base for new users /
low-confidence parses. These two go to Validate Design as a pair (lo-fi, as built).

| ID | Model | Role | Link |
|----|-------|------|------|
| R2-02 | Command-bar / conversational | **Primary** — fast lane: type → confirm → activate | [→](iterations/round-2/02-command-bar/) |
| R2-01 | Smart single-screen form | **Fallback / foundation** — the form B degrades to; also the default for new users | [→](iterations/round-2/01-smart-single-form/) |

**Parked (preserved, revivable):**
- R2-03 Duplicate-first — revive if recurring-billing speed becomes the priority. [→](iterations/round-2/03-duplicate-first/)
- R2-04 Direct-on-document — revive if WYSIWYG/branding emphasis returns; resolve compliance-home first. [→](iterations/round-2/04-direct-document/)

## What Validate Design should scrutinise (B-specific)
- Parse-failure / low-confidence path: how cleanly does B hand off to A?
- How edited line items round-trip after a parse (re-typing vs structured edit).
- Compliance "confirm" affordance — is it unmissable before activate?
- First-time users who don't know what to type — is the fallback discoverable?

## Guardrail
Survivors stay **lo-fi** into Validate Design. Any fidelity uplift (real copy, brand colour,
snapshot-edit) happens later at the Prototype step; UX changes re-enter via change-impact.
