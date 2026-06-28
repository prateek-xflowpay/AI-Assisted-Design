---
render_with_liquid: false
# 04 Accordion Card Stack — round 1
updated: 2026-06-24 · Prateek
status: pending-review
baseline: direct_user flow docs + screenshots (captured June 2026)
lineage: original
reason: —
revival trigger: If step-by-step validation on blur is a priority (e.g. high error rate in current wizard)
screen↔node map:
  - "Invoices list" → A
  - "Overlay (all cards)" → D
  - "Card 1–4 open/collapsed" → C1–C4
  - "Activate" → K

## Mental model
**Step-free card progression.** All four sections are visible as stacked cards in the full-screen split-panel layout. Only one card is open at a time; the others are locked (greyed, showing a preview of their fields). Clicking "Continue" inside a card validates inline and auto-advances — no Back/Next bar at the bottom. Collapsed cards show a summary and an "Edit" link. All four cards must be complete before "Activate Invoice" enables in the footer.

## Hypothesis
The current tab-based wizard hides later steps entirely, creating a "how much longer?" anxiety. Showing all sections upfront (even locked) sets clear expectations and reduces perceived length. Inline validation per-section (on "Continue") catches errors earlier, without a full-form submit failure. The result feels like a form, not a wizard.

## Pros
- All steps visible at once — user knows exactly what's coming
- Inline per-section validation catches errors before the user moves on
- Edit link on collapsed cards is faster than wizard Back navigation
- Preserves the split-panel preview familiar from the current design
- Compliance fields visible in Card 3 preview even when locked — reduces surprise
- Works well on larger screens; no horizontal scroll

## Cons
- "Activate" button locked until all sections done — no shortcut to submit early
- Users may try to click on locked cards and feel frustrated if it's not clear why
- If Card 3 is long (all compliance fields), it may feel like the form suddenly grew
- Scroll management (auto-scroll to newly opened card) needs careful implementation

## Best for
New-to-moderate users who benefit from seeing the full scope upfront. Also good for compliance-sensitive organisations where the Purpose Code step surprises users in the current wizard's Step 3.
