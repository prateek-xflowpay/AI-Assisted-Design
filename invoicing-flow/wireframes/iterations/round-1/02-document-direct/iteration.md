---
render_with_liquid: false
# 02 Document-Direct — round 1
updated: 2026-06-24 · Prateek
status: pending-review
baseline: direct_user flow docs + screenshots (captured June 2026)
lineage: original
reason: —
revival trigger: —
screen↔node map:
  - "Invoices list" → A
  - "Dark stage with invoice doc" → D–E
  - "Floating edit panel" → F–F4
  - "Activate Invoice" → J

## Mental model
**The invoice IS the interface.** Instead of filling a form that generates a PDF, the user works directly on the invoice document. The PDF preview is front and centre (on a dark stage). Clicking any region (header, client, items, dates, payment) opens a focused floating panel anchored to that spot. The top toolbar tracks which sections are complete.

## Hypothesis
The main cognitive friction in the current wizard is the separation between form fields and the final document. Users must mentally translate "Invoice Date field" into "where it appears on the invoice." Making the document clickable eliminates that translation — users see exactly what they're editing and why.

## Pros
- Zero translation between form and output — WYSIWYG experience
- Users can edit sections in any order (non-linear, unlike wizard)
- Progress visible at a glance in toolbar
- Naturally surfaces "what does this field do on the invoice"
- Branding edits feel immediate and satisfying

## Cons
- Document region click targets may be unclear to new users — discoverability risk
- Floating panel anchoring complex to implement (especially on small screens)
- Compliance fields (not shown on invoice) need a non-document home — awkward in this model
- Template selection (Theme Modal) still requires a pre-step modal — small inconsistency

## Best for
Design-conscious users who care about what the invoice looks like and want to work more intuitively. Also good for businesses that customise branding per invoice. Less suited for compliance-heavy workflows where the hidden regulatory fields are important.
