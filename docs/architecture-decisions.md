# Architecture Decisions Record (ADR)

## ADR-001: Use `src/` Layout and `pyproject.toml` with Editable Install
- **Context:** The pipeline comprises CLI entrypoints (`download`, `run`), reusable library modules (`db`, `ingest`, `rules`, `validate`, `report`), and an automated test suite (`tests/`).
- **Decision:** Package the codebase under `src/dvf_gate/` using `pyproject.toml` (`setuptools.build_meta`) and configure `pythonpath = ["src", "tests"]` for `pytest`. Include `tabulate>=0.9` in base dependencies from Day 1 to support Markdown report generation (`DataFrame.to_markdown()`).
- **Consequences:** Works identically in local virtual environments, Docker containers, and GitHub Actions CI without `sys.path` manipulation.

## ADR-002: Enforce Raw Data Exclusion via `.gitignore`
- **Context:** DVF property transaction records contain geolocated mutation data whose terms of reuse prohibit indexing raw transaction files via external search engines.
- **Decision:** Exclude `data/`, `*.csv.gz`, and `.env` in `.gitignore`, while tracking `tests/fixtures/dvf_synth.csv` (100% synthetic data).
- **Consequences:** Zero risk of leaking raw DVF records or local database credentials to GitHub, while enabling deterministic CI runs on synthetic fixtures.
