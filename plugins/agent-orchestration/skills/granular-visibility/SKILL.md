---
name: granular-visibility
description: "Maintain granular progress tracking that serves the user's need for steering, not the agent's preference for tidiness. Default to detail; let the user request compression. Use on any task with 10+ discrete steps, multi-phase work, or when the instinct arises to simplify progress tracking. Trigger phrases: 'long todo list', 'simplify the progress', 'clean this up', 'what is the status', 'too many items'."
---

# Granular Visibility

## Philosophy

On complex work, the user steers. Visibility is the steering wheel. Compressed progress updates remove the user's ability to see what's happening, what's next, and what might need course correction. The instinct to simplify feels helpful to the agent but serves the agent's preference for tidiness, not the user's need for control.

The chain runs in one direction: granular visibility → user sees progress → user can steer → user trusts the process → user delegates more → agent moves faster → better outcomes.

The anti-pattern runs the other way: compressed visibility → user can't see progress → user interrupts to check status → agent stops to explain → both lose momentum → trust erodes.

## When to Use

- Any task with more than 10 discrete steps
- Multi-phase work spanning multiple tool calls or coordinated actions
- When the instinct arises to "simplify" or "clean up" progress tracking
- When working with a user who values steering and visibility over convenience
- When a todo list length triggers concern that it's "too long" — that's usually a signal the work is complex, not that the list is bloated

## Workflow

### Creating Granular Items

1. **Map discrete deliverables**: One todo item per concrete output or decision point, not one per phase
2. **Be specific**: "Read config file" is not granular; "Read config file, identify auth settings, determine if migration needed" is
3. **Avoid nesting**: Don't hide sub-steps under parent tasks; make them visible
4. **Start with the full list**: Granularity from the beginning creates accurate expectations

### Maintaining Visibility

1. **Update status in real-time**: Mark items `in_progress`, `completed`, or `pending` as they change
2. **Add blockers immediately**: If an item is blocked, note it — don't wait for the user to notice
3. **Communicate what changes**: If scope shifts, show how the list evolves
4. **Never pre-compress**: Let the user ask for a simpler view; don't offer it unprompted

### Responding to "Too Long"

If the user says the todo list feels long:

- Confirm that length reflects complexity, not bloat
- Offer to reorganize (by phase, by urgency) without removing items
- Ask if they want a compressed summary *in addition to* the granular list
- Never delete items to make the list shorter

## Best Practices

### What to Track Granularly

- Discrete deliverables (read file, analyze results, generate output)
- Decision points (determine eligibility, choose approach, validate direction)
- Quality gates (test results, review findings, check integrity)
- Coordination steps (wait for user input, get approval, resolve blocking issue)

### What to Consolidate

- Trivial sub-steps (opening a file is part of "read file," not a separate item)
- Steps that must happen together (if A always requires B immediately, they're one item)
- Repeated boilerplate (don't create 20 "read file X" items; group similar reads)

### Tone and Clarity

- Use imperative form: "Read config file" not "Reading the config file"
- Be specific about scope: "Parse JSON and extract auth settings" not "Process data"
- Make status clear: distinguish between "pending" (waiting for decision), "in_progress" (actively working), and "blocked" (waiting for external factor)

## Quality Checklist

- [ ] Each todo item represents one discrete deliverable or decision point
- [ ] Status is updated in real-time as work progresses
- [ ] The list length matches the actual complexity of the work
- [ ] Truly trivial sub-steps (e.g., "read file X") are not individually tracked
- [ ] User has not been asked to accept or approve a compressed view
- [ ] Blocking issues are flagged immediately with reason and impact
- [ ] If scope changes, the list evolves to reflect it
- [ ] Items are specific enough that their status is unambiguous

## Common Pitfalls

### Pre-Compression

**Pitfall**: "The list is getting long, I should simplify it before showing the user."
**Reality**: Length reflects work complexity. Compression removes steering ability.
**Fix**: Show the full list. If the user wants fewer items, they'll ask.

### Hiding Sub-Steps

**Pitfall**: Creating high-level items like "Phase 1: Analysis" to keep the list short.
**Reality**: The user can't see what needs to happen in Phase 1 until you show up with new items mid-stream.
**Fix**: Break Phase 1 into discrete items from the start. It's okay if that creates 8 items instead of 1.

### Assuming Simplicity Preference

**Pitfall**: Assuming all users prefer simplified views and offering compression unprompted.
**Reality**: Many users explicitly choose granular tracking and will ask if they want less detail.
**Fix**: Default to granular. Compression is opt-in, not default.

### Updating Retrospectively

**Pitfall**: Waiting until the phase is done to update the todo list.
**Reality**: The user sees stale status and loses confidence in the progress tracking.
**Fix**: Update as items change. Mark things `in_progress` before you start them, `completed` immediately after.

## Related Skills

- **handoff-protocol**: Clean handoffs require visible progress context; granular tracking provides it
- **workspace-navigation**: Navigating shared work benefits from detailed status visibility
- **decision-propagation**: Decisions surface faster when progress is visible and granular
- **agent-teaching**: Teaching another agent requires understanding where work stands — visibility enables this
