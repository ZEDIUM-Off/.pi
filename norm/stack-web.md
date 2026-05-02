# Web Norm Overlay

## Anchor

You must apply the one-responsibility rule to components, hooks, composables, routes, pages, stores, and UI state.

## Semantic orientation

You must split web code by user-facing responsibility and architectural boundary, not by visual fragments.

## Web rules

You must separate UI rendering, state orchestration, data loading, business rules, validation, authorization, analytics, and provider calls.

You must not put business logic inside presentational components.

You must not put direct persistence or provider access inside UI rendering components.

You must split UI by responsibility, not by visual fragments.

You must not create wrapper components without a distinct UI concern.

You must not split JSX or templates only because they are visually long.

You must allow a larger component when it is coherent, declarative, and owns one UI concern.

You must reject a small component when it mixes UI with domain logic, provider calls, or unrelated state.

You must keep container components focused on orchestration and keep their rendering simple.

You must keep presentational components focused on rendering prepared data and local visual state.

You must keep route and page files focused on composition, routing, and layout.

You must not let route and page files accumulate deep business logic.

## React rules

You must keep React components focused on one UI concern.

You must keep hooks focused on one behavior.

You must not use effects for derivations that can be computed during render.

You must not use context as a dumping ground for unrelated state.

You must not introduce memoization unless it protects a real performance or identity problem.

You must not hide business rules inside JSX branches.

You must keep server/client boundaries explicit when using frameworks that distinguish them.

You must prefer explicit props contracts over implicit object shape guessing.

## Vue rules

You must keep Vue components focused on one UI concern.

You must keep composables focused on one behavior.

You must not use `watch` or `watchEffect` when a `computed` value is sufficient.

You must not hide business rules inside templates.

You must keep props and emits explicit.

You must keep stores focused on coherent state domains.

You must not turn stores into global service containers.
