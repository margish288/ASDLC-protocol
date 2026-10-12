# Dependency Policy

Adding dependencies requires human approval unless the task explicitly authorizes it.

## Current Dependency Profile

Read actual runtime/development dependencies and package manager details from the target manifests and installed `project/context.md`. Do not add a dependency merely because an example protocol check mentions a tool.

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
