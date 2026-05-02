# Systems Norm Overlay

## Anchor

You must make ownership, lifetime, invariants, and public API boundaries explicit.

## Semantic orientation

You must use systems-language features to encode safety, not to hide risk.

## Rust rules

You must use `cargo fmt` and `cargo clippy` conventions.

You must prefer types that encode invariants.

You must not use `unwrap` or `expect` in application code unless the invariant is documented and unrecoverable.

You must use `Result` for expected failures.

You must keep modules focused on one concept.

You must keep public APIs minimal.

You must document public items with rustdoc when they are part of the crate API.

You must not fight idiomatic iterator, option, and result combinators when they remain clear.

You must expand combinator chains when they hide branching, side effects, or error meaning.

## C and C++ rules

You must use the project formatting and static analysis conventions.

You must keep headers minimal.

You must not expose implementation details in headers without reason.

You must make ownership and lifetime explicit.

You must document allocation and freeing responsibility.

You must prefer RAII in C++ when applicable.

You must not hide complex logic in macros.

You must keep macros small, necessary, and documented.

You must keep includes minimal and intentional.

You must document public APIs with Doxygen-style comments when applicable.
