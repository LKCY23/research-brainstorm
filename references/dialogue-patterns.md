# Dialogue Patterns

Use these patterns when the discussion is vague, stuck, or converging too quickly.

## Crystallize the Problem

- "What would be true after this is solved that is not true now?"
- "What is the constraint we are not allowed to violate?"
- "What makes the obvious solution fail?"
- "What would a bad but superficially successful solution look like?"
- "Is the hard part correctness, performance, operability, migration, or developer experience?"

## Challenge Assumptions

- "Why does this need to be solved at this layer?"
- "What if we relaxed that constraint?"
- "What invariant are we relying on, and who enforces it?"
- "Where would this design fail under scale, concurrency, malformed input, or partial outage?"
- "Are we optimizing for the common path or the worst case?"

## Compare Approaches

Use this compact comparison frame:

| Approach | Optimizes for | Gives up | Failure mode | Reject if |
| --- | --- | --- | --- | --- |
| A |  |  |  |  |
| B |  |  |  |  |

## Track State

Use short checkpoints:

- "So far we have decided X and rejected Y because Z."
- "The remaining uncertainty is A; everything else looks implementable."
- "This is still L2: we know the shape, but not the failure behavior."
- "This looks L3: the design is clear enough to compare edge cases."

## Converge

Ask for convergence only after tradeoffs are explicit:

- "Given these tradeoffs, I would recommend A unless B's operational simplicity matters more than latency. Which priority is real here?"
- "The decision seems to hinge on X. If X is true, choose A; otherwise choose B."
- "We can write this as a final spec now, but the unresolved risk is X. Should that be a TODO or should we resolve it first?"

## Handle Direct Coding Pressure

If the user asks for code during the brainstorm:

- "I can implement this after we settle the design. The unresolved design point is X."
- "If you want to switch to implementation now, I will stop using this brainstorm workflow."
- "The code is straightforward once we choose between A and B; the risk is choosing the wrong boundary."
