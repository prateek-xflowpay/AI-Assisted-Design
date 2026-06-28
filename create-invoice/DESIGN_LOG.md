---
---
# Design Log — Create Invoice Flow

---

## Step 1 — Requirements · 2026-06-25 · Prateek
→ [requirements.md](requirements.md)
Scoped to 3 design-ready bugs (XFLOW-5799, XFLOW-9620, XFLOW-9601) within the create invoice modal; XFLOW-9609 descoped by designer, XFLOW-8811 and XFLOW-9640 parked. Step order follows context docs throughout.

## Step 2 — Research · 2026-06-25 · Prateek
→ [research.md](research.md)
Sources used: PostHog (live funnel) · Mobbin (market patterns). Key insight: Invoice Details (−17.1%) and Payment Methods (−15.5%) drops map directly to the 3 in-scope bugs; market consensus confirms inline sub-text for fee disclosure and synchronous preview update for toggle sync.

## Step 3 — User Stories · 2026-06-25 · Prateek
→ [user-stories.md](user-stories.md)
5 core stories, 2 nice-to-have, 5 out of scope. Scope expanded mid-step to add US-6 (partner selection friction, −52% drop) and US-7 (item entry friction, −41% drop) after designer review of PostHog data; US-5 (template selection) dropped — not a blocker. US-8 (flow paradigm) added as nice-to-have to open wireframe exploration to structural alternatives. requirements.md updated to match.

## Step 4 — Information Architecture · 2026-06-25 · Prateek
→ [ia.md](ia.md)
No structural change — all three fixes are Pattern B (extension of existing screen), contained within Invoice Details (XFLOW-5799) and Payment Methods (XFLOW-9620, XFLOW-9601) steps of the existing wizard.

## Step 5 — Lo-Fi Wireframes · Round 1 · 2026-06-25 · Prateek
→ [wireframes/iterations.md](wireframes/iterations.md)
Three distinct lo-fi models produced: A (Polish Current — 4-step wizard with friction fixes), B (Lighter 3-Step — Client+Products merged, step count 4→3), C (Single-Scroll Canvas — no step gates, one continuous form). All models address US-6, US-7, XFLOW-5799, XFLOW-9620, XFLOW-9601. Models B and C additionally explore US-8 (flow paradigm). Awaiting designer review to select 2–3 for Validate Design.
