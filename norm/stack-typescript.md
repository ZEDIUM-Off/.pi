# TypeScript Norm Overlay

## Anchor

You must use TypeScript as a design constraint and verification layer, not as decorative annotation.

## Semantic orientation

You must let inference express local implementation and make types express architectural truth.

## Base rules

You must keep `strict` mode enabled.

You must not weaken TypeScript compiler strictness without an explicit migration reason.

You should enable `forceConsistentCasingInFileNames`, `noImplicitReturns`, and `noUnusedLocals` unless the project has a documented compatibility reason.

You should enable `noUncheckedIndexedAccess` and `exactOptionalPropertyTypes` for new strict codebases unless the project has a documented migration constraint.

You must not use `any` unless it is isolated at a documented boundary or temporary migration seam.

You must prefer `unknown` over `any` for untrusted input.

You must narrow `unknown` before use.

You must validate untrusted data at runtime before treating it as domain data.

You must keep schema validation close to untrusted boundaries such as API input, forms, environment variables, persistence, files, DOM data, and external providers.

You must not trust client-side validation as a backend invariant.

You must use explicit types for exported functions, public APIs, domain models, error models, and architectural boundaries.

You should rely on inference for obvious local implementation details.

You should use `satisfies` when you need structural validation while preserving precise inference.

You must not use type assertions to silence design problems.

You must not use non-null assertions unless the invariant is documented or mechanically guaranteed.

You must not weaken types to satisfy short-term implementation convenience.

You must prefer `const` by default.

You must use `let` only when reassignment is required.

You must never use `var`.

You must use `===` and `!==` instead of coercive equality.

You must use object, array, string, number, boolean, regexp, and function literals instead of object constructors.

You must not use `eval`, `with`, string-based timers, or runtime mutation of built-in prototypes.

You must prefer pure functions for domain transformations.

You must centralize side effects and make them visible in names, types, or boundaries.

You must prefer immutability for shared data, domain values, UI state, and configuration.

You must extract meaningful constants for domain values, protocol values, timeouts, limits, and status codes.

You must not extract constants for obvious local literals that do not carry reusable meaning.

You must keep imports organized, intentional, and unused-free.

You must not keep unused imports, unused variables, unused private members, or unused exports.

You must keep module exports narrow and intentional.

You must not export internals for test convenience without a better seam.

You must not put business rules inside generic utility files.

You must not mix unrelated technologies or layers in the same TypeScript file unless the file is explicitly a framework integration boundary.

## Function style

You should prefer `const` arrow functions for local functions, callbacks, closures, implementation-level helpers, React components, hooks, and Vue composables.

You should prefer arrow functions when lexical `this` is required or when the function is passed as a value.

You should prefer `export const name = (...) => ...` for exported functions when the project style favors expression-based APIs.

You must use explicit exported function types when an exported arrow function is part of a public API.

You should use `function` declarations when overloads, hoisting, declaration merging, recursive self-reference clarity, generator syntax, or framework conventions make them more appropriate.

You must use class or object method syntax for methods unless lexical binding is explicitly required.

You must not mix `function` and arrow styles randomly in the same module.

You must not choose arrow functions only for aesthetics when a declaration better expresses the API contract.

You must not use boolean parameters when they create different behavior paths.

You must split boolean-flag behavior into separate functions or use a named options object with explicit semantic variants.

You must prefix boolean variables and predicates with names such as `is`, `has`, `can`, `should`, or another precise boolean verb.

You must prefer array methods for clear transformations such as `map`, `filter`, `reduce`, `some`, `every`, and `find`.

You must prefer `for...of` or indexed loops when you need early exit, async sequencing, side effects, mutation, or measured hot-path performance.

## Async concurrency

You must prefer `Promise` and `async/await` over raw callbacks for asynchronous flows.

You must not await independent asynchronous operations sequentially.

You must use `Promise.all` when all operations are required and the operation should fail fast.

You must use `Promise.allSettled` when every result matters, including failures.

You must use `Promise.any` only when the first successful result is sufficient.

You must use `Promise.race` only when first-settled behavior is the intended semantics.

You must not use `Promise.all` when partial success must be preserved.

You must not use `Promise.allSettled` when fail-fast behavior is required.

You must preserve input-result ordering when callers rely on positional semantics.

You must map settled results into typed success and failure variants before crossing architectural boundaries.

You must not create unbounded concurrency over large collections.

You must use a concurrency limiter when task count is large, user-controlled, or constrained by external systems.

You must not ignore rejected promises.

You must not fire-and-forget promises unless they are explicitly detached, error-handled, and documented.

You must not use `forEach` with `async` callbacks.

You must use sequential `for...of` with `await` when operations depend on previous results or side-effect order.

You must make long-running async operations cancellable when the caller can abandon the work.

You must accept an `AbortSignal` at async boundaries that perform network, file, stream, timer, worker, or external-provider work.

You must propagate cancellation signals through nested async calls.

You must handle cancellation separately from domain failure when caller behavior differs.

## Advanced type system

You must use advanced TypeScript features only when they preserve or expose domain truth.

You must not use advanced type machinery to impress, compress, or bypass simpler modeling.

You must keep generic type parameters minimal.

You must strongly reconsider any generic type parameter that appears only once.

You must use generic parameters to relate values, not to decorate signatures.

You must push type parameters down when that improves inference.

You must prefer union parameters over overloads when the argument count and return type are the same.

You must use overloads only when call shapes materially differ.

You must not use overloads to avoid modeling a proper union or discriminated union.

You must use conditional types only when the type relation cannot be expressed more simply.

You must document distributive conditional types when distribution is intentional.

You must suppress distributive conditional behavior with tuple wrapping when distribution is not intended.

You must use mapped types when a type transformation is systematic across keys.

You must not use mapped types when an explicit type is clearer and more stable.

You must not create recursive type-level programs without a concrete API or invariant payoff.

You must add type tests for non-trivial public generic types.

You must use literal unions, enums, branded types, or domain-specific types when a string or number has a finite domain meaning.

You must not represent finite domain strings as unrestricted `string`.

You must use discriminated unions for mutually exclusive states and expected error variants.

You must not use boolean flags when they hide domain states.

You must use exhaustive handling for finite unions.

You must not use a default branch that hides missing union variants.

You must not rely on truthiness narrowing when empty string, zero, false, null, or undefined have distinct domain meaning.

## Errors and runtime validation

You must handle JavaScript errors deliberately.

You must treat caught errors as `unknown`.

You must narrow caught errors before reading properties.

You must not assume caught values are `Error` instances.

You must throw `Error` instances, not strings or arbitrary objects, for unexpected failures.

You must model expected failures as typed results or domain error variants when callers must react differently.

You must not mix thrown expected errors and typed expected errors in the same boundary.

You must convert provider errors into domain or infrastructure error variants at the boundary.

You must not leak provider-specific error objects across domain boundaries.

You must not trust static TypeScript types for runtime data that crosses process, network, storage, file, DOM, or user-input boundaries.

## Modules and exports

You must configure TypeScript according to the actual runtime or bundler host.

You must not choose `module`, `moduleResolution`, or file extension conventions by habit.

You must keep ESM and CJS interop explicit.

You must not hide module-system mismatches behind compiler flags.

You must keep import paths aligned with runtime resolution.

You must avoid deep imports across architectural boundaries.

You must prefer named exports for shared modules and domain APIs.

You should use default exports only when framework conventions make them natural.

You must not export large bags of unrelated functions.

You must not use barrel files when they obscure dependency direction, increase circular import risk, or hide architectural boundaries.

You may use barrel files only to define a stable public module surface.

## Testing rules

You must add tests for new behavior, expected error variants, public type-level utilities, non-trivial branches, and bug fixes.

You must test public behavior rather than private implementation details.

You must not export internals only to test them.

You must prefer test seams that preserve architectural boundaries.

You must add type tests for public generic helpers, discriminated unions, branded types, and utility types when misuse would be costly.

You must not use snapshots as a substitute for explicit behavioral assertions.
