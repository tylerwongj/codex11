# Repository Guidelines

## Project Structure & Module Organization
- The repository is currently bare; scaffold it by adding `src/` for runtime packages, `tests/` mirroring module structure, `docs/` for design notes, and `scripts/` for developer tooling.
- Keep shared configuration in `config/` (environment YAML/TOML) and isolate experimental spikes inside `experiments/<topic>` so production code stays clean.
- Store media or large fixtures in `assets/`; if a file exceeds 10 MB, track it with Git LFS and document the source in a README within that folder.

## Build, Test, and Development Commands
- Standardize on a `Makefile` entry point. Provide at minimum `make install`, `make lint`, `make test`, and `make dev`; describe each target at the top of the file.
- `make install` should create `.venv` via `python -m venv .venv` (or `uv venv`) and install dependencies from `requirements.txt`.
- `make lint` runs `ruff check src tests` plus `ruff format --check`; extend it with language-specific linters if additional stacks emerge.
- `make test` wraps `pytest --maxfail=1 --ff`; reserve slower suites for `make test-all` so quick local loops stay under a minute.
- `make dev` launches the primary entry point (CLI or service). If a watcher exists, surface it here rather than requiring contributors to remember the tool flag.

## Coding Style & Naming Conventions
- Target Python 3.11+ with 4-space indentation, `snake_case` for functions and modules, `PascalCase` for classes, and `SCREAMING_SNAKE_CASE` for constants.
- Require type hints on public interfaces and fail CI on `mypy` violations (`mypy src`).
- Prefer kebab-case for branches (`feature-agent-scheduler`), align Markdown headings sequentially, and wrap prose at ~100 characters.

## Testing Guidelines
- House unit tests in `tests/<module_name>/test_<subject>.py` and mirror package names to simplify imports.
- Maintain ≥85% statement coverage; add regression tests alongside bug fixes and reference ticket IDs in test docstrings.
- Mark slow or integration suites with `@pytest.mark.slow`; exclude them from default runs but execute via `make test-all` before merging.

## Commit & Pull Request Guidelines
- Follow `type(scope): imperative summary` commit titles (e.g., `feat(orchestrator): add agent heartbeat watchdog`) and keep related work in a single commit when reviewers benefit from combined context.
- Rebase before pushing, link pull requests to the relevant issue or note, and paste sanitized output of `make lint` and `make test` in the PR description.
- Request at least one review, attach screenshots or logs when behavior changes, and document configuration or migration updates under `docs/`.

## Example Commit Title
```text
docs(unity-core): clarify execution order checklist
```






## References
- [Git branching strategies](https://www.atlassian.com/git/tutorials/comparing-workflows) - compare Git workflows for teams.
- [GitHub flow](https://docs.github.com/en/get-started/quickstart/github-flow) - lightweight branching model for collaboration.
- [Code review developer guide](https://google.github.io/eng-practices/review/) - Google engineering review practices.
- [Pull request template ideas](https://github.com/embeddedartistry/templates) - sample PR templates for engineering teams.
- [Documentation guide](https://www.divio.com/docs/) - framework for structuring project documentation.
## Key Terms
- **Repository Scaffold**: Standard layout (`src/`, `tests/`, `docs/`, `scripts/`, `config/`, `assets/`) that keeps domain code, tooling, and experiments organized.
- **Makefile Target**: Command alias (`make install`, `make lint`, `make test`, `make dev`) that standardizes local workflows.
- **Type Hint Policy**: Requirement that public Python APIs include annotations and pass `mypy` checks in CI.
- **Test Layout**: Convention of mirroring production modules under `tests/` and marking slow suites with `@pytest.mark.slow`.
- **Conventional Commit**: `type(scope): summary` format that keeps commit history consistent and searchable.
- **Pull Request Gate**: Checklist (green CI, logs, reviewers) that must pass before merging changes to main.
