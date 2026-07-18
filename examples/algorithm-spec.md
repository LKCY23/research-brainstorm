# Monotone DP Optimization Spec

## Problem Statement

The current dynamic program evaluates all previous states for every event, producing O(n^2) runtime on sequences up to 200k events. The redesign must preserve exact results while exploiting structure in the transition cost.

## Constraints and Non-Goals

- Preserve the existing objective exactly.
- Support 200k events within the target latency budget.
- Do not change upstream event semantics.
- Do not approximate unless explicitly approved.

## Recommended Approach

First formalize the recurrence and prove whether the transition satisfies a known optimization condition. If the argmin is monotone across positions, use divide-and-conquer DP optimization. If the transition is linear in a queryable variable, use a convex hull trick instead.

## Algorithm

```text
for each layer k:
  solve(l, r, opt_l, opt_r):
    mid = floor((l + r) / 2)
    best_j = argmin over j in [opt_l, opt_r] of dp_prev[j] + cost(j, mid)
    dp_cur[mid] = value(best_j, mid)
    solve(l, mid - 1, opt_l, best_j)
    solve(mid + 1, r, best_j, opt_r)
```

## Invariants

- The optimal transition index for `i` is nondecreasing with `i`.
- Each layer only reads from the previous layer.
- Boundary states are defined before the optimized transition runs.

## Rejected Alternatives

- Full O(n^2) scan: exact but too slow.
- Greedy pruning: may be fast, but correctness depends on unproven assumptions.
- Approximation: rejected unless exactness becomes negotiable.

## Verification Criteria

- Compare optimized output against the O(n^2) implementation on small random inputs.
- Add adversarial cases around equal costs and boundary transitions.
- Benchmark at 200k events with representative layer count.

## Open Risks / TODO

- TODO: prove monotone argmin for the actual cost function.
- TODO: decide fallback if monotonicity is false but convexity holds.
