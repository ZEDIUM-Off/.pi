# Responsibility Norm

## Anchor

You must make every unit own one responsibility at its abstraction level.

## Semantic orientation

You must verify responsibility through code facts, not through a nice description.

## Operational rules

You must treat functions, methods, classes, modules, components, hooks, composables, services, repositories, adapters, routes, tests, and commands as code units.

You must ensure a function owns one operation.

You must ensure a component owns one UI concern.

You must ensure a hook or composable owns one behavior.

You must ensure a service or use-case owns one application action.

You must ensure a repository owns one persistence boundary.

You must ensure an adapter owns one translation between interfaces.

You must ensure a module owns one concept.

You must reject a code unit whose name, imports, exports, side effects, errors, documentation, and tests do not tell the same truth.

You must not mix UI, persistence, business logic, validation, analytics, authorization, provider logic, and formatting inside the same implementation unit unless the unit is explicitly an orchestration boundary.

You must allow orchestration units to coordinate multiple responsibilities, but you must not allow them to implement the internal logic of those responsibilities.

You must keep I/O out of pure domain logic.

You must keep business rules out of rendering code.

You must keep provider-specific details behind adapters, gateways, or repositories.

You must keep formatting and presentation concerns out of domain rules.

You must reject a responsibility description if the imports contradict the declared layer.

You must reject a responsibility description if callers use the unit for unrelated reasons.

You must not split code because it is long.

You must split code when responsibilities, effects, invariants, dependencies, or reasons to change are separable.

You must prefer a larger coherent unit over several tiny artificial units.

You must reject a small unit if it mixes responsibilities.

You must not create wrapper around wrapper without functional justification.

You must not hide simple local logic behind unnecessary file navigation.

You must ensure every extraction pays rent.

You must ensure every abstraction names a responsibility.

You must introduce a new name only when it earns its existence.

You must not create abstractions for speculative reuse.

You must not promote code to shared scope until it is truly shared by multiple real consumers.

You must prefer duplication over the wrong abstraction.

You must eventually extract stable duplication into a named concept when it has a shared reason to change.

You must treat generic names such as `utils`, `helpers`, `common`, `misc`, `manager`, `handler`, `service`, and `processor` as invalid until domain and layer qualification proves their meaning.
