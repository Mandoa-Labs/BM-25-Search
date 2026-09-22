# Code scanning

Reference documentation for GraphQL schema types in the Code scanning category.

## CodeQualityParameters - object

Choose which severity levels of code quality results should block pull request
merges. When configured, a code quality analysis must be done on the pull
request before the changes can be merged.

### Fields for `CodeQualityParameters`

* `severity` (CodeQualitySeverity!): The lowest severity level at which code quality reviews need to be resolved before commits can be merged.

## CodeQualityParametersInput - input object

Choose which severity levels of code quality results should block pull request
merges. When configured, a code quality analysis must be done on the pull
request before the changes can be merged.

### Input fields for `CodeQualityParametersInput`

* `severity` (CodeQualitySeverity!): The lowest severity level at which code quality reviews need to be resolved before commits can be merged.

## CodeQualitySeverity - enum

The lowest severity level at which code quality reviews need to be resolved before commits can be merged.

### Values for `CodeQualitySeverity`

* `ALL`: All.
* `ERRORS`: Errors.
* `NOTES`: Notes and higher.
* `WARNINGS`: Warnings and higher.