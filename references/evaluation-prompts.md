# Evaluation Prompts

Use these prompts to forward-test whether the skill produces design discussion rather than premature implementation.

## How to Evaluate

For each prompt, check that the response:

- Starts by clarifying goal, constraints, or success criteria when they are missing.
- Avoids production code and source edits.
- Compares distinct approaches when there is a real design choice.
- Challenges weak assumptions with a concrete reason.
- Tracks open questions explicitly.
- Produces a spec only after convergence or when the prompt asks for one.

## Prompt 1: Algorithm Optimization

Use `research-brainstorm` to think through this:

> We have a dynamic programming algorithm over a sequence of 200k events. The current O(n^2) transition is too slow. We need the same result but can probably exploit monotonicity in the transition cost. How should we approach the redesign?

Expected behavior: ask about recurrence shape and monotonicity; compare divide-and-conquer DP, convex hull trick, monotone queue, or problem-specific pruning; avoid writing final code.

## Prompt 2: Architecture Boundary

Use `research-brainstorm` to think through this:

> Our billing module is inside the monolith. Product wants near-real-time invoice status in other services. Should we split billing into a service or publish events from the monolith?

Expected behavior: clarify latency, consistency, ownership, migration risk, and failure modes; compare service extraction, transactional outbox/events, and read-model replication.

## Prompt 3: Performance Strategy

Use `research-brainstorm` to think through this:

> Search results are slow because every request recomputes permissions for thousands of documents. We need sub-200ms p95 without leaking documents. What design should we use?

Expected behavior: prioritize correctness and leakage prevention; compare precomputed ACL indexes, per-user cache, query-time filtering, and hybrid invalidation strategies.

## Prompt 4: Vague Research Idea

Use `research-brainstorm` to think through this:

> I want to make our agent planning more robust. Maybe we need a verifier, or maybe better prompts. Help me figure out the technical direction.

Expected behavior: crystallize the research question; separate evaluation, planner design, verifier design, and prompt changes; propose experiments before implementation.

## Prompt 5: Over-Implementation Pressure

Use `research-brainstorm` to think through this:

> Just write the cache implementation, but I am not sure whether keys should be per-user or per-document.

Expected behavior: identify that the unresolved design choice matters; discuss keying strategies and invalidation before switching to coding.
