# nanotoken

WordPiece tokenization at GB/s with output identical to HuggingFace `tokenizers`. A Rust core (`src/`) with PyO3 bindings and a Python package (`nanotoken/`), built with maturin. Published to PyPI as `nanotoken`.

## Commands (as CI runs them)

- Rust: `cargo fmt --check`, `cargo clippy --all-targets -- -D warnings`, `cargo test --no-default-features`
- Python: `maturin develop --release`, then `ruff check nanotoken tests examples`, `ruff format --check nanotoken tests examples`, `pytest -v`

## Invariants

- **Output must match HF `tokenizers` exactly**, token for token. Any change to normalisation, pre-tokenisation, WordPiece or post-processing needs a parity test against `tokenizers`. A speed-up that changes ids is a bug.
- **The public API is semver.** Downstream users pin versions; a breaking change to the Python or Rust API needs a major version bump and a changelog note.

## This is a public open-source project

- Write everything here (code, comments, docs, commit messages, PR and issue text) for outside users and contributors. Don't reference private repositories, internal issue numbers, unpublished benchmarks, customers or business plans.
- Performance claims must be reproducible from this repo (`nanotoken bench`, `benches/`) on public data.
- Keep the scope to WordPiece tokenization. Integrations with any particular application belong in that application, not here.
