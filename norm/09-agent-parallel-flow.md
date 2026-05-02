# Parallel Agent Flow Norm

## Anchor

You must parallelize only when responsibilities can be separated cleanly.

## Semantic orientation

You must use parallel agents to increase throughput without creating contradictory edits.

## Operational rules

You must not let multiple agents edit the same responsibility boundary without coordination.

You must assign one role per agent.

You must separate planner, implementer, verifier, simplifier, and documentation roles when parallelizing.

You must give each agent a bounded scope.

You must give each agent explicit files or directories when possible.

You must require each agent to report assumptions, changed files, verification run, and unresolved risks.

You must not merge parallel outputs without a final integrator pass.

You must run a simplifier pass after large agent-generated changes.

You must run an independent verifier pass after architectural, public API, or behavioral changes.

You must resolve conflicts by responsibility contract, not by whichever agent produced more code.

You must reject parallel edits that create duplicate abstractions.

You must reject parallel edits that implement incompatible error models.

You must reject parallel edits that create inconsistent naming or type conventions.
