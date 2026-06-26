# Requirements — Create Invoice Flow
Date: 2026-06-25
PRD version: v1.0 · June 2026
Persona(s): DU — Direct User (Exports)
Figma file: https://www.figma.com/design/IVa60gc9mNHFus7mnqXN6N/Untitled?node-id=0-1&p=f&t=PTzsffs8LYB4nlfu-11
Planned route: Research → User Stories → Wireframes → Validate → UX Copy → Prototype → Canvas

---

## Problem

The create invoice modal converts at 20.75% (395 of 1,904 unique users over 90 days). Drop-off concentrates at Partner Selection (–52%) and Invoice Items (–41%). Six confirmed Jira bugs spread across the modal are direct causes. This project scopes to three design-ready bugs — a layout bug in the Purpose Code field (XFLOW-5799), missing passthrough fee information in the Payment Methods step (XFLOW-9620), and a disconnect between the payment method toggles and the live invoice preview (XFLOW-9601) — and additionally addresses UX friction at the two highest-drop steps (Client and Products) which are confirmed to have design-side causes.

## Personas

- Targeted: DU — Direct User (Exports)
- Must remain unaffected: PU, CU — verified at Validate Design

## Success Metrics

- Overall modal → submit conversion — baseline: 20.75% — target: 25%+ — measured via PostHog 6-step funnel, 60 days post-ship
- Invoice Details step completion rate — baseline: ~83% (–17% drop at this step) — target: 90%+ — measured via PostHog funnel step completion

## In Scope

- XFLOW-5799 — Constrain the Purpose Code select to container width; audit all selects in the flow for the same layout issue
- XFLOW-9620 — Add inline fee info in the Payment Methods step explaining who bears the passthrough fee by default; link to Settings
- XFLOW-9601 — Bind the invoice preview to real-time payment method toggle state; bank details must disappear from preview the moment Bank is toggled off
- **Step 1 (Client) friction reduction** — −52% drop at partner selection; improve partner lookup speed and empty-state handling (US-6)
- **Step 2 (Products) friction reduction** — −41% drop at item entry; reduce inline editing friction for the typical single-item case (US-7)
- **Overall flow paradigm** — explore whether the 4-step wizard structure best serves the user's mental model; wireframe exploration may propose structural alternatives (US-8, nice-to-have)

## Out of Scope

**Excluded** (design ignores):
- XFLOW-9609 — Card Payments partner filter (descoped by designer)
- XFLOW-8811 — Limit Order conflict dialog CTA (insufficient context to design confidently)
- XFLOW-9640 — Mixed-method balance recalculation (buyer-side checkout link, not invoice creation modal)
- 400_ERROR_ACTIVATE_INVOICE + session recording review (engineering/research tracks, not design)
- Upload invoice flow, invoice details page, OCR, navigation renaming, reconciliation flow, invoice listing/search

## Existing Product Context

The create invoice modal is a full-screen wizard (calc(100dvh - 48px)) with a live PDF preview panel on the right. It has 4 steps in order: **Client** (partner selection) → **Products** (line items) → **Invoice Details** (purpose code, dates, terms) → **Payment Methods** (bank/card toggles + payment link enable). Every form change auto-saves to the backend (850ms debounce) and updates the preview (100ms debounce). Entry points: Invoices list button, Reconcile flow, Limit Order creation flow, home page payment widget.

Step order is sourced from context docs, not PRD PostHog funnel labels.

## Screens Affected

- Step 1 — Client: friction reduction (partner lookup, empty state) — US-6
- Step 2 — Products: friction reduction (item entry UX) — US-7
- Step 3 — Invoice Details: XFLOW-5799 (Purpose Code select layout + full-step select audit)
- Step 4 — Payment Methods: XFLOW-9620 (fee explanation), XFLOW-9601 (toggle-preview binding)
- Live Preview panel (right): XFLOW-9601 (real-time state sync with payment method toggles)
- Overall flow structure: paradigm exploration in wireframes — US-8

## Open Questions

None.

## Constraints

- All changes strictly within the create invoice modal — no navigation or structural changes outside the modal
- XFLOW-9609 explicitly descoped — no partner filtering pattern required in this pass
- Step naming and order: follow context docs throughout (Client → Products → Invoice Details → Payment Methods)
- Scope expansion (US-6, US-7, US-8) added 2026-06-25 after designer review of PostHog drop-off data
