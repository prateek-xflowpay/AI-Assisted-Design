---
render_with_liquid: false
---
# Iterations Ledger — Invoicing Flow

One row per iteration across all rounds. Use this to find parked approaches.

| Round | ID | Model | Status | One-line reason | Revival trigger | Link | Date |
|-------|-----|-------|--------|-----------------|-----------------|------|------|
| R1 | 01 | Single-page form | superseded | Folded into R2-01 (smart single form) on fresh restart | Revisit if R2 abandons single-page direction | [→](iterations/round-1/01-single-page-form/) | 2026-06-24 |
| R1 | 02 | Document-direct | superseded | Reborn as R2-04 (direct-on-document) with region popovers + checklist | — | [→](iterations/round-1/02-document-direct/) | 2026-06-24 |
| R1 | 03 | Quick-create drawer | parked | Not carried into R2; strong for batch/multitask context | Multitasking / batch creation workflow | [→](iterations/round-1/03-quick-drawer/) | 2026-06-24 |
| R1 | 04 | Accordion card stack | parked | Prototyped once, but still step-based — counter to fewer-steps driver | High error-rate in step nav; revisit if guided structure needed | [→](iterations/round-1/04-accordion-steps/) | 2026-06-24 |
| R2 | 01 | Smart single-screen form | selected (fallback) | Carried as the form B degrades to + default for new users | — | [→](iterations/round-2/01-smart-single-form/) | 2026-06-24 |
| R2 | 02 | Command-bar / conversational | selected (primary) | Prateek's lead choice — type the invoice; form becomes a confirmation surface | — | [→](iterations/round-2/02-command-bar/) | 2026-06-24 |
| R2 | 03 | Duplicate-first / template gallery | parked | Not carried; revive if recurring-billing speed becomes priority | Recurring-billing speed is the priority | [→](iterations/round-2/03-duplicate-first/) | 2026-06-24 |
| R2 | 04 | Direct-on-document editing | parked | Not carried; bold but compliance-home unresolved | WYSIWYG/branding emphasis returns | [→](iterations/round-2/04-direct-document/) | 2026-06-24 |

---

## Provenance notes

- **Round 2 (2026-06-24): fresh restart**, scoped by Prateek to a single driver — *too many steps / drop-off*. R1 was set aside (not deleted): 01/02 superseded by sharper R2 models, 03/04 parked with triggers. All R1 folders remain intact under `iterations/round-1/`.
- No `ia.md` or `user-stories.md` available — graceful degrade applied (per `lofi-wireframes` SKILL.md). Working from `direct_user` flow docs (`invoices/invoice-create.md`, `invoices/invoices-list.md`) + screenshots (June 2026) and the `invoice-listing` / `invoice-detail` page-snapshots.
- Baseline carried into every R2 model: full-screen modal, real building blocks (partner picker, line-item table, compliance fields = Purpose Code + Transaction Type, payment-method toggles, live PDF preview, template/branding). Ingress unchanged: `/invoices` → "Add Invoice ▾" → "Create Invoice".
- IA ingress is **not** diverged by any R2 model — all attach at the same point. (Model B adds a command-bar entry *within* the same modal, not a new ingress.)

## Surfaces flagged for Validate Design
- R2-01: collapsed "More details" must not hide required compliance changes; inline non-blocking validation.
- R2-02: parse-failure / low-confidence fallback path; how edited items round-trip.
- R2-03: stale carried-over values (old due terms/amount); invalid source-partner on activate.
- R2-04: compliance has no natural home on the document — footer checklist must make it unmissable; region-clickability discoverability.
