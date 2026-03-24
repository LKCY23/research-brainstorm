# research-brainstorm

> A Claude Code skill for technical design discussion before implementation.

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

The skill shifts Claude into a research-oriented collaboration mode that emphasizes:

- problem crystallization before solutioning
- multiple distinct approaches instead of one immediate answer
- evidence-based tradeoff analysis
- structured convergence toward a spec
- pseudocode/spec output rather than production code

The intended output is usually an implementation-oriented specification that makes later coding and review much easier.

## Repository contents

| Path | Role |
| --- | --- |
| `SKILL.md` | canonical maintained skill definition |
| `README.md` | repository overview and usage context |
| `examples/example-spec.md` | minimal sample of the kind of implementation-oriented spec this skill should produce |

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

Once installed or made available to Claude Code, invoke it through:

- `/research-brainstorm`

A typical interaction should lead toward a structured design discussion and then a written specification, not immediate source-code generation.

## Minimal validation

A lightweight manual validation path for this repository is:

1. confirm `SKILL.md` still clearly describes brainstorming-before-coding behavior
2. invoke `/research-brainstorm` in Claude Code on a design question
3. verify the interaction stays discussion-oriented instead of jumping straight into implementation
4. verify the result trends toward a spec or implementation plan artifact
5. compare the result against `examples/example-spec.md` to sanity-check the expected output shape

## Example artifact

A minimal sample output is included at:

- `examples/example-spec.md`

It is not meant to be the only valid output format, but it anchors the style and level of detail this repository is aiming for.

## Next improvements

- add one example spec output under a future `brainstorming/` or `examples/` directory
- add a more explicit install/setup note if distribution expands
- refine the README once the repo has more than the core skill definition
