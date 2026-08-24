# Dependency Policy

Adding dependencies requires human approval unless the task explicitly authorizes it.

## Current Dependency Profile

- Runtime: `[RUNTIME_DEPS]`
- Development: `[DEV_DEPS]`
- Package manager: `[PACKAGE_MANAGER]`

## Before Proposing A Dependency

Document:

- package name
- reason it is needed
- alternatives considered
- maintenance risk
- license concern, if any
- expected bundle/runtime impact

## Forbidden

Do not add dependencies for trivial helpers, formatting convenience, or avoidable wrappers.
