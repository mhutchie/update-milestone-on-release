# Update Milestone on Release

This GitHub Action updates and closes milestones automatically when a matching release is published.

![Release Example](https://github.com/mhutchie/update-milestone-on-release/raw/master/media/release.png)

![Milestone Example](https://github.com/mhutchie/update-milestone-on-release/raw/master/media/milestone.png)

## Introduction

When a pre-release is published, if the releases tag includes the same `<MAJOR>.<MINOR>.<PATCH>` revision as a revision included within the title of an open milestone, the milestone will have its:
* Description updated to `Pre-release: [<RELEASE-TAG-NAME>](<RELEASE-URL>)`.

When a release is published, if the releases tag includes the same `<MAJOR>.<MINOR>.<PATCH>` revision as a revision included within the title of an open milestone, the milestone will have its:
* Description updated to `Release: [<RELEASE-TAG-NAME>](<RELEASE-URL>)`.
* State updated to 'closed'.

## Examples

When a pre-release with tag `v1.0.0-beta.0` is published, a milestone that exists with the title `v1.0.0` will have its description updated to `Pre-release: [v1.0.0-beta.0](<RELEASE-URL>)`.

When a release with tag `v1.0.0` is published, a milestone that exists with the title `v1.0.0` will have its description updated to `Release: [v1.0.0](<RELEASE-URL>)`, and be closed.

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
      - name: 'Update Milestone on Release'
        uses: mhutchie/update-milestone-on-release@master
        with:
          github-token: ${{ secrets.GITHUB_TOKEN }}
```

3. Commit and push the change to your GitHub repository, and it will start running whenever a new release is published.