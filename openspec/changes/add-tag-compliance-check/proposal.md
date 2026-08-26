## Why

The kata described in [README.md](../../../README.md) asks for a way to detect AWS resources that don't comply with a tagging policy (every resource must carry `owner` and `environment` tags), but no implementation of that check exists in the repo yet.

## What Changes

- Add a function that filters a list of AWS resource records down to the ones missing a required tag.
- A tag counts as missing when its key is absent from `tags` **or** its value is empty/falsy (e.g. `""`, `None`).
- Each non-compliant resource is returned as the original resource plus a `missing_tags` list naming which of `owner`/`environment` are missing.
- Compliant resources are excluded from the result entirely.

## Capabilities

### New Capabilities
- `tag-compliance`: detect AWS resources that are missing required tags (`owner`, `environment`) and report which ones are missing.

### Modified Capabilities
- (none)

## Impact

- New code under `src/` (currently only `src/main.py`/`src/__init__.py` exist) — either extending `src/main.py` or adding a new module — implementing the compliance check.
- New tests under `tests/`.
- No changes to existing behavior or APIs.
