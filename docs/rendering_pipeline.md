# Rendering Pipeline

The [manuscript source](manuscript/) contains numbered chapters, a preamble,
and [the bibliography](manuscript/references.bib). The
[project configuration](manuscript/config.yaml) declares publication and test
metadata. Build from a fresh project checkout to keep its release snapshot
separate from the newly derived results.

## Register the standalone project

From a directory outside the project, clone the shared renderer and register
a separate clone of this project's source at the revision to render.

```bash
git clone https://github.com/docxology/template.git
cd template
git checkout --detach 87704feae0a4490ef7dad9c931d268e8c30273c2
uv sync --locked --no-dev --python 3.14
renderer="$PWD"
mkdir -p projects/working
git clone https://github.com/docxology/template_template.git projects/working/template_template
cd projects/working/template_template
```

Follow [the SDK and reference setup](VERIFICATION.md#prepare-the-sdk-and-the-reference)
in this project checkout. Install Pandoc 3.14, pandoc-crossref 0.3.26, and a
TeX installation with XeLaTeX and BibTeX for the renderer.

## Generate evidence and hydrate the manuscript

Run the project's real producers with the admitted source reference in the
same shell. In this disposable checkout, move aside the tracked output tree
before generating new results.

```bash
mv output ../template_template-published-output
"$sdk_python" -I scripts/generate_architecture_viz.py
"$sdk_python" -I scripts/generate_manuscript_metrics.py
```

The producers write four architecture plots to `output/figures/` and the
live introspection receipt to `output/data/metrics.json`. Metric substitution
creates hydrated chapters under `output/manuscript/` with the bibliography,
preamble, and configuration needed for rendering.

## Render and validate

Run the pinned shared renderer from its own checkout. Clear the project
producer’s source reference binding so the renderer uses its own source
checkout and version.

```bash
cd "$renderer"
unset TEMPLATE_PUBLIC_REFERENCE_ROOT TEMPLATE_PUBLIC_REFERENCE_COMMIT TEMPLATE_PUBLIC_REFERENCE_FINGERPRINT
uv run --no-sync python scripts/pipeline/stage_03_render.py --project working/template_template
uv run --no-sync python scripts/pipeline/stage_04_validate.py --project working/template_template
```

The stages write results below `projects/working/template_template/output/`.
Look for the combined publication in `pdf/template_template_combined.pdf`
and the validation and source provenance receipts under `reports/`.
