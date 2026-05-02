# Norm Evolution Norm

## Anchor

You must let the norm reorganize itself by observed failure modes, shared attributes, exceptions, and predictive value.

## Semantic orientation

You must treat each rule as an attributed object in a living graph: observe, classify, inherit, promote, specialize, except, and revise.

## Operational rules

You must not add a rule before naming the concrete failure mode it prevents.

You must describe every new rule by attributes: scope, trigger, failure mode, target behavior, exception, and verification method.

You must compare a new rule with existing rule classes before creating a new file.

You must attach a rule to the most predictive existing norm file when its attributes match that file's philosophy.

You must create a new norm file only when several rules share a stable philosophy, trigger, or maintenance reason not owned by an existing file.

You must promote repeated local rules into a more general rule when they share the same failure mode.

You must demote a general rule into a stack-specific or trigger-specific rule when it creates noise outside its real scope.

You must create exceptions when a valid local case should not inherit a general rule.

You must remove or weaken rules that do not predict or prevent real failures.

You must not duplicate the same rule across files.

You must reference a rule from another file instead of redefining it.

You must keep behavior rules separate from code rules.

You must keep stack-specific rules out of global core files.

You must prefer deterministic injection over agent-chosen reading.

You must tighten injection matches when a rule is useful only for specific code attributes.

You must broaden injection matches when a rule is repeatedly needed but absent.

You must run `/ct-explain <path> <hook>` when injection coverage is unclear.

You must run `/ct-validate` after editing `CONTEXT.json`.

You must update `CONTEXT.json` when a rule's trigger, scope, or file location changes.
