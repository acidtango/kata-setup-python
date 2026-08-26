# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project overview

This is a Python kata sandbox (`kata-setup-python`), managed with [uv](https://docs.astral.sh/uv/). It is intentionally a skeleton: `src/` currently only has `main.py`.

The kata (see [README.md](README.md)): given a list of AWS resource dicts (each with `account`, `type`, `id`, `tags`), detect resources that don't comply with a tagging policy requiring `owner` and `environment` tags, and report which tags are missing.

## Commands

```bash
uv sync                  # install dependencies (dev group: flake8, pytest)
uv run pytest            # run the test suite
uv run pytest tests/test_smoke.py::TestSmoke::test_addition_should_work  # run a single test
uv run python src/main.py  # run the app entrypoint
uv run flake8 .           # lint (config in .flake8; excludes .venv, .git, __pycache__)
```

CI (`.github/workflows/python.yml`) runs, in order: `uv sync`, a strict flake8 pass (`--select=E9,F63,F7,F82`), a full flake8 pass (`--exit-zero --max-complexity=10 --max-line-length=127`), then `uv run pytest`.

Tests use plain classes named `Test*` with `test_*` methods (see `tests/test_smoke.py`), run via pytest.
