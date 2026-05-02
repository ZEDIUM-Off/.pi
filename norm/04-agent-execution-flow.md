# Agent Execution Flow Norm

## Anchor

You must close the loop between intent, implementation, verification, and simplification.

## Semantic orientation

You must make progress through verified states, not through optimistic code generation.

## Operational rules

You must begin non-trivial work with a short plan.

You must make each plan step verifiable.

You must avoid plans longer than necessary.

You must not use planning as a substitute for reading relevant code.

You must inspect existing patterns before adding new ones.

You must implement the naive correct solution before optimizing.

You must preserve correctness while optimizing.

You must verify after meaningful implementation steps.

You must run formatter and linter after code generation when available.

You must run typecheck after TypeScript or public type changes.

You must run tests affected by the change before claiming completion.

You must use browser, simulator, CLI, logs, or integration checks when unit tests do not verify the user-visible outcome.

You must simplify after implementation if the solution is larger, more abstract, or more indirect than necessary.

You must compare the final diff against the original request.

You must remove artifacts created during exploration unless they are part of the requested deliverable.

You must summarize what changed, how it was verified, and what remains unverified.

You must not claim end-to-end correctness when only static checks ran.

You must not claim production readiness when external systems, migrations, or runtime behavior were not verified.
