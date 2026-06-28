# 01 Smart Single-Screen Form — round 2
updated: 2026-06-24 · Prateek
status: pending-review
baseline: invoice-listing + invoice-create flow doc & screenshots (captured June 2026)
lineage: original (R2 fresh restart; not derived from R1)
reason: directly attacks the "too many steps / drop-off" driver by removing step navigation entirely
revival trigger: —
screen↔node map: single screen (form-panel) ↔ nodes B–K; banners ↔ O,P

## Mental model
Form-first, but **one page instead of four steps**. The user fills a single scrollable form. Cognition load is reduced by *progressive disclosure*: only the three things every invoice truly needs — Client, Items, Payment — are visible. Everything else (invoice #, dates, purpose code, transaction type, T&C, place of supply) is pre-filled with smart defaults and folded into a collapsed "More details" section the user opens only to override.

## Hypothesis
Most drop-off comes from the 4-step wizard making a short task *feel* long, and from compliance fields appearing as required work when they could be defaulted. Collapsing to one page with sensible defaults gets a typical invoice to "Activate" in one scroll, with no Next/Back and no locked steps.

## Pros
- Fewest possible navigation actions; Activate always in view.
- Smart defaults remove the perceived burden of compliance fields.
- Easy to scan the whole invoice state at once — no hidden steps.
- Closest to the current building blocks, so lowest build risk.

## Cons
- A long page can feel heavy on first sight if defaults aren't trusted.
- Risk of users missing the collapsed "More details" when they *do* need to change a purpose code.
- Validation must be inline and non-blocking, which is more design work than step gates.

## Best for
The common case: a direct user creating a familiar invoice for a known partner who wants to be done quickly.
