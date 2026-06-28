---
render_with_liquid: false
---
# 02 Command-Bar / Conversational — round 2
updated: 2026-06-24 · Prateek
status: pending-review
baseline: invoice-create flow doc & screenshots (captured June 2026)
lineage: original (R2 fresh restart)
reason: most radical reduction of "steps" — replaces data entry with a single typed sentence + confirmation
revival trigger: —
screen↔node map: command bar ↔ B–D; parsed cards ↔ E–L; preview ↔ J

## Mental model
Language-first. Instead of navigating a form, the user *describes* the invoice in one line ("Invoice Acme Corp $5,000 for Software Development, due Aug 7"). The system parses it into structured fields, matches the partner, and auto-suggests compliance values. The UI's job flips from *collecting* data to *confirming* it.

## Hypothesis
For experienced users who know exactly what they want, the fastest path is to say it once. If parsing is reliable and compliance is auto-suggested with a clear "confirm" affordance, a whole invoice becomes type → glance → activate — far fewer steps than any form.

## Pros
- Potentially the lowest time-to-activate for repeat/expert users.
- Naturally accommodates partial input — fills what it can, asks only for the rest.
- Compliance framed as "confirm this" rather than "go find this."
- Differentiated, memorable; pairs well with a blank-form fallback.

## Cons
- Parsing reliability is a real risk; bad parses erode trust fast.
- New users may not know what to type — needs strong examples / scaffolding.
- Editing structured items by re-typing is awkward; still needs a fallback form.
- Higher build + model cost than the other approaches.

## Best for
High-volume direct users issuing similar invoices repeatedly, and a "fast lane" entry that always degrades gracefully to the single form (Model A).
