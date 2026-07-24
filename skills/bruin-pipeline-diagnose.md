---
name: pipeline-diagnose
description: Diagnose a failed Bruin pipeline run and propose a fix.
api: Bruin CLI (https://bruin-data.github.io/bruin/)
source: https://bruin-data.github.io/bruin/commands/ai-skills.html
method: searched
commands: [validate, render, run]
---

# Diagnose a failed Bruin pipeline run

Bruin's bundled `pipeline-diagnose` agent skill. Install it into a repo with
`bruin ai skills pipeline-diagnose`. Follow these steps to triage a failure.

## Steps

1. **Validate the project.** Run `bruin validate` to surface configuration,
   dependency, and asset-definition errors before touching data.
2. **Inspect the compiled asset.** Run `bruin render <asset>` to see the exact
   compiled SQL/query Bruin executes, so you can distinguish a config problem
   from a query problem.
3. **Reproduce narrowly.** Re-run the single failing asset with
   `bruin run <path/to/asset>` (rather than the whole pipeline) and read the
   local logs Bruin emits.
4. **Check upstream lineage.** Use `bruin lineage` to confirm whether the
   failure originates upstream (a dependency asset) rather than in the asset
   that reported the error.
5. **Propose the minimal fix** (config, connection, or query) and re-validate
   with `bruin validate` before re-running.

## Rules

- Never fabricate connection credentials; they live in `.bruin.yml`.
- Prefer `validate`/`render` (read-only) before any `run` that materializes data.
