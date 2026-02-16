---
name: pre-commission-alignment
description: "Quality gate before commissioning parallel implementation tracks. Discovers and closes gaps between specs/prompts and actual codebase through a pre-implementation checklist and targeted Track 0 remediation. Use when commissioning against a modified codebase, when time has passed between spec writing and implementation, when multi-track commissions share state, or when prompts reference entities or APIs that may not exist. Trigger phrases: 'commission these tracks', 'ready to hand off', 'Track 0', 'align before building', 'pre-commission check'."
---

# Pre-Commission Alignment

## Philosophy

Autonomous implementation agents encounter type errors, missing imports, and API mismatches when specs drift from the actual codebase. Rather than force agents to halt, improvise, or silently diverge, establish clean handoff points through a deliberate quality gate.

**The insight:** Pre-implementation misalignment is cheap to discover (< 1 day) but catastrophically expensive to debug across parallel tracks (3-5 days of cross-track conflicts). Track 0 isn't bureaucratic friction — it's tactical hygiene that protects all downstream work.

**Why this matters for three-agent workflow:** When strategy → implementation → tactical fixes handoffs are clean, autonomous work accelerates. When they're dirty, agents thrash. This skill ensures clean handoff discipline.

---

## When to Use

Activate this skill when:

- **Time gap exists** between spec authoring and implementation commissioning
- **Codebase changed** since specs were written (v0.2.0 → v0.2.1 → v0.2.2 pattern)
- **Multi-track commissions share state** (all tracks touch the same entities, APIs, or configuration)
- **Prompts reference specific types or endpoints** that may have been refactored
- **You're about to commission > 2 parallel implementation tracks**

Do NOT use if the codebase is frozen, specs were written 1 hour ago, or all actors are working from identical, static context.

---

## Workflow

### Phase 1: Dual-Read (30 min)

1. **Read the actual codebase** (not the spec doc):
   - Entity definitions, types, enums
   - API routes, middleware, models
   - Configuration, build output, runtime structure
   - Note what *exists*, not what the spec says should exist

2. **Read the prompts** (the ones you're about to give to agents):
   - Mark every reference to a type, entity, or endpoint
   - Highlight assumptions about naming conventions
   - Note content types, API patterns, data flow expectations

3. **Create a gap inventory** (list, not essay):
   ```
   MISMATCHES:
   - Prompt assumes EntityType.CUSTOM_TYPE but codebase has Type.VARIANT only
   - Prompt references /api/v2/items but only /api/v1/items exists
   - Import paths in prompt: src/types/X but actual: src/lib/X
   - Prompt expects configSchema.js but actual: config.ts
   ```

### Phase 2: Track 0 Remediation (1-3 hours)

Sequential, minimal, targeted changes:

1. **Identify the smallest atomic fix** that removes one mismatch
2. **Make the fix** in the codebase (not in the prompts)
   - Update type names
   - Adjust import paths
   - Add missing endpoints
   - Align naming conventions
3. **Run tests + build** immediately after each fix
   - `npm test && npm run build` (or equivalent)
   - Catch breaks early
4. **Repeat** until all mismatches are closed
5. **Document Track 0 changes** in a commit message:
   ```
   Track 0: Pre-commission alignment
   - Renamed EntityType.CUSTOM to EntityType.VARIANT (prompts expect this)
   - Added /api/v2/items endpoint stub
   - Standardized import paths to src/types/*
   ```

### Phase 3: Verification (15 min)

1. **Re-read the prompts** against the updated codebase
2. **No red flags** when cross-referencing types, endpoints, imports
3. **Tests pass**, build succeeds
4. **All references resolve** (no missing types, undefined imports)

### Phase 4: Commission (immediate)

1. Release the **pre-aligned codebase** to implementation agents
2. Commission **parallel tracks with confidence**
3. Agents encounter zero "wait, this type doesn't exist" friction

---

## Best Practices

**Bias toward codebase over spec:** The codebase is ground truth. If a spec says one thing and the code says another, fix the code, not the spec.

**Keep Track 0 minimal:** Only close gaps that would block implementation. Don't refactor, restructure, or "improve" — that's scope creep. Touch nothing that doesn't have a mismatch.

**Document mismatches before fixing:** Your gap inventory becomes a record of why changes were made. This prevents later confusion.

**Test each fix immediately:** A broken build after Track 0 is catastrophic. Verify after every change.

**Stagger commission:** Don't release all prompts at once. Release Track 0, get confirmation, then release tracks 1-N. This lets early-stage agents validate assumptions before later tracks inherit them.

---

## Quality Checklist

Before commissioning parallel tracks:

- [ ] Gap inventory exists and is non-empty (if empty, you still did the dual-read)
- [ ] Every mismatch has a corresponding Track 0 commit
- [ ] Build passes: `npm test && npm run build` succeeds
- [ ] Type errors resolved: No `TS2304` (not found), `TS7016` (no declaration), etc.
- [ ] Import paths verified: All paths in prompts match actual filesystem structure
- [ ] Naming conventions aligned: Prompts reference entity/type names that exist in codebase
- [ ] API endpoints checked: Prompts reference routes that exist (or have stubs)
- [ ] Configuration matches: If prompts mention config keys, they exist in the actual config
- [ ] Spot-check: Pick 3 random prompt sentences and verify every reference resolves

---

## Common Pitfalls

**Pitfall 1: "Dual-read" becomes "read the spec twice"**
- Fix: Force yourself to browse the actual codebase files, not the spec summary. Grep for type definitions.

**Pitfall 2: Track 0 becomes a rewrite**
- Fix: Set a time box (< 3 hours). If you're still fixing things, you went too deep. Return to the gap inventory.

**Pitfall 3: Commissioning without re-verifying**
- Fix: After Track 0 changes, spend 15 min re-reading prompts against the new codebase. Don't skip this.

**Pitfall 4: Ignoring small mismatches "they'll figure it out"**
- Fix: They won't. A missing import path or wrong type name multiplies across every track. Fix it now.

**Pitfall 5: Not documenting the gap inventory**
- Fix: Write it down (even informally). Future you will ask "why did we change this?" Track 0 commits need a paper trail.

---

## Related Skills

- **codebase-audit-grounding**: Proactive counterpart — audit prevents gaps that Track 0 fixes
- **pre-implementation-checklist**: Document-level verification; this skill is code-level verification
- **parallel-tracks**: This skill ensures parallel tracks start from a clean foundation
- **implementation-prompt**: Receives higher-quality handoffs when pre-commission alignment is done
- **specification-writer**: Specs benefit from codebase grounding but still drift during implementation

---

## Etymology

**Origin:** v0.2.2 commissioning incident. Prompts assumed EntityType names and API patterns that didn't exist after v0.2.0/v0.2.1 implementation. Multiple agents encountered type errors simultaneously. Root cause: 5-day gap between spec writing and implementation start, during which codebase evolved.

**Lesson:** Humans change specs; code changes implementation. Misalignment compounds at handoff points. This skill is the tax we pay for asynchronous, multi-agent work.
