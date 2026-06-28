---
---
# Research — Create Invoice Flow
Date: 2026-06-25
Persona(s): DU — Direct User (Exports)

## Research Plan
Questions:
1. Where in the create invoice modal are users abandoning, and does it correlate with the three in-scope bugs?
2. How do comparable products handle (a) inline fee transparency at payment method selection and (b) live preview sync with form toggle state?

Sources used: PostHog (live funnel) · Mobbin (market patterns)
User research: Not conducted — confirmed out of scope for this session.

Note: PostHog event names do not match context doc step names — context docs are the source of truth for step naming and order (Client → Products → Invoice Details → Payment Methods). PostHog funnel drop-off numbers are treated as directionally valid observations only.

---

## What the data tells us

### PostHog — 90-day funnel (Mar 27 – Jun 25 2026)

| Step | Users entered | Drop |
|------|--------------|------|
| Client (Partner Selection) | 1,904 | −52% |
| Products (Invoice Items) | ~915 | −41% |
| Invoice Details | ~540 | −17.1% |
| Payment Methods | ~448 | −15.5% |
| Submit | 395 | −2.7% |
| **Overall** | **395 / 1,904** | **20.75%** |

Steps 3 and 4 (Invoice Details and Payment Methods) together account for ~145 users lost. These are the exact steps the three in-scope bugs live in. The two largest drops (Client −52%, Products −41%) are outside this project's scope.

### Mobbin — Market patterns

**Pattern A — Fee transparency at payment method selection (for XFLOW-9620)**

Three approaches surfaced, ranked by friction:

- **A1 — Inline sub-text per row** (Wise, PayPal, Deel): fee copy sits directly under the payment method label — always visible, no interaction required. [Wise](https://mobbin.com/screens/38777d12-6cdb-4ed8-a8ad-2b30aeaa7de0) · [PayPal](https://mobbin.com/screens/8e97eee4-ddb5-410d-b567-a590ce83dd17) · [Deel](https://mobbin.com/screens/8b442ff3-842a-4e75-8a8a-b5022bd85a4d)
- **A2 — Group-level ⓘ with fee total in group header** (Wise): fee summary visible in the group label; detail on tap. [Wise](https://mobbin.com/screens/50b65c13-495d-43ed-9a30-29f4ba90d580)
- **A3 — Fee passthrough toggle + live preview** (Whop): "Pass processing fees on to customer" checkbox updates invoice total in preview. Closest structural analogy to `processingFeeIndicator` — but that field is plan-level read-only on Xflow, so this maps to display/disclosure only, not a user-facing toggle. [Whop](https://mobbin.com/screens/5099041b-196e-462b-ab86-10effe394758)

**Pattern B — Form-to-preview sync on payment method toggles (for XFLOW-9601)**

- **B1 — Synchronous preview update** (Stripe, Mercury, Revolut Business, HoneyBook): when a payment method toggle changes, the preview panel updates immediately — no save required. Payment method rows toggled off disappear from the preview's "Pay via" block. [Stripe flow](https://mobbin.com/flows/03c71446-31eb-497b-b715-3419cf8cd922) · [Mercury](https://mobbin.com/screens/2986eb22-0e3d-4129-8718-0cbb560d3922) · [Revolut Business](https://mobbin.com/screens/96f25163-6586-442c-93dc-a627339d1410) · [HoneyBook flow](https://mobbin.com/flows/47602473-b190-4974-a2bc-4ce3da008632)
- **B2 — Multi-surface preview tabs** (Stripe, Whop): Invoice PDF / Email / Hosted Page tabs all reflect the same toggle state simultaneously. Directly relevant — Xflow's preview is a PDF, and the bank details block in the PDF is what must disappear when Bank is toggled off. [Stripe](https://mobbin.com/screens/56723e31-70fe-484a-8c2d-6600dd3eaeaa) · [Whop](https://mobbin.com/screens/5099041b-196e-462b-ab86-10effe394758)

---

## Patterns worth considering

1. **Inline sub-text (A1)** — Wise, PayPal, Deel — fee always visible in the row, zero interaction cost — directly applicable to surfacing `processingFeeIndicator` state under the card payment option in Payment Methods
2. **ⓘ group header (A2)** — Wise — summary visible, detail on demand — fallback if fee explanation needs more room than a single line
3. **Synchronous preview update (B1)** — Stripe, Mercury, Revolut Business, HoneyBook — universal standard; toggle off = immediate removal from PDF preview — direct solution model for XFLOW-9601
4. **Multi-surface preview tabs (B2)** — Stripe, Whop — all output surfaces (PDF, email, hosted page) reflect the same state — useful framing for how the Xflow PDF preview should be treated as a live output, not a static thumbnail

---

## Design implications

**XFLOW-5799** — The −17.1% drop at Invoice Details has a broken select visible on-screen. Fixing the layout constraint removes an immediately visible friction point before the user even interacts with the field. Full select audit across the flow is warranted — the same overflow bug may exist elsewhere.

**XFLOW-9620** — `processingFeeIndicator` is plan-level read-only, so this is a disclosure problem, not a control. Pattern A1 (inline sub-text under the card option) is the right fit: one short line, always visible, no tooltip or modal. Pattern A2 (ⓘ) is a valid fallback if the explanation needs more room or links to Settings.

**XFLOW-9601** — Market consensus is unambiguous: preview must update synchronously when a toggle flips. The current behaviour (bank details persist in the PDF preview after Bank is toggled off) signals to the user that their action didn't register — a trust problem at the final step before submit. This is a likely contributor to the −15.5% Payment Methods drop.

---

## What we still don't know

- **Why users abandon at Payment Methods** — Mobbin patterns are directionally strong, but there is no session recording or interview data to confirm whether fee confusion or preview confusion is the primary driver. Flagged gap; no qualitative research in scope for this session.
