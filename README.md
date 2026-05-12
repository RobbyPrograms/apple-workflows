# apple-workflows

Shared GitHub Actions workflows for the apple microservices.

## Reusable workflow

The main reusable workflow lives at `.github/workflows/go-ci.yml`.

It is designed to be called from service repositories with `workflow_call` and runs these jobs in order:

1. `lint`
2. `test`
3. `build`
4. `docker`

## Expected input

Service repositories should pass:

- `service-name`: used to label the Docker image build in CI

## Example usage

```yaml
name: CI

on:
  push:
    branches: [main]
  pull_request:
    branches: [main]

jobs:
  ci:
    uses: RobbyPrograms/apple-workflows/.github/workflows/go-ci.yml@main
    with:
      service-name: svc-inventory
```
