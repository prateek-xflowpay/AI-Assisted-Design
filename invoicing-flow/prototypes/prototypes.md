# Prototypes — Invoicing Flow
Date: 2026-06-24 · Persona: direct_user (merchant / finance admin)

## Built

- **Command Bar (Model B)** — lineage: `wireframes/iterations/round-2/02-command-bar/` (R2 selected, primary) — file: `variants/command-bar/prototype.html`
  - Hypothesis: describing an invoice in one line and confirming it (form → confirmation surface) cuts the 4-step wizard to one screen and reduces drop-off.
  - Trade-off: speed depends on parse reliability; degrades to the Model A blank form on low confidence / new partners.
  - Copy: real, from `ux-copy.md`. Harness covers happy path + 6 edge/branch states (3 tagged "new surface").

- **Accordion Card Stack** — lineage: `wireframes/iterations/round-1/04-accordion-steps/` — file: `variants/accordion-card-stack/prototype.html`
  - status: **superseded by R2** — built in Round 1 before the fewer-steps re-design; still step-based. Kept for reference, not carried to handoff.

## Fidelity check

- **Command Bar:** preserves R2-02's validated* flow nodes, ingress, and declared states; visual + copy uplift only, no UX drift. (*Validate Design skipped — see caveat below.)
- **Accordion:** preserved from R1; not part of the current re-design line.

## Stakeholder Review

Not yet shared. Next: confirm the Command Bar prototype with Prateek → share with stakeholders. Stakeholders select one → Step 9 (prototype-to-canvas).

## Outcome

Pending stakeholder review. Selection: —

## Visual Design Handoff

Not yet initiated. Notes to carry forward for **Command Bar**:
- **Validate the 3 "new surface" states first** (partner-not-matched, low parse confidence, save error) — Step 6 was skipped.
- Parse → structured-field round-trip: how a user edits parsed line items (re-type vs. structured edit).
- Compliance "confirm" affordance (Purpose code / Transaction type) must be unmissable before activate.
- Fallback discoverability: "Start from a blank form" must be obvious to first-time users.
- Currency in the command-bar placeholder: spell the currency (avoid "$" implying USD-default) per ux-copy open question.
