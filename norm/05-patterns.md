# Design Pattern Norm

## Anchor

You must use design patterns as problem-shape vocabulary, not decoration.

## Semantic orientation

You must justify patterns by the concrete coupling, creation, behavioral, lifecycle, or extension problem they solve.

## Operational rules

You must introduce a design pattern only when the problem shape matches the pattern intent.

You must not introduce a pattern because it is known, elegant, or reusable in theory.

You must not use pattern names to justify abstractions.

You must prefer simpler code when the pattern does not reduce complexity.

You must document a Pattern Admission Record before introducing a non-trivial pattern.

You must state the pattern name, problem shape, why simpler code is insufficient, participants, stable interface, replaceable parts, failure mode if misused, and why the pattern is not premature abstraction.

You should use Adapter for incompatible interfaces.

You should use Facade for simplifying complex subsystems.

You should use Strategy for interchangeable algorithms.

You should use State for behavior that varies by lifecycle state.

You should use Command for actions that must be queued, retried, logged, serialized, undone, or passed around.

You should use Observer for multiple subscribers reacting to events.

You should use Proxy for access control, caching, lazy loading, instrumentation, or remote boundaries.

You should use Decorator for composable behavior around a stable interface.

You should use Builder for complex staged construction or invariant-heavy object creation.

You must reject patterns that create wrapper hell, god objects, unnecessary indirection, or speculative extension points.
