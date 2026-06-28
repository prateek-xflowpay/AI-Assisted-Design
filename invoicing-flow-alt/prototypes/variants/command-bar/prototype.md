---
render_with_liquid: false
---
# Prototype — Command Bar (Model B)
updated: 2026-06-24 · Prateek
status: built — pending stakeholder review
lineage: `wireframes/iterations/round-2/02-command-bar/` (R2-02), with `round-2/01-smart-single-form/` (R2-01) as the wired fallback
copy: `ux-copy.md` (2026-06-24)
file: `variants/command-bar/prototype.html` (open in a browser)

## Hypothesis
For experienced direct users, the fastest path to an invoice is to *describe* it once and confirm. Turning the form into a confirmation surface (type → parse → confirm auto-filled compliance → activate) cuts the 4-step wizard to a single screen and directly targets the drop-off driver.

## Key trade-off
Speed depends on parse reliability. The prototype shows the graceful-degrade story: low-confidence parses, unmatched partners, and "start from a blank form" all route to the Model A single-page form. Stakeholders should react to whether the *confirmation* model feels trustworthy for money movement.

## Baseline provenance
Added 2026-06-24 after the prototype skill was tightened (snapshot gate + provenance requirement). The host list page was **rebuilt from the real snapshot** — the first version had invented it from tokens.

| Screen | Host snapshot used | capturedAt | Evidence (real structure lifted) | Or: built fresh because… |
|--------|--------------------|-----------|----------------------------------|--------------------------|
| Invoices list (host) | `page-snapshots/invoice-listing.html` | 2026-06-17 | Filter chips (Active 42 · Draft 93 · Overdue 40), "Add Invoice ⇅" split button, columns (Invoice Date · Due Date · Invoice No. · Partner Name · Invoice Amount · Amount Pending · Status), Draft=amber / Active=blue pills, Receive Payments / Developers / Features sidebar + Multi-currency & Test Mode cards | — |
| Create command-bar modal | — | — | — | No snapshot — the create flow is a full-screen modal (a new surface); built fresh on Xflow tokens |

## Fidelity check
**1. UX vs lo-fi (R2-02):** same flow nodes, ingress (`/invoices` → Add Invoice → Create Invoice), and declared states. No UX redesign during build.
**2. Visual vs snapshot (host regions):** sidebar grouping ✓ · top nav (dark navy) ✓ · table columns & order ✓ · filter chips ✓ · status colours (Draft amber / Active blue) ✓ · ingress button ("Add Invoice ⇅" split, not an invented "+ Create") ✓. The modal is the only intentionally-new surface (no snapshot exists).
> Visual uplift only over R2-02 lo-fi — real Xflow tokens (Inter, blue rgb(62,139,254)), real copy from `ux-copy.md`. (*Validate Design was skipped — see below.)

## Harness states
| State | Tag | Source |
|-------|-----|--------|
| Empty command bar | validated | R2-02 flow node B |
| Parsed result (confirm fields) | validated | R2-02 flow nodes E–K |
| Activated success | validated | baseline success state |
| Blank-form fallback (Model A) | validated | R2-01 (selected) |
| VBAN unavailable | validated | baseline corner case |
| Partner verifying | validated | baseline corner case |
| Partner not matched | **new surface** | introduced by command-bar parsing |
| Low parse confidence | **new surface** | introduced by command-bar parsing |
| Save error | **new surface** | baseline API error, re-surfaced here |

> **Caveat:** Step 6 (Validate Design) was skipped at the designer's direction. The three "new surface" states have **not** been through a UX gate — they should be validated before VD handoff. Tagged in the harness so they stay visible.
