# Review Git Diff Action

This GitHub Action reviews the Git diff and comments on the Pull Request based on the number of changes found.
This only works on `pull_request` workflow events.

# Usage

## Inputs

|input|description|
|-|-|
|github-token|The GitHub Actions token. Not required.|
|threshold|The maximum number of diff lines.|
|message|The message when diff lines exceeds threshold.|

## Example

```
name: Sample
on:
  pull_request_target:
    types:
      - opened
      - reopened

jobs:
  sample:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
        with:
          fetch-depth: 0

      - uses: KazukiHayase/review-git-diff-action
        with:
          threshold: 100
          message: "⚠️  Git diff exceeds 100, please consider if PR can be split."
```
