---
name: schema-drift-check
description: Detect and report schema changes (drift) in a Bruin pipeline.
api: Bruin CLI (https://bruin-data.github.io/bruin/)
source: https://bruin-data.github.io/bruin/commands/ai-skills.html
method: searched
commands: [validate, query]
---

# Detect schema drift

Bruin's bundled `schema-drift-check` agent skill. Install with
`bruin ai skills schema-drift-check`.

## Steps

1. **Validate current definitions.** Run `bruin validate` so the declared asset
   columns/types are known-good.
2. **Introspect the live schema.** Use `bruin query` to read the current column
   set and types of the materialized table from its connection.
3. **Diff declared vs. live.** Compare the asset's declared columns against the
   live schema; flag added, removed, or retyped columns.
4. **Assess blast radius** with `bruin lineage` to see which downstream assets
   consume the drifted columns.
5. **Report the drift** with the exact columns and recommend updating the asset
   definition or the upstream source mapping.

## Rules

- Never assume column types; read them from the live connection with `query`.
- Surface drift; do not silently auto-migrate schemas.
