---
name: quality-check-investigate
description: Investigate why a Bruin data quality check failed.
api: Bruin CLI (https://bruin-data.github.io/bruin/)
source: https://bruin-data.github.io/bruin/commands/ai-skills.html
method: searched
commands: [validate, render, query]
---

# Investigate a Bruin quality-check failure

Bruin's bundled `quality-check-investigate` agent skill. Install with
`bruin ai skills quality-check-investigate`.

## Steps

1. **Confirm the check definition.** Run `bruin validate` to ensure the failing
   quality check (e.g. `not_null`, `unique`, `positive`, or a custom SQL check)
   is well-formed.
2. **Render the check.** Run `bruin render <asset>` to see the compiled query
   the check runs against the materialized table.
3. **Query the offending rows.** Use `bruin query` against the connection to
   pull the specific rows violating the check (e.g. nulls, duplicates,
   out-of-range values).
4. **Attribute the cause** to source data, a transformation, or a stale
   materialization, and recommend the fix.
5. **Re-validate** with `bruin validate` after any change.

## Rules

- Read-only investigation first: `query`/`render` before re-running the asset.
- Do not weaken a quality check to make it pass; fix the data or the transform.
