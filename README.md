# pypi-package-uv-template

A GitHub repository template for Python packages using [uv](https://docs.astral.sh/uv/), with ruff, mypy, pytest, pre-commit, MkDocs (API docs via mkdocstrings), GitHub Pages, and automatic PyPI release via trusted publishing.

**Use this template** — click "Use this template" above to create a new repo from this template.

## Installation

```bash
uv sync
```

Or with pip:

```bash
pip install -e .
```

Python 3.12+ is required (see [.python-version](.python-version)). uv will use it automatically.

## Usage

```bash
python -m pypi_package_uv_template
```

## Development

1. Install dependencies (including dev): `uv sync`
2. Install pre-commit hooks so checks run on commit: `pre-commit install`
3. Run checks manually:
   - `uv run ruff check .`
   - `uv run ruff format --check .`
   - `uv run mypy src/`
   - `uv run pytest`
4. Serve docs locally: `uv run mkdocs serve`
5. Add dependencies: `uv add <pkg>` or `uv add --group dev <pkg>`

To validate the whole repo: `pre-commit run --all-files`

## Documentation

API documentation is built with [MkDocs](https://www.mkdocs.org/) and [mkdocstrings](https://mkdocstrings.github.io/), and deployed to **GitHub Pages** on every push to `main`.

- **Local:** `uv run mkdocs serve`
- **Online:** After enabling Pages, docs will be at `https://<owner>.github.io/<repo>/`

To enable: In the repo **Settings → Pages**, set **Source** to **GitHub Actions** so Pages is served from the workflow.

## Releasing

Releases are published to **PyPI** automatically when you create a **GitHub Release**.

1. Configure **trusted publishing** for this repo on PyPI: go to your project on [pypi.org](https://pypi.org) → **Publishing** → **Add a new pending publisher**, and add the GitHub repo with workflow name `Publish to PyPI` and the appropriate ref (e.g. `release` for tags).
2. Create a new release (e.g. tag `v0.1.0`) and publish it; the [publish workflow](.github/workflows/publish.yml) will build and upload the package via OIDC (no API token needed).

## License

See [LICENSE](LICENSE) if present.
