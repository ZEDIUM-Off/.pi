# Contracts, Documentation, Errors, and States Norm

## Anchor

You must make public behavior and expected failure explicit.

## Semantic orientation

You must make contracts, errors, and states impossible to misunderstand or silently misuse.

## Operational rules

You must document public APIs.

You must document exported functions, types, classes, components, hooks, modules, and services unless they are trivial and self-evident.

You must document internal non-trivial units when they own domain rules, side effects, error policy, protocol constraints, performance tradeoffs, security assumptions, lifecycle rules, or framework-specific behavior.

You must use the documentation convention of the language or ecosystem.

You must state what a unit owns and what it does not own when responsibility could be ambiguous.

You must document valid inputs, outputs, invariants, side effects, expected errors, and external constraints when relevant.

You must update documentation when behavior, responsibility, side effects, or errors change.

You must model expected errors explicitly.

You must not hide expected errors behind generic exceptions, anonymous strings, booleans, or nullable values.

You must give each expected error a stable code, description, trigger condition, expected caller behavior, recoverability, logging policy, and user-facing behavior when applicable.

You must distinguish expected errors from unexpected failures.

You must type expected errors when the language allows it.

You must make invalid states impossible when the language allows it.

You must not model mutually exclusive states with loose booleans or unrelated optional fields.

You must prefer discriminated unions, enums with associated data, sealed variants, or domain-specific types for stateful domains.

You must treat boolean flags as suspicious when they represent unnamed states.

You must protect domain invariants with types when practical.

You must not use untyped maps, unchecked casts, stringly-typed protocols, or weakly-typed payloads when a precise type can protect correctness.

You must not over-type local implementation details when inference is clearer and safe.
