# Permission-Aware Search Performance Spec

## Problem Statement

Search requests recompute permissions for thousands of candidate documents. The target is sub-200ms p95 while ensuring no unauthorized document is returned.

## Baseline and Target

- Baseline: query-time permission checks across all candidate documents.
- Target: p95 below 200ms on representative workloads.
- Safety target: zero known permission leaks.

## Recommended Strategy

Build a permission-aware index that precomputes document visibility by stable principal groups, then apply a small query-time filter for rapidly changing exceptions. This preserves correctness while moving most work out of the request path.

## Design Details

- Hot path: search index returns candidates already filtered by principal group.
- Cold path: permission change updates group-document mappings asynchronously.
- Exception path: query-time deny filter handles recent revocations until the index catches up.
- Safety rule: revocations must take effect before grants when ordering is ambiguous.

## Tradeoffs

- Improves p95 latency by reducing per-request permission recomputation.
- Adds index freshness and invalidation complexity.
- Requires explicit monitoring for stale permission windows.

## Rejected Alternatives

- Per-user full result cache: high invalidation cost and poor hit rate for long-tail users.
- Pure query-time filtering: simplest but unlikely to meet p95 target.
- Document-only cache: insufficient because authorization depends on requester identity.

## Verification Criteria

- Benchmark p50/p95/p99 on representative query mix.
- Differential test against the existing permission checker.
- Revocation test: removed access must not leak during index lag.
- Production signal: index freshness, deny-filter hits, and authorization mismatch count.

## Open Risks / TODO

- TODO: define maximum acceptable index staleness.
- TODO: measure principal group cardinality before finalizing index shape.
