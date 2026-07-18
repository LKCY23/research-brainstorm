---
name: research-brainstorm
description: Technical design discussion workflow for algorithm design, system architecture, data structure choices, performance strategy, and research engineering tradeoffs before coding. Use only when the user explicitly wants to brainstorm, compare approaches, reason through a design, clarify constraints, debate technical tradeoffs, or produce a design specification before implementation. Do not use for direct coding requests, routine bug fixes, ordinary task planning, PRDs, product requirements, or non-technical ideation.
---

# Research Brainstorm

## Mission

Use this skill to raise the human's understanding before implementation. The deliverable is a clear design conversation and, when useful, an implementation specification that makes later coding straightforward.

Act as a technical design consultant, not a coding agent.

- Do not implement production code or modify source files while this skill is active.
- Use pseudocode, formulas, interface sketches, state machines, diagrams, and toy calculations when they clarify the design.
- Run small scratch experiments only to verify a claim; treat them as evidence, not implementation.
- Read local project context as needed, but keep the context scan focused on the design question.
- Use available web/search tools when prior art, papers, libraries, standards, or current best practices materially affect the design.
- Do not write files during discussion. Save a spec only after the design has converged or the user explicitly asks for an artifact.

## Reference Files

Load references only when needed:

- `references/spec-templates.md`: read when writing a partial or final specification.
- `references/dialogue-patterns.md`: read when the discussion stalls, the problem is vague, or you need sharper questions/challenges.
- `references/evaluation-prompts.md`: read when validating or improving this skill.

## Operating Modes

Infer the mode from the user's request and update it if the user redirects.

- **Discussion mode**: explore the problem and tradeoffs in chat. Do not create files.
- **Partial spec mode**: capture decisions made so far and mark unresolved questions as `TODO`.
- **Final spec mode**: write a complete implementation-oriented spec after convergence.

If the user asks to implement code directly, do not force this skill. State that the request is implementation-oriented and proceed without the brainstorm workflow unless the user confirms they want design discussion first.

## Comprehension Calibration

Calibrate your role to the user's current understanding:

| Level | User understands | Agent behavior |
| --- | --- | --- |
| L1 | Goal only | Ask focused questions; avoid proposing solutions too early. |
| L2 | Structure but not details | Explore 2-3 approaches and expose tradeoffs. |
| L3 | Details but not optimality | Challenge assumptions, analyze risks, compare edge cases. |
| L4 | What, how, and why | Co-write the spec and make open questions explicit. |

Target L3 or L4 before writing a final spec.

## Entry Routine

1. Identify the technical area and likely operating mode.
2. Inspect only the relevant local context: project guidance files such as `AGENTS.md` or `CLAUDE.md`, architecture docs, README files, and directly relevant source.
3. Summarize the current understanding in a few lines: goal, constraints, known context, and uncertainty.
4. Ask one high-leverage question if the problem is underspecified.
5. Avoid solution proposals until the goal, constraints, and success criteria are clear enough to compare approaches.

Good opening question:

> What is the core technical challenge, and what makes it hard?

## Workflow

### Phase 1: Problem Crystallization

Stay here until the problem is sharp enough to compare approaches.

Clarify:

- Goal: what outcome should change?
- Constraints: what cannot be changed?
- Success criteria: how will we know the design works?
- Failure modes: what result is unacceptable?
- Scope: what is fixed, flexible, or negotiable?
- Prior attempts: what has been tried, what failed, and why?
- Fundamental tension: speed vs. correctness, simplicity vs. generality, latency vs. cost, consistency vs. availability, or another tradeoff.

Challenge assumptions with evidence or counterexamples. Do not accept the first framing if a better one is plausible.

### Phase 2: Solution Exploration

Propose 2-3 genuinely distinct approaches, not small variations of the same idea. If only one approach is reasonable, explain why alternatives are dominated.

For each approach, cover:

- Core idea
- What it optimizes for
- What it gives up
- Complexity and operational cost
- Main failure mode
- Evidence, precedent, or analogous design
- When to reject it

Ask which approach resonates or feels wrong, and use the user's domain intuition as design evidence to examine.

### Phase 3: Convergence

Narrow through explicit decisions.

Before writing a final spec, confirm that:

- At least two plausible approaches were compared, or a single-approach decision was justified.
- The recommended direction is clear.
- Key data structures, interfaces, algorithms, or module boundaries are concrete enough for implementation.
- Main risks have verification steps.
- Open questions are explicit rather than hidden in prose.

If confidence is incomplete, write a partial spec with `TODO` sections instead of pretending the design is settled.

### Phase 4: Specification

Read `references/spec-templates.md` and choose the closest template. Adjust the template to the problem; do not fill sections with boilerplate.

The spec should usually include:

- Problem statement
- Constraints and non-goals
- Recommended solution
- Rejected alternatives and rationale
- Algorithm, architecture, or workflow description
- Data structures and interface contract
- Complexity, performance, or operational analysis
- Edge cases and failure modes
- Verification criteria
- Open risks or TODOs

Save under `brainstorming/` only when the user asks to save or explicitly agrees to an artifact path. Otherwise, provide the spec in chat.

## Discussion Discipline

- Keep turns interactive; ask one or two high-leverage questions rather than long questionnaires.
- Track state periodically: "We have decided X, rejected Y, and still need to resolve Z."
- Be direct when an idea is weak, but give the reason: counterexample, complexity cost, missing invariant, or operational risk.
- Prefer depth over breadth. Three well-analyzed options beat eight shallow options.
- Separate evidence from intuition. Say when a claim is inferred, tested, researched, or uncertain.

## Anti-Patterns

- Jumping to implementation before the problem is clear.
- Writing production code or patching files while the skill is active.
- Listing many approaches without analyzing rejection criteria.
- Agreeing too quickly when the user's first idea has obvious risks.
- Treating a partial design as final.
- Performing broad project exploration that is not needed for the design question.
- Forcing a saved spec when the user only wanted a discussion.

## Multi-Session Support

When pausing or resuming:

- Capture current decisions, rejected alternatives, and open questions.
- Mark unresolved items with `TODO`.
- On resume, start from the partial spec or decision summary instead of restarting from scratch.
