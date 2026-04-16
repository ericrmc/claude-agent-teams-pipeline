# Post-Session Feedback

Reflect on the session that just completed. Surface execution friction, protocol gaps, and structural improvements that only become visible by running the process — not by analyzing it theoretically.

**Session:** $ARGUMENTS

---

## Why This Exists

Brainstorm agents reason about the system from outside. Stress-tests analyze the mechanism structurally. Neither has the perspective of "I just executed this protocol and here's what was actually hard." This command captures that operational perspective while it's fresh.

The agents inside a process can challenge each other's *ideas* but cannot challenge the *process itself* — they operate inside the frame the prompt sets. This command operates outside that frame, from the executor's perspective rather than the designer's.

---

## When to Run

After completing a `/brainstorm`, `/review-fix`, or `/pipeline` session. Run it in the same conversation where the session happened — the execution context is in your conversation history. If run in a fresh conversation, provide the session type and any working files (brainstorm output, transcripts, checkpoints) as arguments.

---

## Reflection Protocol

Work through each section. Be specific and honest — the value is in concrete observations, not general impressions. Reference specific moments in the session where possible.

### 1. Execution Friction

Where did the protocol make your job harder?

- **Instructions you had to re-read or search for** — sections where the information you needed wasn't where you expected it when you needed it.
- **Steps where you had to improvise** — places the protocol didn't cover what actually happened (agent non-response, unexpected output format, timing issues).
- **Context pressure** — moments where you felt the protocol instructions were competing with working state for attention. Which sections could you have done without at that point in execution?
- **Coordination overhead** — agent management steps that cost time without adding value (redundant messages, unnecessary waiting, agents that didn't contribute).

### 2. Protocol vs. Reality

Where did the protocol's model of execution diverge from what actually happened?

- **Assumed sequences that didn't hold** — steps that happened out of order, or agent behaviors the protocol didn't anticipate.
- **Instructions that were ignored or impossible** — things the protocol told you to do that you skipped (and nothing broke) or couldn't do (and had to work around).
- **Missing instructions** — situations you encountered that the protocol gave no guidance for.

### 3. What Worked Well

What aspects of the protocol made execution easier? These are as important as the friction points — they should be preserved and possibly applied to other sections.

- **Instructions that were immediately actionable** — steps you could execute without re-reading or interpreting.
- **Structural patterns that helped** — formatting, ordering, or grouping that matched how you needed to use the information.
- **Mechanisms that produced good results** — voting, challenge, convergence, or coordination patterns that reliably produced the intended outcome.

### 4. Proposed Changes

For each friction point or divergence, propose a concrete change. Focus on changes to the command files themselves — the execution environment, not the ideas the process produces.

For each proposal:
```
**Problem:** {what went wrong or was hard, with specific reference to the session}
**Cause:** {which part of the protocol caused it — file, section, specific instruction}
**Fix:** {concrete change — rewrite the section, move it, remove it, add something}
**Confidence:** high | medium | low {how sure are you this fix helps without causing new problems}
```

### 5. Structural Observations

Step back from individual fixes. Are there patterns across your friction points that suggest a larger structural change?

- Do the friction points cluster in one phase or one file?
- Is there a recurring cause (too much reference material in the execution path, missing error handling, unclear scoping)?
- Would a different organization of the protocol files address multiple friction points at once?

---

## Output

Write findings to `feedback-{session-type}-{YYYYMMDD}.md` in the working directory (or `--output PATH` if specified).

```markdown
# Session Feedback: {session type and brief description}

**Date:** {date}
**Session:** {brainstorm / review-fix / pipeline}
**Duration:** {approximate, if known}
**Files involved:** {command files that were executed}

## Execution Friction
{findings from section 1}

## Protocol vs. Reality
{findings from section 2}

## What Worked
{findings from section 3}

## Proposed Changes
{each proposal in the format above}

## Structural Observations
{findings from section 5}
```

### Present to user

Show:
- Count of friction points and proposed changes
- The top 2-3 proposed changes with one-line descriptions
- The structural observation (if any)
- The output file path for full details
