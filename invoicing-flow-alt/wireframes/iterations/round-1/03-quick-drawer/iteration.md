---
# 03 Quick-Create Drawer — round 1
updated: 2026-06-24 · Prateek
status: pending-review
baseline: direct_user flow docs + screenshots (captured June 2026)
lineage: original
reason: —
revival trigger: If screen real estate or multitasking becomes a priority concern
screen↔node map:
  - "Invoices list (dimmed)" → A
  - "Right drawer" → D
  - "Stepper steps 1–4" → S1–S4
  - "Drawer closes · list row appears" → L / J

## Mental model
**Invoice creation as a task, not a takeover.** A right drawer (65% width) slides in over the invoice list, which stays visible and dimmed behind. Completed steps collapse into summary chips; next step reveals below. A thumbnail preview strip at the bottom of the drawer gives a live sense of the document without committing to a split layout. When submitted, the drawer closes and the new row appears in the list — the user never left.

## Hypothesis
Full-screen modal creation breaks context — users lose sight of the list they were looking at. A drawer preserves spatial continuity: the new invoice appears in the same place the user is already looking at. For finance teams who create many invoices in a session, this reduces the "where was I?" re-orientation cost.

## Pros
- Context preserved — list stays visible behind the drawer; user never loses orientation
- Collapsed step summaries reduce form length and confirm what's done
- Thumbnail preview is lower-commitment than a full split panel — less overwhelming
- New invoice row appears naturally in the list on close — satisfying flow
- Consistent with drawer patterns used elsewhere in dashboards

## Cons
- 65% width is tight for the full split-panel preview — thumbnail is a compromise
- Longer forms (Step 2 items, Step 3 compliance) still require significant scrolling inside drawer
- On smaller viewports the drawer may cover the list entirely — negating the context benefit
- Step-by-step still present — same wizard friction, just in a narrower container

## Best for
Users who work through batches of invoices in a session and need to keep the list in view. Also good for teams where an admin creates invoices while a manager reviews the list state simultaneously.
