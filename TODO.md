# template_template TODO

This backlog is future-only. Completed validation and dated review evidence are preserved in
[`docs/maintenance/exemplar-backlog-history.md`](https://github.com/docxology/template/blob/main/docs/maintenance/exemplar-backlog-history.md)
or in source-owned generated receipts. Each active row must retain a stable ID, size, dependency,
next action, proving artifact, acceptance command, and negative control; absence of an owner or external receipt
keeps a capability blocked rather than silently promoting it.

## Backlog operating rules

- Keep deterministic and offline defaults unchanged unless an upcoming row explicitly scopes an opt-in.
- Do not close a row until its producer, artifact, consumer, gate, and failing negative control are present.
- Treat unavailable network, LLM, container, formal-tool, and publication paths as explicit skips
  or blockers.
- Re-derive counts and receipts from live source data; never copy measurements into this planning file.

## Integrity and template-status gaps

- Keep this exemplar as the template-about-template reference for architecture,
  metrics, and confidentiality invariants.
- Keep every generated metric derived from the live tree and generated-doc
  sources rather than copied literals.
- Public-roster and confidentiality-policy changes require a compatibility note
  in the same revision as the generated roster update.

## Configurable-surface gaps

- Keep `manuscript/config.yaml.example` as the copy-and-customize metadata
  starting point (shape-synced with the live config: split DOIs,
  `repository_url`, `published_artifacts`, `transmission_bookends`).
- Explicit config keys are required before any new manuscript metric becomes
  user-tunable.

## Documentation and signposting gaps

- Keep README and AGENTS linked to generated public-scope docs instead of
  duplicating the rotating project list.
- The fork guidance is a documentation requirement for any downstream copy of
  this exemplar; it is not a claim that a downstream fork exists here.

## Test and validator gaps

- Negative controls for stale generated metrics and accidental inclusion of
  local-only project paths are bound by `tests/metrics/test_stale_metrics_control.py` to
  the generated metric schema and live public-scope paths.
- Schema tests are required before changing the metrics JSON consumed by the
  manuscript.
- Keep the manuscript evidence-contract test green as new generated metrics or
  cited empirical values are introduced; live counts remain token-injected, and
  policy percentages remain bound to executable configuration.
- Use `infrastructure.core.pipeline.artifacts.snapshot_current_artifact_manifest`
  for single-stage analysis, render, and copy checks. It writes a
  `current-output-snapshot` manifest without requiring a full
  `PipelineExecutor` run.
- Validate actual introspection branch reachability before adding coverage;
  preserve honest limitations and use real inputs/environments rather than mocks.

## Platform 4 acceptance scope

The rows below describe remaining acceptance and repairs, not a claim that
existing implementations are missing. Inspect current source and the dated
[program record](https://github.com/docxology/template/blob/main/docs/maintenance/platform-4-upgrade.md) first.
Set `P4_PROJECT_ROOT` to this project's absolute canonical checkout and prepare
its locked environment using the [runtime matrix guide](https://github.com/docxology/template/blob/main/docs/development/public-runtime-matrix.md).
Run one project per pytest process under the producer's declared finite outer
deadline and source-owned per-case limits. The whole-selection domain command
is an explicit acceptance opt-in: prepare its declared unpaid tool/model
prerequisites, disable test model pulls, and override default marker exclusions
with `-m ""`. Own-source acceptance requires nonempty complete collection, real
behavior and at least 90% branch coverage; a focused test or previous revision's
result does not close the row. Missing preparation remains blocked.

Native and live lanes additionally require actual producers, independent
content/visual/domain checks and current source/tool/model identities; ordinary
unit tests do not replace them. Apply the root `P4-RUNTIME-MATRIX`,
`P4-INSTALLED-MATRIX`, `P4-UNPAID-CAPABILITIES` and publication contracts.
Unavailable required tools/providers remain blocked. Independent intended
versions come from the program record and package metadata, and remain separate
from genuinely published versions.

## Minor upcoming

| ID | Status | Size | Dependency | Next action / unblock condition | Proving artifact | Acceptance command | Negative control |
| --- | --- | --- | --- | --- | --- | --- | --- |
No active rows are currently scoped at this size.

## Medium upcoming

| ID | Status | Size | Dependency | Next action / unblock condition | Proving artifact | Acceptance command | Negative control |
| --- | --- | --- | --- | --- | --- | --- | --- |
| `P4-TEMPLATE-DOMAIN-1` | partial | Medium | All other exemplar and source/documentation integration; P4-PUBLIC-REFERENCE-1 | Regenerate this exemplar last and independently recount final public source, architecture, DAG and manuscript metrics using the admitted Root source rather than ambient Git/PATH or stale snapshots. | independent final metrics, source/DAG and confidentiality receipts | `OLLAMA_SKIP_TEST_MODEL_PULL=1 uv run --locked --no-sync --offline --project "$P4_PROJECT_ROOT" --directory "$P4_PROJECT_ROOT" python -m pytest tests/ --cov=src --cov-branch --cov-fail-under=90 --timeout=120 -m ""`; execute each declared opt-in capability producer under the root acceptance profile | private same-leaf aliases, forged PATH counts, stale source identities or copied literal metrics must fail |
| `P4-TEMPLATE-MANUSCRIPT-1` | open | Medium | P4-TEMPLATE-DOMAIN-1; reviewed per-project render/native producer contracts and prepared tools | Regenerate final architecture diagrams, manuscript tables, source metrics and figures after all other changes; bind every claim to generator-owned current evidence. Audit configurable inputs, thin orchestration, injected variables and accessibility; repair only verified gaps. | current analysis/hydration/source bindings, all declared format outputs and visual/content negative controls | `uv run --no-sync --offline python scripts/pipeline/stage_02_analysis.py --project templates/template_template`; then canonical `stage_03_render.py` and `stage_04_validate.py` with the same selection and the required native producer | stale variables, unresolved content, missing formats, incorrect figures/citations or wrong-source visual evidence must fail |
| `P4-TEMPLATE-PORTABILITY-1` | open | Medium | P4-TEMPLATE-DOMAIN-1; P4-TEMPLATE-MANUSCRIPT-1; built genuine SDK/provider; reviewed packaging projection | Execute all supported runtime and installed-wheel cells and fresh disposable standalone setup/full own-suite/format replay before publication. Verify independent intended version, source/export digest, public resource completeness and reviewed packaging projection; remote promotion is a separate row. | complete runtime/installed and pre-push isolated export/reinstallation receipts | `uv run --no-sync --offline python scripts/gates/installed_public.py --project templates/template_template --python "3.12=$P4_PYTHON312" --python "3.13=$P4_PYTHON313" --python "3.14=$P4_PYTHON314"`; then complete isolated exported suite and declared formats | parent-relative imports, editable provider substitution, absent cells, incomplete exports, invented publication metadata or remote content mismatch must fail |

| `P4-TEMPLATE-REMOTE-1` | open | Medium | P4-TEMPLATE-PORTABILITY-1; P4-STANDALONE-MAIN-1; actual publication authority | After pre-push acceptance and authorized destination promotion, independently verify remote main commit, retrieved export-content/artifact hashes, genuine published version and working declared repository/publication URLs; retain existing releases and deposits. Keep unpublished projects explicit until genuine first receipts. | actual destination/version/commit, retrieval-content parity and applicable DOI/URL receipts | `git ls-remote "$P4_DESTINATION" refs/heads/main`; retrieve/reinstall the actual promoted artifact and rerun the isolated own-suite and declared format checks | a planned version, nonexistent destination, fabricated DOI, stale remote parent or mismatched retrieved export must fail |

## Major upcoming

| ID | Status | Size | Dependency | Next action / unblock condition | Proving artifact | Acceptance command | Negative control |
| --- | --- | --- | --- | --- | --- | --- | --- |
No active rows are currently scoped at this size.

## Backlog status

Rows remain active until the acceptance command and negative control pass in the same source revision.
A blocked row is a deliberate boundary, not a skipped success.

## Workflowz review — 2026-11-10

- [ ] **WZ-20261110-01 — P2: Pin and actually validate the Python 3.15 development lane.**
  - **Evidence:** `.python-version:1` requests only `3.15`, while `pyproject.toml:57` declares tested versions only through 3.14. This is a validation/reproducibility gap, not evidence that any dependency is outdated.
  - **Observable outcome:** Set the development request to `3.15.2`; after the complete locked own-suite passes on that exact interpreter, add `3.15` to `tested_python_versions`. Keep the existing `requires-python` range unchanged. If a locked dependency or the declared SDK context actually prevents the run, record that concrete constraint and do not claim a tested 3.15 cell.
  - **Acceptance probe (from repository root, in the declared prepared SDK/dev environment):**
    ```bash
    uv run --locked --no-sync --python 3.15.2 python -c 'import sys; assert sys.version_info[:3] == (3, 15, 2), sys.version'
    uv run --locked --no-sync --python 3.15.2 python -m pytest
    ```
    The first command must report the exact selected interpreter through its assertion and the second must finish all collected tests successfully.
  - **Negative control:** `uv run --locked --no-sync --python 3.14 python -c 'import sys; assert sys.version_info[:3] == (3, 15, 2), sys.version'` must fail the version assertion when that interpreter is available; a missing dependency or missing interpreter must not be recorded as a passing 3.15.2 validation.
  - **Dependencies/constraints:** Requires Python 3.15.2, the locked dev dependencies, and the local/admitted `research-project-template` arrangement described at `pyproject.toml:50-52`. Do not relax the lock or silently upgrade a dependency to make the cell pass.

- [ ] **WZ-20261110-02 — P2: Restore the intended release C flags in the pinned Kmyth SGX build.**
  - **Evidence:** `_template_resources/infrastructure/steganography/kmyth/sgx/Makefile:111` appends release definitions to `GX_COMMON_CFLAGS`, whereas the initialized and consumed variable is `SGX_COMMON_CFLAGS` at `_template_resources/infrastructure/steganography/kmyth/sgx/Makefile:95` and `_template_resources/infrastructure/steganography/kmyth/sgx/Makefile:96`. Consequently the ordinary release branch does not add the documented `-DNDEBUG -UEDEBUG` flags.
  - **Observable outcome:** The release branch updates `SGX_COMMON_CFLAGS`, while debug and prerelease branches retain their existing distinct flags. Carry the one-line correction as a documented downstream patch or an explicitly reviewed upstream fix.
  - **Acceptance probe (from repository root):**
    ```bash
    make -s -C _template_resources/infrastructure/steganography/kmyth/sgx \
      --eval='print-review-cflags: ; @echo $(SGX_COMMON_CFLAGS)' \
      print-review-cflags SGX_DEBUG=0 SGX_PRERELEASE=0
    ```
    The emitted release flags must include both `-DNDEBUG` and `-UEDEBUG`, and must not include `-DDEBUG`.
  - **Negative control:** Repeat with `SGX_DEBUG=1 SGX_PRERELEASE=0`; that output must include `-DDEBUG` and `-UNDEBUG`, demonstrating that the release definitions were not indiscriminately applied to every build mode.
  - **Dependencies/constraints:** GNU make is sufficient for this build-contract probe; no SGX compiler or hardware is required. Kmyth is pinned third-party source (`AGENTS.md:97`), so preserve upstream/version provenance and do not perform an unrelated vendor upgrade.

- [ ] **WZ-20261110-03 — P3: Collect network-test headers from the network-test include directory.**
  - **Evidence:** `_template_resources/infrastructure/steganography/kmyth/Makefile:159` defines `TEST_NETWORK_INC_DIR` as `$(TEST_INC_DIR)/network`, but `_template_resources/infrastructure/steganography/kmyth/Makefile:160` expands `TEST_NETWORK_HEADERS` using `TEST_UTIL_INC_DIR`. The declared network-header set can therefore be empty or sourced from an unrelated directory.
  - **Observable outcome:** `TEST_NETWORK_HEADERS` expands the headers under `TEST_NETWORK_INC_DIR`; changing the unrelated utility include variable no longer changes that network-header list.
  - **Acceptance probe (from repository root):**
    ```bash
    make -s -C _template_resources/infrastructure/steganography/kmyth \
      --eval='check-review-network-headers: ; @test "$(TEST_NETWORK_HEADERS)" = "$(wildcard $(TEST_NETWORK_INC_DIR)/*.h)"' \
      check-review-network-headers TEST_UTIL_INC_DIR=/nonexistent-review-path
    ```
    With the checked-in network test headers present, this make-based equality check must exit successfully and remain independent of the deliberately invalid utility path.
  - **Negative control:** Restoring the `TEST_UTIL_INC_DIR` wildcard must make the same probe fail when `test/include/network` contains headers and `/nonexistent-review-path` does not; an empty genuine network-header directory must not be mistaken for coverage of this control.
  - **Dependencies/constraints:** Requires GNU make and the checked-in network test headers, not a TPM build. As with WZ-20261110-02, preserve the pinned Kmyth provenance noted at `AGENTS.md:97` and avoid an unrelated third-party refresh.
