# zendev-actions

Reusable GitHub Actions wrappers for zendev tooling.

## Available actions

### `validate-title`

Validate a PR title against zendev emoji commit conventions by invoking
`zendev-validate-title` through `uvx --from git+...`.

```yaml
jobs:
  title:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v6
      - uses: zrr1999/zendev-actions/validate-title@<commit>
        with:
          text: ${{ github.event.pull_request.title }}
```

The action pins `zendev` to a default git commit, but you can override it with
the optional `zendev-ref` input while testing changes on a feature branch.

### `validate-body`

Validate a PR body against required H2 section headings (Summary, Validation, Notes).
Reuses commit convention help from the zendev Python package in error messages.

```yaml
jobs:
  body:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: zrr1999/zendev-actions/validate-body@<commit>
        with:
          body: ${{ github.event.pull_request.body }}
          template: .github/pull_request_template.md  # optional
```
