# /scout -- Navigate a Strategic Tension

**Argument hint:** `<tension, decision, or strategic question>`

---

## Philosophy

Strategic thinking begins with tension, not solution. The quality of your routes is determined by the quality of your questions. A scout doesn't recommend -- it reveals the landscape so the user can choose with clarity.

---

## Workflow

### Step 1: Surface the Tension

Ask the user to describe the tension. Accept any form:

- A binary decision: "Should we X or Y?"
- A strategic question: "How should we approach Z?"
- A feeling of being stuck: "Something isn't right about our Q direction."

Help articulate the tension as a clean statement: **"The tension is between [A] and [B]."**

If the user provides a clear tension in their argument, acknowledge it and move to Step 2. Do not over-interrogate when the tension is obvious.

### Step 2: Gather Context

If **~~knowledge base** is connected, search for prior strategic documents, decision records, or retrospectives related to this tension.

Ask the user for any additional context:
- What has been tried before?
- What constraints exist (time, budget, team size)?
- Who are the stakeholders?

Conclude context gathering when you have enough to scout meaningfully. Don't delay scouting for perfect information.

### Step 3: Scout 3-5 Routes

Generate 3-5 **distinct** routes. Each route is a complete strategic direction, not a minor variation. For each route, define:

| Field | Description |
|-------|-------------|
| **Name** | A memorable, descriptive title |
| **Thesis** | One sentence explaining the core idea |
| **Risk** | What could go wrong |
| **Impact** | What this enables if successful |
| **Duration** | Rough timeline estimate |
| **Optimizes for** | What this route prioritizes |
| **Sacrifices** | What this route gives up |

Present routes as a table. **Do NOT recommend one.** Ask the user:

> "Which of these routes resonate? Which feel wrong? Did any spark a new idea?"

### Step 4: Listen and Synthesize

After user feedback:

1. Note which routes resonated and why
2. Note which routes felt wrong and why
3. Look for connections between what resonated
4. Listen for reframes -- did the user's reaction reveal a deeper question?

If a reframe emerges, name it explicitly and consider re-scouting with the new lens (see the `iterative-scouting` skill).

If no reframe emerges, synthesize a hybrid direction that incorporates what resonated. Give the synthesized direction a memorable name.

### Step 5: Produce the Strategic Decision Document

Create a markdown document with these sections:

```
# Strategic Scout: [Topic]

**Date:** [date]
**Tension:** [tension statement]

## Routes Explored

[Table of all routes with Name, Thesis, Risk, Impact, Optimizes For, Sacrifices]

## What We Heard

[Summary of user feedback -- what resonated, what didn't, any reframes]

## Synthesized Direction: [Name]

[Description of the hybrid/refined direction with rationale]

## Next Steps

[3-5 concrete next steps to move from strategy to action]

## Open Questions

[Any unresolved questions that need further exploration]
```

Save the file as `[date]_strategic_scout_[topic].md`.

---

## Quality Gate

Before delivering, verify:

- [ ] The tension is clearly articulated as a statement, not a solution
- [ ] At least 3 distinct routes are presented (never fewer)
- [ ] Each route has a name, thesis, tradeoffs, and what it optimizes/sacrifices
- [ ] Routes are presented without recommendation -- the user chose what resonated
- [ ] User feedback was gathered before synthesizing
- [ ] The synthesized direction has a name and clear rationale
- [ ] The output is saved as a dated markdown file
- [ ] Next steps are concrete and actionable

---

## Output

A strategic decision document saved as:

```
[date]_strategic_scout_[topic].md
```
