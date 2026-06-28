---
render_with_liquid: false
---
# 04 Direct-on-Document Editing — round 2
updated: 2026-06-24 · Prateek
status: pending-review
baseline: invoice-create flow doc, live-preview section & screenshots (captured June 2026)
lineage: original (R2 fresh restart). Note: shares the "document is the interface" spirit with R1-02 (discarded) but is rebuilt fresh with region popovers + a footer checklist rather than a step model.
reason: collapses the form/preview split into a single direct-manipulation surface — zero steps, spatial editing
revival trigger: —
screen↔node map: document regions ↔ C–L; footer checklist ↔ J,M; popover ↔ D,L

## Mental model
Direct manipulation / spatial. There is no separate form and no preview — the invoice document *is* the editing surface. Every region (Bill-To, dates, line items, branding, payment & compliance) is clickable and opens a small inline popover. Required regions are tracked by a checklist in the footer instead of by step gates.

## Hypothesis
The current flow forces users to mentally map form fields to where they land on the invoice. If they edit the invoice directly, the mapping disappears, the live preview becomes redundant (saving screen space), and "steps" dissolve into "click the thing you want to change." WYSIWYG reduces both step count and cognitive translation.

## Pros
- Zero steps; what you see is exactly what the partner gets.
- Removes the form↔preview translation entirely; reclaims the split-screen space.
- Naturally surfaces branding/template as part of the same surface.
- Strong fit for visual / detail-oriented users.

## Cons
- Compliance fields have no natural "place" on the document — risk of being buried in a footer popover (must be made unmissable via the checklist).
- Discoverability: users must learn that regions are clickable.
- Harder to enforce required-field validation than an explicit form; relies on the checklist.
- Higher build complexity (region hit-targets, popovers, responsive document).

## Best for
Users who think visually and care about the final document, and lower-volume invoicing where polish matters more than raw speed. Weakest on the compliance-clarity dimension — flag for Validate Design.
