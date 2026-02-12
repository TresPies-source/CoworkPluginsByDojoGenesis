# /strategic-workflow -- Run the Full 8-Phase Strategic-to-Tactical Workflow

**Argument hint:** `<initiative or project to plan>`

---

## Philosophy

Software development is not a linear process. It is a **loop**: from strategic tension to tactical execution and back again. Each cycle produces not just working software, but accumulated wisdom about how to build better, faster, and with more clarity. This command orchestrates the complete loop.

---

## Workflow

This is the master command that coordinates the other commands and skills across 8 phases. Each phase produces a section of a comprehensive strategic brief. Not every phase requires equal time -- move quickly through phases that are already resolved.

### Phase 1: Recognize the Tension

**Goal:** Identify and articulate the strategic tension that needs exploration.

**Actions:**
1. Listen for the tension in the user's request
2. Articulate it as a clear, open-ended question
3. Resist the urge to immediately solve it

The best work begins not with a command ("build X") but with a tension ("should we do X or Y?").

**Output:** A clearly articulated strategic tension.

**Uses:** `strategic-scout` skill (Step 1)

### Phase 2: Scout Multiple Routes

**Goal:** Explore 3-5 distinct strategic routes before committing.

**Actions:**
1. Use the `/scout` workflow to generate 3-5 routes
2. For each route, define: approach, risks, impact, duration
3. Present routes without recommending one

**Output:** A set of viable routes with clear tradeoffs.

**Uses:** `strategic-scout` skill (Step 2), `iterative-scouting` skill if reframing is needed

### Phase 3: Gather Feedback

**Goal:** Present routes and listen for reframes.

**Actions:**
1. Present the scouted routes
2. Listen for the question behind the question
3. If a reframe emerges, return to Phase 2 with the new lens
4. If positioning clarity is needed, use the `/position` workflow

**Output:** Either a decision on a route, or a reframe that triggers re-scouting.

**Uses:** `iterative-scouting` skill, `product-positioning` skill if binary decisions surface

### Phase 4: Make the Strategic Decision

**Goal:** Commit to a strategic direction.

**Actions:**
1. Select the best route (or hybrid)
2. Articulate the decision clearly
3. Document the **why** behind the decision
4. Identify what this decision enables and what it rules out

**Output:** A clear strategic decision with rationale.

### Phase 5: Ground in Reality

**Goal:** Before specifying, understand the current state of constraints and resources.

**Actions:**
1. If **~~project tracker** is connected, search for existing work, epics, and tickets related to this initiative
2. If **~~knowledge base** is connected, search for relevant documentation, prior decisions, or architecture docs
3. If **~~design** is connected, search for relevant design files or prototypes
4. Otherwise, ask the user about:
   - Current constraints (time, budget, team size)
   - Existing work in progress
   - Technical dependencies
   - Stakeholder expectations

**Output:** A grounding summary documenting constraints, dependencies, and current state.

### Phase 6: Specify

**Goal:** Transform the strategic decision into detailed specifications.

**Actions:**
1. Suggest using a specification-driven development workflow if available (cross-plugin reference: `specification-driven-development` plugin)
2. If no spec plugin is available, help the user outline:
   - Architecture (high-level design, component structure)
   - Requirements (detailed, testable success criteria)
   - Non-goals (what is explicitly out of scope)
   - Dependencies and integration points

**Output:** A specification document or outline ready for implementation.

**Note:** This phase is a suggestion, not a hard dependency. If the user has their own specification process, use it.

### Phase 7: Commission Implementation

**Goal:** Move from specification to action.

**Actions:**
1. Suggest using an orchestration or handoff workflow if available (cross-plugin reference: `agent-orchestration` plugin)
2. If no orchestration plugin is available, help the user:
   - Break work into parallel tracks if applicable
   - Define implementation prompts with context, requirements, and success criteria
   - Identify who (or what agent) will execute each track
   - Define the dependency order

**Output:** Implementation commissioned or a clear execution plan.

**Note:** This phase is a suggestion, not a hard dependency.

### Phase 8: Reflect

**Goal:** After execution, extract patterns and improve the process.

**Actions:**
1. Suggest using a retrospective workflow if available (cross-plugin reference: `continuous-learning` plugin)
2. If no learning plugin is available, guide a lightweight reflection:
   - What worked well in this cycle?
   - What would you do differently?
   - Did any new patterns emerge worth capturing?
   - What was the most valuable reframe?

**Output:** Reflection notes and any new patterns identified.

**Note:** This phase is a suggestion, not a hard dependency.

### Produce the Comprehensive Strategic Brief

At the conclusion, compile all phases into a single document:

```
# Strategic Brief: [Initiative]

**Date:** [date]
**Status:** [phase reached]

## 1. The Tension

[Strategic tension from Phase 1]

## 2. Routes Explored

[Route table from Phase 2]

## 3. Feedback & Reframes

[What we heard from Phase 3]

## 4. The Decision

[Strategic decision and rationale from Phase 4]

## 5. Grounding

[Constraints, dependencies, current state from Phase 5]

## 6. Specification

[Spec summary or link from Phase 6]

## 7. Implementation Plan

[Execution plan from Phase 7]

## 8. Reflections

[Learnings from Phase 8]

## Open Questions

[Unresolved items across all phases]
```

Save the file as `[date]_strategic_brief_[initiative].md`.

---

## Quality Gate

Before delivering, verify:

- [ ] Each phase that was executed has a clear output section in the brief
- [ ] The tension was articulated before solutions were explored
- [ ] Routes were explored before committing to a direction
- [ ] User feedback was gathered before synthesizing
- [ ] The decision includes a "why" rationale
- [ ] Cross-plugin references are suggestions, not hard dependencies
- [ ] The output is saved as a dated markdown file

---

## Output

A comprehensive strategic brief saved as:

```
[date]_strategic_brief_[initiative].md
```
