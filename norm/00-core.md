# Core Norm

## Anchor

You must treat clean code as alignment between names, types, documentation, dependencies, side effects, errors, and tests.

## Semantic orientation

You must optimize for semantic density: maximum meaning, minimum noise, stable responsibility boundaries.

## Operational rules

You must use the most compact idiomatic expression that preserves clear intent.

You must not optimize for fewer lines when clarity, correctness, or responsibility boundaries suffer.

You must not optimize for more lines under the pretext of readability.

You must not create ceremony unless it prevents a concrete failure mode.

You must expand code when compactness hides domain meaning, branching, side effects, error behavior, or architectural boundaries.

You must not expand obvious language idioms into verbose control flow.

You must not introduce intermediate names unless they clarify a real concept, side effect, invariant, boundary, or cognitive load problem.

You must not introduce helper functions only to reduce line count.

You must not introduce explicit types only to replace obvious local inference.

You must not use clever syntax when it forces the reader to decode the code.

You must not dumb down idiomatic code for imaginary beginners.

You must prefer one precise comment over artificial extraction when the comment explains a real technical, protocol, performance, security, framework, or domain constraint.

You must not use comments to repeat obvious code.

You must keep one diff focused on one reason.

You must not mix bugfix, feature work, refactor, formatting, migration, and architecture changes without explicit justification.

You must not perform opportunistic refactors outside the requested scope.

You must not make silent architectural changes.

You must not leave dead code, unused exports, obsolete comments, or stale documentation.

You must run or request the relevant formatter, linter, typechecker, and tests when applicable.
