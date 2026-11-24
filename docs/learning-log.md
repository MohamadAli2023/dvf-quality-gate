# Learning Log — DVF Quality Gate

## Session 1: Environment Setup & Data Profiling

### Key Concepts Covered
1. **Modern Python Packaging (`pyproject.toml` & `src/` Layout):**
   - Using `pyproject.toml` (PEP 621) to centralize package metadata, runtime dependencies, dev dependencies (`pytest`, `ruff`), and tool configuration.
   - Using the `src/dvf_gate/` layout with editable installs (`pip install -e ".[dev]"`) so tests always import the installed package rather than relying on fragile relative path hacks.
2. **Git Hygiene & Data Privacy in Data Engineering (`.gitignore`):**
   - Ignoring `data/` and `*.csv.gz` rather than `*.csv` so raw DVF datasets are never committed to version control (complying with open-data privacy rules), while synthetic test fixtures (`tests/fixtures/dvf_synth.csv`) remain tracked for CI.
