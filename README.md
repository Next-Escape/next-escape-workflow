# Github Action

## How to use this reusable github action
Create a new workflow with the following yaml configuration
```yaml
# This is a basic workflow to help you get started with Actions

name: Release

# Controls when the workflow will run
on:
  workflow_dispatch:
    inputs:
      IS_RELEASE:
        type: boolean
        description: Perform a release. Upgrade the version
        required: true
        default: false
      IS_PUBLISH:
        type: boolean
        description: Publish the release
        required: true
        default: false

# A workflow run is made up of one or more jobs that can run sequentially or in parallel
jobs:
  release:
    uses: Next-Escape/next-escape-workflow/.github/workflows/release.yml@main
    with:
      IS_RELEASE: ${{ github.event.inputs.IS_RELEASE == 'true' }}
      IS_PUBLISH: ${{ github.event.inputs.IS_PUBLISH == 'true' }}
      GITHUB_REPO: ${{ github.repository }}
```
