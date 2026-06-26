---
# Accordion Card Stack Prototype
updated: 2026-06-24 · Prateek
status: built — pending stakeholder review
lineage: wireframes/iterations/round-1/04-accordion-steps/
source-flow: wireframes/iterations/round-1/04-accordion-steps/flow.mermaid
baseline: dashboard-context (no page-snapshots present — gap noted)
hypothesis: Showing all steps as locked cards upfront reduces "how much longer?" anxiety while inline Continue validation catches errors earlier than a full-form submit failure.
trade-off: Locked cards may frustrate users who try to click ahead; auto-scroll to the newly opened card on Continue needs careful implementation to feel natural at all viewport heights.
---

## Fidelity check

Prototype preserves the validated UX from Iteration 04:
- ✓ 4 accordion cards, only one open at a time
- ✓ Locked cards show ghost previews of upcoming fields
- ✓ Continue button inline per card (no global Back/Next bar)
- ✓ Collapsed cards show summary + Edit link
- ✓ Activate Invoice button in footer, disabled until all 4 cards done
- ✓ Split-panel with live invoice preview (updates at each step)
- ✓ Template modal pre-step (first-time user)

No UX drift detected — prototype is a visual/interaction uplift of the validated lo-fi only.

---

## State harness

| Button | State | Tag | Notes |
|--------|-------|-----|-------|
| Jump to Step 2 — Items | Cards 1 done, 2 open | validated | Tests editing after Client step |
| Jump to Step 4 — All filled | Cards 1–3 done, 4 open | validated | Activate button enabled |
| Validation: no items | Step 2, items-error shown | validated | Error on Continue with empty items |
| Save / API error banner | API error banner | new surface | Not yet validated — candidate for Validate |
| Currency VBAN unavailable | Warning banner | new surface | Not yet validated — candidate for Validate |
| Activate → Success | Success dialog | validated | Partner activated path |
| Activate → Partner Verifying (Draft) | Draft saved dialog | validated | Partner verifying path |
| Reset to Invoices list | Invoices list screen | validated | Clean slate |

**New surfaces flagged for Validate Design:**
- Save / API error banner (mid-creation save failure)
- Currency VBAN unavailable banner (MCY currency without VBAN)

---

## Screens built (flow node map)

| Screen / State | Flow node | Notes |
|---|---|---|
| Invoices list | A | Full list with Add Invoice split button |
| Template modal | C | 3 template options, remember checkbox |
| Create overlay — Card 1 open | C1 | Partner dropdown, info bar, Continue |
| Create overlay — Card 1 done, Card 2 open | C1ok / C2 | Summary chip, items table |
| Create overlay — Card 2 done, Card 3 open | C2ok / C3 | Details + compliance fields |
| Create overlay — Card 3 done, Card 4 open | C3ok / C4 | Payment toggles, T&C |
| Activate → Success | L | Success dialog |
| Activate → Draft (verifying) | M | Draft saved dialog |
| Validation error — items | C2err | Inline error on Continue |
