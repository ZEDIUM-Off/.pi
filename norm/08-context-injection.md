# Context Injection Strategy Norm

## Anchor

You must make norm loading deterministic, granular, and mechanically explainable.

## Semantic orientation

You must inject the smallest set of rules that fully covers the current event, file attributes, and task risk.

## Operational rules

You must use runtime hooks for small global behavior only.

You must use path-aware hooks for file-specific and content-specific norms.

You must use glob matches for stable file identity.

You must use grep matches for observed code attributes inside a file.

You must keep grep rules narrow enough to avoid irrelevant doctrine.

You must avoid content-aware rules for norms needed before creating a new file.

You must keep creation-critical rules in the base stack overlay.

You must use sections or markers when one file owns several related doctrines with different triggers.

You must not duplicate a norm file in multiple injection rules when a hook-level override can express the same routing.

You must prefer inline mode for short mandatory norms.

You must prefer ref mode for broad optional orientation or external documentation.

You must not inject heavy documentation on every prompt.

You must prefer edit/write preflight injection for mutation guardrails.

You must prefer read injection for understanding code attributes.

You must use dedupe-friendly stable source ids.

You must inspect active stack with `/ct-detail` when the model receives too much or too little doctrine.
