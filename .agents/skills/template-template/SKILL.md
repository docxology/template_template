---
name: template-template
description: "Meta-template exemplar — self-referential introspection of the template repo: infrastructure modules, pipeline DAG, security layers, and public exemplar roster."
version: 0.1.0
author: docxology
license: MIT
tags: [exemplar, meta, introspection, autopoietic]
---

# template-template

Project-scoped skill for the in-repo exemplar at
`projects/templates/template_template/`. Load this when working inside the project.

## When to Use

- Working inside the `template_template` exemplar — running scripts, editing source,
  or regenerating outputs.
- Forking this exemplar as the starting scaffold for a new research project.
- Validating that the exemplar's contracts (thin-orchestrator, layer boundaries,
  no-mocks testing) still hold after changes.

## Quick Reference

Use the [standalone verification setup](../../../docs/VERIFICATION.md) to prepare
the SDK and source data. Follow the [rendering pipeline](../../../docs/rendering_pipeline.md)
for live metrics, hydration, and the shared stages.

## Pitfalls

- **Keep scripts thin.** Business logic belongs in `src/` or shared
  `infrastructure/`, not in `scripts/`.
- **No mocks.** All tests must use real data, real files, and real
  computation.
- **Outputs are disposable.** Never hand-edit `output/` — regenerate from
  source and config.
- **Run from the repo root.** Commands assume the template monorepo root
  as working directory unless the child `AGENTS.md` states otherwise.

## Cross-refs

- Project contract: [`AGENTS.md`](../../../AGENTS.md)
- README: [`README.md`](../../../README.md)
- TODO: [`TODO.md`](../../../docs/backlog.md)
- Exemplar roster: [`projects/AGENTS.md`](https://github.com/docxology/template/blob/87704feae0a4490ef7dad9c931d268e8c30273c2/projects/AGENTS.md)
