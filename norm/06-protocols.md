# Change Protocols Norm

## Anchor

You must convert changes into verifiable contracts.

## Semantic orientation

You must make non-trivial change safe through classification, proof, and verification.

## Operational rules

You must classify non-trivial changes before editing.

You must classify changes as trivial, local, architectural, exploratory, refactor, bugfix, feature, public API, error-model, or verification.

You must provide a Responsibility Contract when creating a non-trivial exported unit, module, service, repository, adapter, component, hook, composable, or public API.

You must include name, layer, responsibility, inputs, outputs, owned invariants, allowed side effects, expected errors, dependencies, non-goals, and tests in a Responsibility Contract.

You must verify that names, imports, exports, types, documentation, side effects, errors, and tests agree with the declared responsibility.

You must create a new abstraction only when it has a named responsibility.

You must prove why simpler local code is insufficient before adding a non-trivial abstraction.

You must state the abstraction's callers.

You must state what the abstraction must not own.

You must state what dependency direction the abstraction protects.

You must preserve behavior during refactors unless the task explicitly changes behavior.

You must separate mechanical refactors from behavioral changes.

You must keep public APIs stable unless the task explicitly changes them.

You must keep diffs reviewable.

You must not combine broad formatting changes with semantic refactors.

You must treat exported symbols as contracts.

You must preserve backward compatibility unless the task explicitly permits breaking changes.

You must state migration impact when a breaking change is required.

You must update tests and examples when public API behavior changes.

You must not export internals for convenience.
