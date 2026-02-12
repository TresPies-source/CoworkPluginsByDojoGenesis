# /surface-strategy -- Design a Multi-Surface Product Strategy

**Argument hint:** `<product or feature to distribute across surfaces>`

---

## Philosophy

In a multi-surface world, the biggest mistake is to build the same product on every device. Each surface should be a **complementary** experience, optimized for the unique context in which it will be used. Surfaces are for contexts, not devices. Asymmetry is a feature. The handoff between surfaces is itself a feature.

---

## Workflow

### Step 1: Identify the Surfaces

Ask the user to identify the surfaces they're considering:
- Desktop (native, Electron, Tauri)
- Mobile (native, PWA, React Native)
- Web (SPA, SSR, static)
- API / CLI
- Browser extension
- Other (voice, wearable, embedded)

For each surface, ask: Why this surface? What user context does it serve?

If the user is unsure, help brainstorm by exploring the contexts their users encounter (at a desk, on the go, in a meeting, first encounter).

### Step 2: Define Context and Job-to-be-Done

For each surface, define:

1. **The context:** When, where, and why a user reaches for this surface
2. **The job-to-be-done:** "When I'm [context], I want to [action] so I can [outcome]."

Present as a table:

| Surface | Context | Job-to-be-Done |
|---------|---------|---------------|
| [surface] | [when/where/why] | "When I'm [context], I want to [action] so I can [outcome]" |

Ask the user to validate. Revise if any surface's job overlaps significantly with another's -- overlap means one surface may be unnecessary, or the jobs need sharper differentiation.

### Step 3: Build the Feature-to-Surface Mapping Table

Create a table with features as rows and surfaces as columns. For each cell:
- **Primary:** This is where the feature lives and shines
- **Secondary:** Available but not optimized for this surface
- **--** (Not Available): Deliberately excluded from this surface

```
| Feature | Surface A | Surface B | Surface C |
|---------|-----------|-----------|-----------|
| [feature 1] | Primary | -- | Secondary |
| [feature 2] | Secondary | Primary | -- |
| [feature 3] | -- | -- | Primary |
```

**Validation rules:**
- Every surface must have at least one Primary feature the others don't have
- If a feature is Primary on every surface, it's not differentiated -- rethink
- Not Available is a valid and valuable choice -- asymmetry is a feature

Ask the user to review. Adjust based on their feedback.

### Step 4: Design the Handoffs

For each pair of surfaces that users might transition between, define:

| Handoff | Trigger | State Transferred | UX Moment |
|---------|---------|-------------------|-----------|
| [Surface A -> B] | [what triggers the switch] | [what data/context carries over] | [what the user sees/feels] |

Key design questions:
- What sync architecture supports the handoffs? (cloud, real-time, eventual consistency)
- What happens when surfaces are out of sync?
- Where does the "Continue on [Surface]" moment live in the UI?

**Key principle:** The handoff is the feature. The moment a user switches surfaces and their work is seamlessly there is the moment your multi-surface strategy proves its value.

### Step 5: Define the Business Model

For each surface, define:

| Surface | Pricing | Rationale |
|---------|---------|-----------|
| [surface] | Free / Paid / Freemium / Included | [why this pricing for this surface] |

Consider:
- Should surfaces be bundled or sold separately?
- Does each surface's pricing reflect its unique value?
- Is there a free tier that serves as a discovery funnel?

### Step 6: Plan the Phasing

Define the build order:

| Phase | Surface | Milestone | Rationale |
|-------|---------|-----------|-----------|
| 1 | [core surface] | [what ships] | [why first] |
| 2 | [next surface] | [what ships] | [why second] |
| 3 | [next surface] | [what ships] | [why third] |

**Key principle:** Start with one core surface, prove its value, then expand. Don't build all surfaces simultaneously.

### Step 7: Produce the Strategy Document

Create a markdown document with these sections:

```
# Multi-Surface Strategy: [Product]

**Date:** [date]

## Surfaces & Contexts

[Table of surfaces with context and job-to-be-done]

## Feature Map

[Feature-to-surface mapping table]

## Handoff Design

[Handoff table with triggers, state, and UX moments]

## Business Model

[Pricing table with rationale]

## Phasing

[Phased rollout plan]

## Design Principles

1. Asymmetry is a feature -- each surface has a unique reason to exist
2. The handoff is the feature -- seamless transitions prove the strategy
3. Simplicity on each surface -- ruthlessly focused on core job
```

Save the file as `[date]_surface_strategy_[product].md`.

---

## Quality Gate

Before delivering, verify:

- [ ] All surfaces are identified with their contexts
- [ ] Each surface has a unique job-to-be-done statement
- [ ] A feature-to-surface mapping table is produced
- [ ] Each surface has at least one unique Primary feature
- [ ] Handoff moments are designed for each surface pair
- [ ] A business model is defined for each surface
- [ ] A phased rollout plan exists (not all surfaces at once)
- [ ] User feedback was gathered at each step before proceeding
- [ ] The output is saved as a dated markdown file

---

## Output

A multi-surface strategy document saved as:

```
[date]_surface_strategy_[product].md
```
