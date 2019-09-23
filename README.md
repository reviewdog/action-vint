# GitHub Action: Run vint with reviewdog

[![Docker Image CI](https://github.com/reviewdog/action-vint/workflows/Docker%20Image%20CI/badge.svg)](https://github.com/reviewdog/action-vint/actions)
[![Release](https://img.shields.io/github/release/reviewdog/action-vint.svg?maxAge=43200)](https://github.com/reviewdog/action-vint/releases)

This action runs [vint](https://github.com/Kuniwak/vint) with
[reviewdog](https://github.com/reviewdog/reviewdog) on pull requests to improve
code review experience.

## Inputs

### `github_token`

**Required**. Must be in form of `github_token: ${{ secrets.github_token }}`'.

### `level`

Optional. Report level for reviewdog [info,warning,error].
It's same as `-level` flag of reviewdog.

## Example usage

### [.github/workflows/reviewdog.yml](.github/workflows/reviewdog.yml)

```yml
name: reviewdog
on: [pull_request]
jobs:
  vint:
    name: runner / vint
    runs-on: ubuntu-latest
    steps:
      - name: Check out code.
        uses: actions/checkout@v1
      - name: vint
        uses: reviewdog/action-vint@v1
        with:
          github_token: ${{ secrets.github_token }}
```
