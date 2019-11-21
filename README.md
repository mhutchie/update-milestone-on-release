# Update Milestone on Release

This GitHub Action updates and closes milestones automatically when a matching release is published.

## Introduction

When a Pre-Release is Published, any milestone sharing the same `<MAJOR>.<MINOR>.<PATCH>` revision as the releases tag will have its:
* Description updated to `Pre-release: [<RELEASE-TAG-NAME>](<RELEASE-URL>)`.

When a Release is Published, any milestone sharing the same `<MAJOR>.<MINOR>.<PATCH>` revision as the releases tag will have its:
* Description updated to `Release: [<RELEASE-TAG-NAME>](<RELEASE-URL>)`.
* State updated to 'closed'.

## Usage

1. Create the GitHub Workflows Directory `.github/workflows` if it doesn't exist in your repository.
2. Create a new file (e.g. `action.yml`) in the GitHub Workflows Directory, and paste the following code into it:

```
name: 'Update Milestone on Release'

on:
  release:
    types: [published]

jobs:
  update-milestone-on-release:
    runs-on: ubuntu-latest
    steps:
      - name: 'Checkout'
        uses: actions/checkout@v1
      - name: 'Update Milestone on Release'
        uses: mhutchie/update-milestone-on-release@master
        with:
          github-token: ${{ secrets.GITHUB_TOKEN }}
```

3. Commit and push the change to your GitHub repository, and it will start running when any new releases are published.