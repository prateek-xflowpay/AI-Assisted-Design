---
# 01 Single-Page Form — round 1
updated: 2026-06-24 · Prateek
status: pending-review
baseline: direct_user flow docs + screenshots (captured June 2026)
lineage: original
reason: —
revival trigger: —
screen↔node map:
  - "Invoices list" → A
  - "Theme modal" → C
  - "Single-page form (all sections)" → D–H
  - "Activate Invoice" → K
  - "Invoice detail" → L

## Mental model
**One-page, scroll-to-complete.** All 4 wizard steps collapsed into a single scrollable form inside the full-screen overlay. Sections are clearly labelled (1–4) with dividers. No step navigation, no Back/Next buttons. The user fills fields in natural reading order and submits at the bottom.

## Hypothesis
Removing the wizard structure reduces context-switching overhead. Experienced users (who run invoicing repeatedly) don't need guided step-by-step — they know the fields. A single form lets them tab through quickly, reference earlier sections without Back navigation, and see the overall completion state at a glance.

## Pros
- Zero back-navigation cost — any field is reachable by scrolling
- Compliance fields (Transaction Type, Purpose Code) are not hidden on a later step — visible earlier reduces surprise
- Simpler mental model for repeat users
- Same split-panel layout as today — preview familiarity preserved
- "Activate" button always visible in footer — no step gating

## Cons
- Form is long — users might feel overwhelmed on first use
- No progressive disclosure — all fields visible even before partner is selected
- Scroll position management (e.g. auto-scroll after partner selection) needs design care
- Less natural for rare/first-time users who benefit from guided steps

## Best for
Power users and finance teams who create invoices frequently and know the fields well. Not ideal as the only entry point for new users.
