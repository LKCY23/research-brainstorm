# Example System Design Review — Implementation Specification

## Problem Statement

The team needs a structured way to discuss a technical change before implementation. The challenge is that jumping directly into code produces shallow decisions, unclear tradeoffs, and slow review cycles.

## Solution Overview

Use a discussion-first workflow that forces the problem to be clarified, explores multiple candidate approaches, and ends in a written implementation specification.

## Algorithm / Design Description

1. Clarify the problem and constraints.
2. Identify 2-3 distinct approaches.
3. Compare tradeoffs and likely failure modes.
4. Converge on one recommended direction.
5. Write the result as a spec rather than production code.

## Data Structures

- Problem statement
- Candidate approaches
- Tradeoff matrix
- Final recommendation
- Open risks

## Interface Contract

**Input:** a technical problem, design question, or architecture choice.

**Output:** a structured implementation-oriented specification.

## Design Decisions & Rationale

- Prefer structured dialogue over immediate code generation.
- Require multiple approaches so the first idea is not accepted by default.
- End with a spec so implementation can become mechanical later.

## Complexity Analysis

The discussion cost is front-loaded, but reduces downstream implementation churn and review ambiguity.

## Edge Cases and Boundary Conditions

- User already knows the answer and only needs code.
- Problem is too underspecified to compare approaches meaningfully.
- Multiple valid approaches remain after discussion.

## Verification Criteria

A successful brainstorm:
- surfaces at least one tradeoff
- compares more than one direction
- avoids jumping into code too early
- produces a usable written spec

## Open Risks

- The discussion may stay too abstract without concrete constraints.
- The agent may drift into implementation mode if the problem is too narrow.
