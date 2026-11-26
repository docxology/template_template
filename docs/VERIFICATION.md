# Verification

The standalone project uses two independent inputs. The executable SDK is
`research-project-template==4.0.1`. The complete public reference supplies the
files measured by the manuscript, including the public exemplar roster and
tests. A wheel install supplies the SDK. Keep the reference checkout off the
Python import path and use a separate project checkout for generated outputs.

## Prepare the SDK and the reference

Install Git, [uv](https://docs.astral.sh/uv/), and Python 3.14. From the
standalone project root, choose a workspace outside the project to hold the
reference and wheel. The reference pin is the source commit recorded in
[the export receipt](../.template-export.json).

```bash
workspace="$(mktemp -d)"
git init "$workspace/reference"
git -C "$workspace/reference" remote add origin https://github.com/docxology/template.git
git -C "$workspace/reference" fetch --depth 1 origin d160eb9c90eec18e365117c3ccaef731c47d8604
git -C "$workspace/reference" checkout --detach FETCH_HEAD
git -C "$workspace/reference" \
  -c submodule.infrastructure/steganography/kmyth.url=https://github.com/NationalSecurityAgency/kmyth.git \
  submodule update --init --depth 1 -- infrastructure/steganography/kmyth
uv build --wheel --out-dir "$workspace/wheels" "$workspace/reference"
uv venv --python 3.14 "$workspace/venv"
sdk_python="$workspace/venv/bin/python"
```

The submodule command uses the public upstream for this exact gitlink. Install
the locked Linux dependency versions and the built wheel into the
external project environment created above. The project bootstrap selects
the SDK from outside the project checkout. The lock's editable SDK entry applies to an in-repository build.

```bash
"$sdk_python" - <<'PY' > "$workspace/requirements.txt"
import tomllib
with open("uv.lock", "rb") as stream:
    packages = tomllib.load(stream)["package"]
for package in packages:
    if "registry" in package["source"] and package["name"] != "colorama":
        print(f'{package["name"]}=={package["version"]}')
PY
uv pip install --python "$sdk_python" -r "$workspace/requirements.txt" \
  "$workspace/wheels/research_project_template-4.0.1-py3-none-any.whl"
export TEMPLATE_PUBLIC_REFERENCE_ROOT="$workspace/reference"
export TEMPLATE_PUBLIC_REFERENCE_COMMIT="$(git -C "$workspace/reference" rev-parse HEAD)"
export TEMPLATE_PUBLIC_REFERENCE_FINGERPRINT="$("$sdk_python" -I - "$workspace/reference" <<'PY'
from pathlib import Path
import sys
from infrastructure.project.public_acceptance_scope import RuntimeScope
from infrastructure.project.public_reference import SnapshotReader, _path_admission

root = Path(sys.argv[1])
reader = SnapshotReader(root)
print(RuntimeScope(root, "root").source_identity(path_admission=_path_admission(reader)))
PY
)"
```

The SDK checks the reference commit, fingerprint, submodule identity, and
source inventory on admission and before accepting results. See
[the producer and renderer workflow](rendering_pipeline.md) to render the
publication after setup.

## Run the native tests

```bash
"$sdk_python" -I -m pytest tests/ --cov=src --cov-fail-under=90
```

Use the full [test suite](testing/README.md) for changes to manuscript paths,
source discovery, or evidence. The native test run and shared renderer
validation produce separate receipts.
