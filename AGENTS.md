# Repository Guidelines

## Project Structure & Module Organization
Source modules live under `src/`, mirrored by unit tests in `tests/<module>/`. Learning materials and reference notes stay in `docs/`, while reusable tooling belongs in `scripts/`. Use `config/` for shared YAML/TOML settings, `assets/` for large fixtures (track >10 MB files with Git LFS and note the source), and `experiments/<topic>/` for spikes that should not ship. Keep the workspace tidy by archiving deprecated artifacts rather than deleting history.

## Build, Test, and Development Commands
Run `make install` to bootstrap the `.venv` and install dependencies from `requirements.txt`. `make lint` executes `ruff check src tests` followed by `ruff format --check`. `make test` wraps `pytest --maxfail=1 --ff` for fast feedback, while `make test-all` is reserved for slow or marked suites. Use `make dev` to launch the primary entry point or watcher-based workflow for the active module.

## Coding Style & Naming Conventions
Target Python 3.11 with 4-space indentation and `snake_case` for functions, modules, and files. Classes follow `PascalCase`; constants use `SCREAMING_SNAKE_CASE`. Annotate public interfaces with type hints and keep `mypy src` clean. Format code with `ruff format` and favor concise, purposeful comments.

## Testing Guidelines
Place tests in `tests/<module_name>/test_<subject>.py`, mirroring the runtime package path. Maintain ≥85% statement coverage; add regression tests alongside fixes and reference ticket IDs in docstrings. Mark slow or integration tests with `@pytest.mark.slow` so they are excluded from `make test` but included in `make test-all` before merging.

## Commit & Pull Request Guidelines
Follow `type(scope): imperative summary` commit titles (e.g., `feat(orchestrator): add agent heartbeat watchdog`). Rebase before pushing, link PRs to their issues, and attach sanitized output from `make lint` and `make test`. Include screenshots or logs for behavior changes and document configuration updates under `docs/`. Request at least one review and summarize risk, mitigation, and rollout checks in the PR description.

## Security & Configuration Tips
Store secrets outside the repo; load them via environment overrides that reference templates in `config/`. Review dependency updates during `make install`, pin critical packages, and scan for exposed credentials before publishing branches.
