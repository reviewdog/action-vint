# GitHub Action: Run vint with reviewdog

[![Docker Image CI](https://github.com/reviewdog/action-vint/workflows/Docker%20Image%20CI/badge.svg)](https://github.com/reviewdog/action-vint/actions)
[![Release](https://img.shields.io/github/release/reviewdog/action-vint.svg?maxAge=43200)](https://github.com/reviewdog/action-vint/releases)

This action runs [vint](https://github.com/Kuniwak/vint) with
[reviewdog](https://github.com/reviewdog/reviewdog) on pull requests to improve
code review experience.

[![github-pr-check example](https://user-images.githubusercontent.com/3797062/65413404-57887a00-de2c-11e9-8f45-0729808b1c29.png)](https://github.com/reviewdog/action-vint/pull/1)
[![github-pr-review example](https://user-images.githubusercontent.com/3797062/65413352-3f185f80-de2c-11e9-956e-569eeaccac5f.png)](https://github.com/reviewdog/action-vint/pull/1)

## Inputs

### `github_token`

**Required**. Must be in form of `github_token: ${{ secrets.github_token }}`'.

### `level`

Optional. Report level for reviewdog [info,warning,error].
It's same as `-level` flag of reviewdog.

### `reporter`

Reporter of reviewdog command [github-pr-check,github-pr-review].
Default is github-pr-check.
github-pr-review can use Markdown and add a link to rule page in reviewdog reports.

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
      - uses: actions/checkout@v1
      - name: vint
        uses: reviewdog/action-vint@v1
        with:
          github_token: ${{ secrets.github_token }}
          reporter: github-pr-review # Change reporter.
```
