# research-brainstorm

> A skill for technical design discussion before implementation.

---

## Overview

`research-brainstorm` is a standalone skill for working through technical problems in discussion mode before writing code.

It is designed for cases where the real task is not "implement immediately", but rather:

- clarify the problem
- compare approaches
- surface tradeoffs
- challenge assumptions
- converge on a clear design
- produce an implementation specification

## What the skill does

The skill shifts the agent into a research-oriented collaboration mode that emphasizes:

- problem crystallization before solutioning
- multiple distinct approaches instead of one immediate answer
- evidence-based tradeoff analysis
- structured convergence toward a spec
- pseudocode/spec output rather than production code

The intended output is either a clarified technical direction in chat, a partial specification with explicit TODOs, or a final implementation-oriented specification that makes later coding and review much easier.

## Repository contents

| Path | Role |
| --- | --- |
| `SKILL.md` | canonical maintained skill definition and source of truth for the skill |
| `references/spec-templates.md` | optional templates for algorithm, architecture, performance, and research specs |
| `references/dialogue-patterns.md` | optional prompts for crystallizing vague problems, challenging assumptions, and converging |
| `references/evaluation-prompts.md` | forward-test prompts and acceptance criteria for validating the skill |
| `README.md` | repository overview, usage context, and maintenance workflow |
| `examples/*.md` | realistic sample specs for the kind of artifacts this skill should produce |
| `.gitignore` | local-hygiene rules for keeping machine-specific files out of the repo |

## Current usage model

This repository is the canonical source for `research-brainstorm`.

The maintained skill definition lives at:

- `SKILL.md`

`claudespace` consumes this repository through the submodule path:

- `skills/research-brainstorm`

## Current role in claudespace

This repository is maintained as a standalone skill repository and is also linked into the larger `claudespace` workspace as a git submodule.

That means the expected workflow is:

1. edit and maintain the skill here
2. commit changes here first
3. update the submodule reference from `claudespace` after changes are ready

## When to use this skill

Use `research-brainstorm` when the goal is to think through a technical problem before implementation, for example:

- algorithm design
- architectural tradeoffs
- performance strategy
- data structure choice
- complex system design
- any situation where understanding should come before coding

## Usage

Once installed or made available to an agent runtime, invoke it through:

- `/research-brainstorm`

A typical interaction should lead toward structured design discussion first. A written specification is produced only after convergence or when the user explicitly asks for one, not as an automatic first response.

## Minimal validation

A lightweight manual validation path for this repository is:

1. confirm `SKILL.md` still clearly describes brainstorming-before-coding behavior
2. confirm the frontmatter description has both positive and negative trigger conditions
3. invoke `/research-brainstorm` on one prompt from `references/evaluation-prompts.md`
4. verify the interaction stays discussion-oriented instead of jumping straight into implementation
5. verify the response clarifies constraints, compares real alternatives, and challenges weak assumptions
6. verify a spec is produced only after convergence or when explicitly requested
7. compare the result against `examples/*.md` to sanity-check the expected output shape

## Example artifact

Sample outputs are included in:

- `examples/algorithm-spec.md`
- `examples/architecture-spec.md`
- `examples/performance-spec.md`

They are not meant to be the only valid output formats, but they anchor the style and level of detail this repository is aiming for.

## Maintenance notes

- Keep `SKILL.md` concise and platform-neutral.
- Put reusable templates and examples in `references/` or `examples/` rather than expanding `SKILL.md`.
- Avoid adding scripts unless a repeated deterministic operation appears.
- After changing behavior, forward-test with `references/evaluation-prompts.md`.
- Commit changes in this repository first, then update the parent `claudespace` submodule reference if needed.
