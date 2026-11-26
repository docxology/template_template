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

The separately exported `_template_resources/` tree holds Template SDK resources.
The tracked `output/` tree contains a publication snapshot. The export and publication-tree receipts
record the imported source and output snapshot. See
[verification](VERIFICATION.md) for a fresh build in an isolated checkout.
