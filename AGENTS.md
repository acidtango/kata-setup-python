# Repository Agent Guidelines

This repository is a Python kata sandbox for AWS tag compliance checking, managed with `uv`.

## Key Documentation & Links

- [CLAUDE.md](CLAUDE.md) – Commands for setup, testing (`uv run pytest`), linting (`uv run flake8 .`), and CI behavior.
- [README.md](README.md) – AWS resource tag compliance kata prompt and example data.

## Development & Code Conventions

- **Environment & Execution**: Use `uv` for dependency management. Run commands via `uv run` (e.g., `uv run pytest`, `uv run python src/main.py`).
- **Testing**: Use `pytest` runner. Test files belong in [tests/](tests/), using `Test*` classes and `test_*` functions.
- **Code Quality**: Ensure linting passes with `uv run flake8 .`. Follow configuration in [.flake8](.flake8) (max line length 127).
