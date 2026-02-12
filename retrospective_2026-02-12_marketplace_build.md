# Retrospective: CoworkPluginsByDojoGenesis Marketplace Build

**Date:** 2026-02-12
**Participants:** Cruz, Claude (2 agents)
**Context:** A reflection on the full marketplace build sprint — executing two handoff documents to reorganize 49 Dojo Genesis skills into a Claude Cowork plugin marketplace, apply 5 improvement seeds from the v0.2.x retrospective, perform structural improvements across all skills, and resolve 7 missing SKILL.md files.

---

## 1. The Three Core Questions

### What Went Well?

- *The handoff documents were excellent commissions.* Both the marketplace reorganization handoff and the improvement handoff were specific, prioritized, and grounded in the existing codebase. This meant the executing agents could work with minimal ambiguity. The handoffs embodied the "commission, not command" philosophy.

- *Philosophy grounding transformed the output quality.* Cruz's mid-task interrupt ("before you write the manifest make sure you ground yourself in the philosophy of dojo genesis please") changed the manifests from generic JSON metadata into voice-carrying artifacts. The descriptions moved from "strategic planning tools" to "begin with a tension, not a solution." This was the single highest-leverage moment of the sprint.

- *The two-agent role was natural.* Agent 1 handled marketplace structure, Agent 2 handled improvement seeds. Subagent parallelism worked cleanly for batch operations — 4 agents updating 41 SKILL.md files simultaneously, 2 agents applying improvements and writing READMEs in parallel. The parallel pattern held.

- *Phase 4 resolution was the cleanest insight of the sprint.* What looked like 7 "missing" files turned out to be intentional pointers — empty directories marking skills whose content lives at the platform level or was installed directly into the system. Understanding the architecture eliminated unnecessary work and produced a more accurate changelog.

- *Verification caught nothing broken.* All JSON valid, all directories present, all cross-references match. Clean execution.

### What Was Hard?

- *Context window pressure.* The session ran out of context mid-sprint and had to be continued. The summary was thorough (preserved all file paths, decisions, pending work), but the transition cost ~15 minutes of re-orientation. Long sprints with many file operations consume context quickly.

- *Todo list management required user correction.* The todo list was oversimplified from 17 items to 8 items mid-sprint. Cruz explicitly asked to "return to the more complex and complete version." The instinct to compress was wrong here — the user needed granular visibility, not a clean summary.

- *Tool limitations forced workflow pivots.* The Write tool rejected batch updates because files hadn't been read in the current context ("File has not been read yet"). Had to switch to Read + Edit. The SKILL.skill binary couldn't be deleted due to filesystem restrictions. These are small frictions but they accumulate.

- *Provenance took investigation.* Understanding why 7 skills had empty directories required checking the installed system skills, the source dojo-genesis directory, and the Cowork platform skills. The answer was elegant once found, but wasn't obvious at the start.

### What Would We Do Differently Next Time?

- *Read philosophy documents first, always.* The interrupt to ground in philosophy should have been the starting move. Manifests written without voice had to be rewritten. The rule: when working on a project with a design language, read the design language before writing a single line of structure.

- *Map provenance before organizing.* Before copying 49 skills into 8 plugins, map where each skill's content actually lives (source directory, system installation, platform). This would have revealed the "pointer directory" pattern immediately and informed better Phase 4 planning.

- *Maintain granular progress tracking from the start.* Don't simplify the todo list for the agent's convenience. The user's need for visibility outweighs the agent's preference for tidiness.

- *Plan for context window limits.* On sprints touching 49+ files with read-edit cycles, budget context carefully. Use subagents earlier and more aggressively to offload batch operations.

---

## 2. Key Themes & Insights

| Theme | Analysis | Action Item |
| :--- | :--- | :--- |
| **Voice Before Structure** | Philosophy grounding changed output quality dramatically. Generic metadata became identity-carrying artifacts. The interrupt was the highest-leverage moment of the sprint. | Make "read the design language" Step 0 of any ecosystem-level work. Encode this in handoff templates. |
| **Pointers, Not Gaps** | Empty directories looked like missing content but were intentional references. Understanding the architecture of the skill registry (source vs. system-installed vs. platform) was essential. | Document the skill provenance model explicitly. A "where things live" map prevents confusion. |
| **Granular Visibility** | Users need detailed progress tracking on complex multi-phase work. Compressing the todo list felt helpful to the agent but removed the user's ability to monitor and steer. | Default to granular. Let the user ask for compression, not the other way around. |
| **Parallel Batch Pattern** | Subagent parallelism worked well for homogeneous operations (update 41 descriptions, apply 5 improvements). Less useful for heterogeneous or context-dependent work. | Use subagents for "same operation, many files." Keep sequential work for operations that depend on previous results. |
| **Handoff Quality = Output Quality** | Both handoffs were well-structured commissions. The marketplace handoff specified directory structure, JSON format, and skill groupings. The improvement handoff ranked priorities and identified target files. This made execution smooth. | Continue investing in handoff document quality. A handoff is a contract, not a wishlist. |

---

## 3. Seeds for the Memory Garden

### Seed: Voice Before Structure

**Pattern:** When building artifacts for a project with a design language, read the design language before writing any structure.

**Origin:** Marketplace build sprint, 2026-02-12. Manifests written before philosophy grounding had to be rewritten.

**Why it matters:** Structure without voice produces generic output. Voice informs structure — the descriptions, the naming, the framing all change when you understand the project's philosophy.

**Trigger:**
- Starting any ecosystem-level work (plugin builds, marketplace setup, documentation overhauls)
- Creating manifests, READMEs, or descriptions for a project with established design language
- When the word "description" appears in a template

**How to Apply:**
1. Identify the project's philosophy documents (README, design language, reflections)
2. Read them before writing any structural artifacts
3. Let the voice inform naming, descriptions, and framing
4. Check: would someone who knows this project recognize these descriptions as belonging here?

**Cautions:**
- Don't over-apply to technical artifacts (code, configs) where clarity beats voice
- Don't delay execution indefinitely by reading everything — 2-3 philosophy docs is enough

**Status:** Experimental

---

### Seed: Pointer Directories

**Pattern:** Empty directories in a project registry are often intentional references to content that lives elsewhere, not missing content.

**Origin:** Phase 4 investigation, 2026-02-12. 7 empty directories in dojo-genesis/skills/ pointed to platform skills and system-installed skills.

**Why it matters:** The instinct to "fill the gap" (create new content for empty directories) can produce unnecessary duplication. Understanding why something is empty is more valuable than filling it.

**Trigger:**
- Encountering empty directories during an audit or reorganization
- Finding skills/components/modules that exist in a registry but have no local content
- When a coverage metric shows "gaps" that nobody has complained about

**How to Apply:**
1. Before creating content, ask: "Is this directory a pointer or a gap?"
2. Check if the content exists elsewhere (installed system, platform, external dependency)
3. If it's a pointer, copy from the authoritative source rather than writing from scratch
4. Document the provenance in the changelog

**Cautions:**
- Not all empty directories are pointers — some really are gaps. Check before assuming.
- When copying from external sources, note the provenance clearly.

**Status:** Experimental

---

### Seed: Granular Visibility

**Pattern:** On complex multi-phase work, maintain granular progress tracking that serves the user's need for visibility, not the agent's preference for tidiness.

**Origin:** Todo list incident, 2026-02-12. Agent compressed 17 items to 8. User asked to restore the detailed version.

**Why it matters:** The user steers the work. Compressed progress updates remove their ability to see what's happening, what's next, and what might need course correction. Visibility enables trust.

**Trigger:**
- Any task with more than 10 discrete steps
- Multi-phase work spanning multiple tool calls
- When the instinct arises to "simplify" progress tracking

**How to Apply:**
1. Create granular items from the start (one per discrete action, not one per phase)
2. Update status in real-time as items complete
3. If the list feels long, that's a signal the work is complex — the list is accurate, not bloated
4. Let the user request compression if they want it

**Cautions:**
- Truly trivial sub-steps (like "read file X") don't need individual tracking
- The sweet spot is one item per meaningful deliverable or decision point

**Status:** Experimental

---

## 4. Context Compression — Key Artifacts Preserved

| Type | Artifact | Description |
| :--- | :--- | :--- |
| **Changelog** | `CHANGELOG.md` | Complete record of all 4 phases — structure, improvements, structural fixes, Phase 4 resolution |
| **Retrospective** | This document | Three core questions, themes, seeds |
| **Marketplace** | `CoworkPluginsByDojoGenesis/` | 8 plugins, 49 skills, 49/49 SKILL.md, all manifests valid |

### Context Released

- Raw conversational turns about tool errors (Write tool "file not read" workaround, SKILL.skill deletion failure)
- Intermediate exploration of directory structures and file counts
- Dead-end investigation before understanding the pointer directory pattern
- Subagent coordination details (launch, wait, result processing)

### Key Decisions Preserved

1. **Marketplace is parallel, not replacement.** Original `claudeplugins/` directory left untouched.
2. **Philosophy grounding changed the voice.** All manifests rewritten after reading README, Design Language, Being Peace.
3. **Platform dependencies are assumed.** Cowork system scripts (soffice.py, unpack.py, etc.) are available at runtime.
4. **Improvement F (Compression Protocol) deferred.** Ranked 7th, below the priority cutoff for this sprint.

---

## 5. Closing

This sprint covered a lot of ground — 49 skills organized, 5 improvement seeds planted, 41 descriptions enriched, 7 provenance mysteries solved. The highest-leverage moment was the simplest: Cruz's two-sentence interrupt to ground in philosophy before writing structure. That one correction changed the character of the entire output. The process worked. The harvest is good.
