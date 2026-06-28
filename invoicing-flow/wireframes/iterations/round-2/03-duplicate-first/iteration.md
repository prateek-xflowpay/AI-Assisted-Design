---
render_with_liquid: false
---
# 03 Duplicate-First / Template Gallery — round 2
updated: 2026-06-24 · Prateek
status: pending-review
baseline: invoices-list + invoice-create flow docs & screenshots (captured June 2026)
lineage: original (R2 fresh restart)
reason: removes most data entry for repeat invoices by starting from an existing one; cuts "steps" via reuse
revival trigger: —
screen↔node map: chooser ↔ B–C; editor ↔ F–I; preview ↔ G

## Mental model
Reuse-first. The blank form is no longer the default starting point — a *chooser* of recent invoices and saved templates is. Picking a source clones a fully valid invoice; the user edits only the deltas (typically amount and dates). Carried-over fields are explicitly labelled "kept" so nothing feels hidden.

## Hypothesis
A large share of invoices closely resemble a previous one to the same partner. If the system starts from "last time" instead of from blank, the user's job shrinks to a couple of edits — which is fewer real steps than re-deriving every field, and sidesteps compliance friction because those values carry over correctly.

## Pros
- Eliminates most data entry for recurring/repeat invoices.
- Compliance fields carry over correctly — fewer chances to get them wrong.
- "Kept vs updated" labelling builds trust and makes the diff scannable.
- Encourages saved templates, compounding the speed-up over time.

## Cons
- Weak for genuinely new partners / first-ever invoice (must fall back to blank form).
- Risk of stale values carrying over silently (old due terms, wrong amount).
- Adds a chooser step before editing — net win only when a good source exists.

## Best for
Established direct users with recurring partners and repeat billing; pairs naturally with Model A as the blank-form fallback.
