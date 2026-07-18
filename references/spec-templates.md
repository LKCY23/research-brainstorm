# Spec Templates

Use the smallest template that captures the real design complexity. Remove sections that do not apply and expand sections where the hard reasoning lives.

## Common Rules

- Write implementation specifications, not product requirements.
- Include rejected alternatives and why they lost.
- Use pseudocode only for algorithms or workflows that need precision.
- State invariants, preconditions, postconditions, and failure behavior when they matter.
- Mark unresolved decisions as `TODO` rather than burying uncertainty.

## Algorithm Design Spec

```markdown
# [Name] Algorithm Design Spec

## Problem Statement
[Input, desired output, constraints, why the straightforward approach is insufficient.]

## Constraints and Non-Goals
- [Constraint]
- [Non-goal]

## Recommended Approach
[Core idea in 2-3 sentences.]

## Algorithm
[Pseudocode or mathematical recurrence.]

## Invariants
- [Invariant that must hold.]

## Data Structures
- `[name]`: [shape, operations, why chosen.]

## Complexity Analysis
- Time:
- Space:
- Bottleneck:

## Rejected Alternatives
- [Alternative]: rejected because [reason].

## Edge Cases
- [Case]: [expected behavior].

## Verification Criteria
- [Property test, example, benchmark, or proof obligation.]

## Open Risks / TODO
- [Unresolved question.]
```

## Architecture Spec

```markdown
# [Name] Architecture Spec

## Problem Statement
[Current architecture, desired capability, and why the change is hard.]

## Context
- Existing modules:
- External systems:
- Operational constraints:

## Recommended Design
[Core architecture and module boundaries.]

## Interface Contract
- Inputs:
- Outputs:
- Errors:
- Idempotency / consistency:

## Data Flow
[Sequence, state machine, or diagram-friendly workflow.]

## Migration Plan
1. [Step]
2. [Step]

## Rejected Alternatives
- [Alternative]: rejected because [reason].

## Failure Modes
- [Failure]: [mitigation or detection.]

## Verification Criteria
- [Unit, integration, load, rollback, or observability check.]

## Open Risks / TODO
- [Unresolved question.]
```

## Performance Strategy Spec

```markdown
# [Name] Performance Strategy Spec

## Problem Statement
[Observed bottleneck, workload, target, and current limitation.]

## Baseline and Target
- Baseline:
- Target:
- Measurement method:

## Recommended Strategy
[Caching, indexing, batching, parallelism, algorithmic change, or another strategy.]

## Design Details
- Hot path:
- Cold path:
- Invalidations / consistency:
- Backpressure / limits:

## Tradeoffs
- Improves:
- Costs:
- Risks:

## Rejected Alternatives
- [Alternative]: rejected because [reason].

## Verification Criteria
- Benchmark:
- Regression guard:
- Production signal:

## Open Risks / TODO
- [Unresolved question.]
```

## Research / Experiment Spec

```markdown
# [Name] Research Engineering Spec

## Research Question
[Hypothesis or technical uncertainty.]

## Experimental Design
- Independent variable:
- Dependent metric:
- Baseline:
- Dataset / workload:
- Controls:

## Implementation Sketch
[High-level workflow, not production code.]

## Success Criteria
- [Metric threshold or qualitative acceptance rule.]

## Failure Interpretation
- If [result], then [interpretation].

## Rejected Experimental Designs
- [Alternative]: rejected because [reason.]

## Risks / TODO
- [Unresolved question.]
```
