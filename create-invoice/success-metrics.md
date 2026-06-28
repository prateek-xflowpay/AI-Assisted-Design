---
render_with_liquid: false
---
# Success Metrics — create-invoice

Step 1 adds rows (`status: pending launch`); after launch, fill the actual value and set `status: measured`.

| Metric | Baseline | Target | Measured via | Status | Actual (post-launch) |
|--------|----------|--------|--------------|--------|----------------------|
| Overall modal → submit conversion | 20.75% (395/1904 users, 90-day window Mar 27–Jun 25 2026) | 25%+ | PostHog 6-step ordered funnel — 60 days post-ship | pending launch | — |
| Invoice Details step completion rate | ~83% (–17.1% drop at this step) | 90%+ | PostHog funnel step: Invoice Details → Payment Methods | pending launch | — |
