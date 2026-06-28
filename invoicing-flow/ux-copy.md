---
---
# UX Copy — Invoicing Flow (Re-design)
Date: 2026-06-24
Persona(s): Direct User (DU)
Based on: selected R2 approaches — **B · Command-bar / conversational** (primary) + **A · Smart single form** (fallback/foundation)
Voice: per `../../brand-voice.md` — lean hard to Efficiency Seeker; Creator flavour only in empty/success; never in errors/compliance. Domain terms from `.context/exports/direct_user/meta/glossary.md` (Partner, Receivable, Purpose Code, Transaction Type, Payment Link, VBAN, MCY).

> Note: copy written without Validate Design (Step 6 skipped). States below are taken from the R2 Mermaid flows + the baseline `invoice-create.md` state table. Items marked **[unvalidated]** correspond to surfaces flagged in the prototype harness.

---

## Shared copy (applies across B and A)

| Location | Element | Copy |
|----------|---------|------|
| Modal header | Title | Create invoice |
| Modal header | Close confirm (draft exists) | Saved as draft. You can finish it anytime from Invoices. |
| Partner field | Label | Partner |
| Partner field | Placeholder | Search partners |
| Partner field | Inline action | + Add new partner |
| Partner field | Helper | The customer you're billing. Sets the invoice currency. |
| Partner field | Error | Select a partner to continue. |
| Items table | Column headers | Item · Qty · Unit price · Amount |
| Items table | Add row | + Add item |
| Items table | Empty error | Add at least one item. |
| Amount field | Error | Enter an amount greater than 0. |
| Currency | Helper (MCY) | Currency is set by the partner. |
| Purpose Code | Label | Purpose code |
| Purpose Code | Helper (compliance) | Required by RBI to classify this cross-border payment. |
| Transaction type | Label | Transaction type |
| Payment methods | Section label | How your partner can pay |
| Payment methods | Bank transfer | Bank transfer (VBAN) |
| Payment methods | Card | Card payment |
| Payment methods | Payment link toggle | Include a payment link on the invoice |
| Card fee banner (`user`) | Body | Card fees are charged to you. Change this in Settings › Fees. |
| Card fee banner (`partner`/`shared`/null) | Body | Card fees are charged to your partner. Change this in Settings › Fees. |
| Payment methods | Error | Turn on at least one payment method. |
| Primary CTA | Button | Activate invoice |
| Secondary | Button | Save as draft |
| Activating | Button (loading) | Activating… |
| Save error (API) | Banner | We couldn't save this invoice. Try again in a moment. |
| Save error | Actions | Retry · Exit without saving |
| VBAN unavailable | Banner (compliance) | Bank transfer isn't available for this currency yet. Choose another payment method or currency to continue. |
| Partner verifying (on activate) | Dialog title | Saved as draft — partner is being verified |
| Partner verifying | Dialog body | We saved this invoice as a draft. We'll let you know when [Partner] is verified so you can activate it. |
| Partner verifying | Dialog buttons | View invoice · Close |
| Success | Toast | Invoice [INV-number] activated for [Partner]. |

---

## Approach-specific copy

### B · Command-bar / conversational (primary)

| Location | Element | Copy |
|----------|---------|------|
| Command bar | Label | New invoice |
| Command bar | Placeholder | Describe the invoice — e.g. "Acme Corp $5,000 for software development, due Aug 7" |
| Command bar | Helper | Type naturally. Add partner, amount, item and due date in any order. |
| Command bar | Primary action | Create |
| Command bar | Alt action | Start from a blank form |
| Parsed result | Section heading | Here's your invoice — check the highlighted fields |
| Parsed field | "confirm" tag | Confirm |
| Parsed field | "auto" tag (compliance) | Auto-filled |
| Parsed field | edit action | Edit |
| Auto compliance helper | Purpose code | Suggested from this partner's past invoices. Confirm it's right. |
| Partner not matched | Inline prompt | We couldn't match a partner named "[text]". Pick one or add a new partner. |
| Low parse confidence **[unvalidated]** | Banner | We couldn't read all the details. Check the fields below, or start from a blank form. |
| Footer status | Note | [N] auto-filled fields to confirm before activating |
| Footer CTA (pre-confirm) | Button | Review & activate |

### A · Smart single form (fallback / new users)

| Location | Element | Copy |
|----------|---------|------|
| Header subtitle | Helper | One page — fill what you need, we'll handle the rest. |
| More details | Disclosure title | More details |
| More details | Disclosure hint | Invoice number, dates, purpose code and terms — already filled in. |
| Defaults | Helper | These come from your settings. Tap to change. |
| Empty (no partners yet) | Title | Add a partner first |
| Empty (no partners yet) | Body | Create your first partner to start invoicing them. |
| Empty | CTA | Add partner |
| Footer status (ready) | Note | Everything required is filled — ready to activate. |

---

## Open copy questions
- **"Activate invoice" vs "Create invoice":** baseline uses both (button = "Activate Invoice", flow name = "Create Invoice"). Recommend: keep **Create invoice** as the modal title/entry verb and **Activate invoice** as the final commit CTA, since activation is the real state change (Draft → active Receivable). Confirm with the team.
- **Command-bar example string:** uses "$" — confirm we want a currency symbol in the placeholder vs. "USD 5,000", given MCY partners. Recommend spelling the currency to avoid implying USD-default.
- **Partner-verifying copy:** confirm legal-approved phrasing for the verification hold; current line avoids committing to a timeline.
- **Purpose code helper:** confirm "RBI" is acceptable in-product copy or whether to say "for cross-border compliance" plainly.
