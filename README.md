# AI-Assisted Design at Xflow — Output Gallery

**Live gallery: [prateek-xflowpay.github.io/AI-Assisted-Design](https://prateek-xflowpay.github.io/AI-Assisted-Design/)**

This repository holds the wireframes and prototypes produced during the initial test runs of Xflow's AI-assisted UX design workflow. Every output here was generated with Claude as a design collaborator — not as automation, but as a structured process where a designer reviews, decides, and advances each step.

The workflow runs in nine steps: Requirements, Research, User Stories, Information Architecture, Lo-Fi Wireframes, Validate Design, UX Copy, Prototype, and Prototype to Canvas. Each step produces a named output file. The three projects here represent the first end-to-end test runs.

---

## Projects

### Invoicing Flow Redesign
A lo-fi exploration of the invoice creation experience across two rounds. Round 1 tested four distinct mental models and converged on the Command Bar as the decisive direction. Round 2 explored earlier structural alternatives. Both rounds include interactive wireframes and clickable prototypes.

### Create Invoice
The most complete step-by-step record: a fabricated PRD based on three real backlog bugs was run through Requirements, Research, User Stories, IA, and Lo-Fi Wireframes. Includes real PostHog funnel data from the 90-day period March–June 2026. Three lo-fi models tested different structural approaches to the wizard.

### Balances
A focused lo-fi exploration of the currency card layout on the /balances page. Three candidate layouts tested approaches to de-verticalising the currency selector.

---

## What's in this repo

Each project follows the same folder structure:

```
[project]/
├── requirements.md
├── research.md
├── user-stories.md
├── ia.md
├── wireframes/
│   └── iterations/round-N/[iteration-name]/wireframe.html
└── prototypes/
    └── variants/[name]/prototype.html
```

Wireframes and prototypes are self-contained HTML files that run directly in the browser.

---

*Part of an ongoing initiative to integrate AI into the Xflow design workflow. Built by the Xflow design team.*
