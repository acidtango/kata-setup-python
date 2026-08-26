## Purpose

Detects AWS resources that fail a tagging policy requiring `owner` and `environment` tags, reporting exactly which required tags are missing on each one.

## ADDED Requirements

### Requirement: Filter resources to non-compliant ones
The system SHALL accept a list of AWS resource records and return only the resources that are missing at least one required tag (`owner`, `environment`). Compliant resources SHALL NOT appear in the result.

#### Scenario: All resources compliant
- **WHEN** every resource in the input list has both `owner` and `environment` tags with non-empty values
- **THEN** the result is an empty list

#### Scenario: Mix of compliant and non-compliant resources
- **WHEN** the input list contains both resources that have both required tags and resources missing at least one
- **THEN** the result contains only the non-compliant resources, in their original relative order

### Requirement: Report which required tags are missing
For each non-compliant resource, the system SHALL indicate which of the required tags (`owner`, `environment`) are missing, alongside the resource's original data.

#### Scenario: Resource missing one required tag
- **WHEN** a resource's `tags` has `environment` but no `owner` key
- **THEN** it is included in the result with `missing_tags` equal to `["owner"]`, and its original fields (`account`, `type`, `id`, `tags`) are preserved unchanged

#### Scenario: Resource missing all required tags
- **WHEN** a resource has an empty `tags` mapping
- **THEN** it is included in the result with `missing_tags` equal to `["owner", "environment"]`

### Requirement: Treat empty tag values as missing
A required tag SHALL be treated as missing when its key is absent from `tags` or when its value is empty (falsy), such as `""` or `None`.

#### Scenario: Required tag present but empty
- **WHEN** a resource has `owner` set to `""` and a non-empty `environment`
- **THEN** it is included in the result with `missing_tags` equal to `["owner"]`

#### Scenario: Required tag present but None
- **WHEN** a resource has `owner` set to `None` and a non-empty `environment`
- **THEN** it is included in the result with `missing_tags` equal to `["owner"]`
