## 1. Implementation

- [ ] 1.1 Add a `find_non_compliant_resources` function (new module under `src/`) that filters a list of resource dicts down to those missing `owner` and/or `environment`, treating an absent key or an empty/falsy value as missing, and verify it against the spec's scenarios
- [ ] 1.2 For each returned resource, attach a `missing_tags` list (in `["owner", "environment"]` order, only the missing ones) while preserving the resource's original fields unchanged, and verify with a unit test asserting both the filtered set and the `missing_tags` contents

## 2. Tests

- [ ] 2.1 Add tests covering: all-compliant input (empty result), a mix of compliant/non-compliant resources (order preserved), a resource missing one tag, a resource missing both tags (empty `tags`), and verify `uv run pytest` passes
- [ ] 2.2 Add tests for the falsy-value edge cases (`""` and `None` as a required tag's value both count as missing) and verify `uv run pytest` passes
