# actions

This repository contains a collection of GitHub Actions that are used across different OpenProblems repositories.

## Usage

### Build

This action creates a development or a release build of a Viash project.

To use it, create `.github/workflows/build.yml` with the following content:

```yaml
name: Build

on:
  push:
    branches: [ 'main' ]
  workflow_dispatch:
    inputs:
      version:
        description: |
          The version of the project to build. Example: `1.0.3`.
          
          If not provided, a development build with a version name
          based on the branch name will be built. Otherwise, a release
          build with the provided version will be built.
        required: false

jobs:
  build:
    uses: openproblems-bio/actions/.github/workflows/build.yml@main
    with:
      version: ${{ github.event.inputs.version }}
```

### Test

This action runs the tests of a Viash project.

To use it, create `.github/workflows/test.yml` with the following content:

```yaml
name: Test

on:
  push:
  pull_request:

jobs:
  build:
    uses: openproblems-bio/actions/.github/workflows/test.yml@main
```