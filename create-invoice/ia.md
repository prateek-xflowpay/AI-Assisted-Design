---
---
# Information Architecture — Create Invoice Flow
Date: 2026-06-25
Persona(s): DU — Direct User (Exports)

## Current IA (affected sections)

```
/invoices  (Invoices listing)
  └── Create invoice wizard  [overlay, full-screen, 4 steps]
        ├── Step 0 — Client           (partner selection)
        ├── Step 1 — Products         (line items)
        ├── Step 2 — Invoice Details  (purpose code, dates, terms)
        └── Step 3 — Payment Methods  (bank/card toggles + payment link)
              └── Live preview panel  [right pane, always visible]
```

Entry points into the wizard: Invoices list → "Create Invoice" button · Reconcile flow · Limit Order creation · Home page payment widget.

Note: information-architecture.json and page-registry.json are not present in the context. IA derived from navigation-map.md and flows/invoices/invoice-create.md.

## Ingress points (current → proposed)

No change to ingress points. The wizard continues to be triggered from the same four entry points. The "Create Invoice" button on the Invoices listing page is the primary ingress point for wireframing purposes (designer confirmed: start from the listing page).

## Confirmed IA Extension

Pattern: **B — Extension of existing screen** (all changes are internal to existing wizard steps; no new routes, nav items, or overlays).

```
/invoices  (Invoices listing)
  └── Create invoice wizard  [overlay, full-screen, 4 steps]
        ├── Step 0 — Client
        │     + [US-6] Partner lookup: recent/frequent partners surfaced first
        │     + [US-6] Empty state: inline path to add a partner without abandoning flow
        ├── Step 1 — Products
        │     + [US-7] Item entry: reduced inline editing friction for typical case
        │     + [US-7] Catalogue items surfaced for quick selection
        ├── Step 2 — Invoice Details
        │     + [XFLOW-5799] Purpose Code select: constrained to container width
        │     + [XFLOW-5799] All other selects in the step: same constraint applied
        └── Step 3 — Payment Methods
              + [XFLOW-9620] Fee ownership indicator: inline below card option
              + [XFLOW-9620] Settings link → /usersettings?tab=fees (read-only cross-link)
              + [XFLOW-9601] Live preview panel: bound to real-time toggle state
```

Note: US-8 (flow paradigm) may require IA revision if wireframe exploration proposes a structural change (step consolidation, reordering). This will be assessed after wireframes and updated here if a paradigm shift is confirmed.

## Isolation & forward-compatibility notes

- Persona isolation: clean. The create invoice modal is DU-only. The Settings link (/usersettings?tab=fees) points to an existing page — no structural change to Settings, just a hyperlink. PU and CU are unaffected; formal isolation check at Validate Design.
- Forward-compatibility: no design-forward items in scope; nothing to accommodate.

## Rationale

All three fixes are scoped strictly within existing wizard steps at the component/content layer. No structural change to navigation, routing, or modal architecture is warranted.

## Alternatives considered

None — Pattern B was unambiguous given the purely internal nature of all three fixes.
