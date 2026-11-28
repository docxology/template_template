# Template Meta-Project Documentation

This project measures the Docxology Template repository and builds a manuscript
describing its architecture, pipeline, and documentation practices.

| Task | Guide |
| --- | --- |
| Set up the SDK and complete source data, then run the test suite | [Verification](VERIFICATION.md) |
| Generate live evidence and render the publication | [Rendering pipeline](rendering_pipeline.md) |
| Edit paper chapters, citations, or configuration | [Manuscript source](manuscript/README.md), [authoring guide](manuscript_guide.md) |
| Understand the project code and evidence contracts | [Architecture](architecture.md), [source](source.md), [package](package.md), [data](data.md) |
| Locate producers and generated figures | [Scripts](scripts.md), [figures](figures.md) |
| Find the test plan and failure diagnostics | [Test suite](testing/README.md), [test philosophy](testing_philosophy.md), [troubleshooting](troubleshooting.md) |
| Fork the project or review publishing history | [Standalone guide](standalone.md), [publication consistency review](publication_consistency_review.md), [backlog](backlog.md) |
| Find repository conventions for changes | [Agent guidance](AGENTS.md), [workflow](agent_instructions.md) |

The [bundled infrastructure](../_template_resources/infrastructure/README.md) is part of the Template source export.
The evidence producers and tests use the Template 4.0.1 wheel and the complete public
reference prepared by the [verification setup](VERIFICATION.md#prepare-the-sdk-and-the-reference).
Build the readers with the separately pinned checkout in the [rendering pipeline](rendering_pipeline.md#render-and-validate).

The tracked `output/` tree contains the publication snapshot. The export receipt identifies
the imported source revision, and the publication-tree inventory records managed source paths.
