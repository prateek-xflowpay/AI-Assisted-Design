---
render_with_liquid: false
---
# User Stories — Create Invoice Flow
Date: 2026-06-25
Persona(s): DU — Direct User (Exports)
Provenance: requirements + research (PostHog funnel · Mobbin market patterns)

---

## Core Stories

**US-1 — Purpose Code select renders within container** `[DU]`
*(XFLOW-5799)*

When I reach the Invoice Details step and open the Purpose Code field, I want the dropdown to stay within the form container, so the step looks correct and I can make my selection without the UI breaking.

Acceptance criteria:
- Purpose Code select is constrained to its container width and does not overflow at any supported viewport size
- The selected value is readable (not clipped) within the field
- All other select fields across all 4 steps are audited; any with the same overflow behaviour are fixed in the same pass

— why: −17.1% drop at Invoice Details [PostHog]

---

**US-2 — Card processing fee ownership is visible before sending** `[DU]`
*(XFLOW-9620)*

When I enable card payments in the Payment Methods step, I want to see who bears the card processing fee, so I know what my buyer will be charged before I send the invoice.

Acceptance criteria:
- A fee ownership indicator is visible inline with or beneath the card payment option when card is enabled
- Indicator reflects the plan's `processingFeeIndicator` in plain language: `user` → fee borne by me; `partner` → fee borne by buyer; `shared` → fee split between both
- Indicator is not shown when card is disabled
- A link to Settings is present — the field is read-only; users cannot change the fee plan from this modal

— why: −15.5% drop at Payment Methods; fee ownership is invisible before send [PostHog + research]

---

**US-3 — Payment method toggles update the invoice preview in real time** `[DU]`
*(XFLOW-9601)*

When I toggle any payment method on or off in the Payment Methods step, I want the invoice PDF preview to reflect that change immediately, so I can verify what my buyer will see before sending.

Acceptance criteria:
- Bank toggled off → bank account details removed from PDF preview (≤ 100ms)
- Bank toggled on → bank account details appear in PDF preview (≤ 100ms)
- Card toggled off → card payment option removed from PDF preview (≤ 100ms)
- Card toggled on → card payment option appears in PDF preview (≤ 100ms)
- At no point during the step does the preview show a state that doesn't match current toggle selections

— why: preview-toggle disconnect signals to user that their action didn't register [research — universal market standard is synchronous update]

---

**US-6 — Partner selection is fast and unblocked** `[DU]`

When I reach the Client step, I want to find and select my partner with as few actions as possible, so I'm not slowed down before the invoice has started.

Acceptance criteria:
- Recently used / most-frequent partners surface at the top without searching
- If only one partner exists, the field is pre-filled (or the step auto-advances)
- If no partners exist, the empty state gives a clear inline path to add one without abandoning the flow or losing invoice progress

— why: −52% drop at Client step [PostHog]

---

**US-7 — Adding items is lightweight for the typical case** `[DU]`

When I'm in the Products step, I want to enter one or a few items without navigating multiple inline editing states per row, so adding items doesn't feel like managing a spreadsheet.

Acceptance criteria:
- A single item can be entered and confirmed without a per-row Save/Cancel gate blocking Next
- Frequently used catalogue items are surfaced for quick selection
- I can add items and proceed without the row-level edit state feeling like a form within a form

— why: −41% drop at Products step [PostHog]

---

## Nice-to-Have

**US-4 — Fee indicator copy covers all plan configurations** `[DU]`

When my fee plan is set to a shared or partner-borne configuration, I want the indicator to still be clearly worded, so I'm not confused by copy that only accounts for the user-pays case.

Acceptance criteria:
- Copy is validated and distinct for all 3 `processingFeeIndicator` values (user / partner / shared)
- Shared state has explicit copy — not a generic "processing fee applies"

---

**US-8 — The create flow is structured around how I naturally think about invoices** `[DU]`

When I create an invoice, I want the flow structure and step grouping to match my natural mental model (who, what, when, how to pay), so I'm not translating between my intent and the tool's structure.

Acceptance criteria:
- Required fields are clearly distinguished from optional ones — I'm never blocked by optional complexity
- Step grouping is logically coherent from the user's perspective
- The typical case (one partner, a few items, standard bank payment) completes with the minimum number of decisions

---

## Out of Scope

**Excluded:**
- US-5 — Template selection as a blocker: not applicable — template is prompted only on first use and re-uses previous selection thereafter; not a friction point
- XFLOW-9609 — Card Payments partner filter: descoped by designer
- XFLOW-8811 — Limit Order conflict dialog CTA: insufficient context; parked
- XFLOW-9640 — Mixed-method balance recalculation: buyer-side checkout link, not the create invoice modal
- 400_ERROR_ACTIVATE_INVOICE + session recording: engineering/research tracks, not design

**Design-forward** (pattern must accommodate; not built now):
- None. All in-scope fixes are self-contained; US-8 explores paradigm options but does not foreclose the current structure.

---

Stories count: 5 core, 2 nice-to-have, 5 out of scope
