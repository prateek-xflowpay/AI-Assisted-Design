# Design Log — Invoicing Flow

---

## Step 5 — Lo-Fi Wireframes (Round 2, re-design) · 2026-06-24 · Prateek

→ [wireframes/](wireframes/) · [iterations.md](wireframes/iterations.md)

Fresh restart at Prateek's direction. Scope locked to one driver: **too many steps / drop-off**. R1 set aside (not deleted) — R1-01/02 superseded, R1-03/04 parked with triggers.

Round 2 — 4 genuinely distinct mental models, all compressing the 4-step wizard:
- 01 · **Smart single-screen form** — 4 steps → 1 page; essentials shown, compliance defaulted + collapsed
- 02 · **Command-bar / conversational** — type the invoice in one line; form becomes a confirmation surface
- 03 · **Duplicate-first / template gallery** — start from a past invoice; edit only the deltas
- 04 · **Direct-on-document** — the invoice itself is the editable surface; footer checklist tracks completeness

**Parked:** R1-03 quick-drawer (batch/multitask trigger), R1-04 accordion (guided-structure trigger).
**Superseded:** R1-01, R1-02.
**Provenance:** No ia.md / user-stories.md — graceful degrade to `direct_user` flow docs + screenshots + page-snapshots (June 2026). Ingress unchanged across all models.

**Converged (2026-06-24):** Prateek picked **Model B (command-bar)** as the lead. Carried with **Model A** as its coupled fallback (B degrades to a blank form; A is the safe base for new users / low-confidence parses). C and D parked with revival triggers. See [selected.md](wireframes/selected.md).

**Next:** Validate Design (Step 6) on B + A, lo-fi as built.

---

## Prototype skill hardened + list page fixed · 2026-06-24 · Prateek

Caught that the command-bar prototype had an **invented** invoice-listing host page (wrong ingress, missing filter chips, wrong columns/status colours, restructured sidebar) — the `invoice-listing.html` snapshot was never used. Root cause: the snapshot step was prose, not enforced. Tightened `skills/prototype/SKILL.md` (blocking snapshot gate, required baseline-provenance table, "never copy a sibling prototype's shell" anti-pattern, host = [snapshot verbatim] + [new section] reframe, second visual-vs-snapshot fidelity check) and, as the first test, **rebuilt the list page from the real snapshot** (chips, "Add Invoice ⇅" split button, real columns, Draft=amber/Active=blue, real sidebar). Provenance table added to `prototypes/variants/command-bar/prototype.md`. Logged in wiki [[prototype-baseline-2026-06]].

---

## Step 8 — Prototype · 2026-06-24 · Prateek

→ [prototypes/prototypes.md](prototypes/prototypes.md)

Built 1 prototype: **Command Bar (Model B)** — clickable, Xflow-token fidelity, real copy from `ux-copy.md`. Happy path (type → parse → confirm → activate) plus a tagged state harness (9 states; 3 "new surface": partner-not-matched, low parse confidence, save error). Wired fallback to Model A blank form. R1 accordion prototype marked superseded. Pending stakeholder review. **Caveat:** built without a Validate Design pass — new surfaces flagged for validation before VD handoff.

---

## Step 7 — UX Copy · 2026-06-24 · Prateek

→ [ux-copy.md](ux-copy.md)

Wrote real on-brand copy for ~30 screens/states across B (command-bar) + A (fallback): labels, CTAs, empty/error/success states, and money/compliance microcopy, using glossary domain terms (Partner, Receivable, Purpose Code, Payment Link, VBAN). Notable decision: keep "Create invoice" as the entry verb and "Activate invoice" as the final commit CTA (activation is the real Draft → Receivable state change). 4 open copy questions logged for the team.

---

## Step 6 — Validate Design · SKIPPED · 2026-06-24 · Prateek

Skipped Step 6 — Prateek's call, to move straight to UX Copy → Prototype. Reason/gap accepted: this is a re-design exploration round and the team wants a clickable artifact fast. Required VD inputs (`user-stories.md`, `ia.md`) were absent anyway (graceful-degrade project), so a gate against missing inputs would have added little. **Known gap:** the B-specific risks normally caught by VD remain unvalidated — parse-failure handoff to A, line-item round-trip after a parse, compliance "confirm" affordance. These are carried forward as flagged "new surfaces" in the prototype's state harness so they stay visible.

---

## Step 5 — Lo-Fi Wireframes (Round 1) · 2026-06-24 · Prateek

→ [wireframes/](wireframes/)

1 round; 4 iterations produced, pending review.

**Iterations:**
- 01 · Single-page form — all steps on one scrollable page
- 02 · Document-direct — invoice preview is the clickable interface
- 03 · Quick-create drawer — right-drawer preserves list context
- 04 · Accordion card stack — all steps visible as locked cards, inline Continue

**Parked:** none yet  
**Rejected:** none yet  

**Provenance:** No ia.md / user-stories.md — gracefully degraded to `direct_user` flow docs + screenshots (June 2026).

**Next:** Mix-and-match refinement with Prateek → converge to 2–3 survivors → Validate Design.

---

## Step 8 — Prototype · 2026-06-24 · Prateek

→ [prototypes/prototypes.md](prototypes/prototypes.md)

Built 1 prototype: **Accordion Card Stack** (Model D). Selected by Prateek from Round 1 wireframes.

Pending stakeholder review. 2 new surfaces flagged for Validate before VD handoff (API error banner, VBAN unavailable banner).
