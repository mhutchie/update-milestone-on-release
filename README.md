# Update Milestone on Release

This GitHub Action updates and closes milestones automatically when a matching release is published.

## Introduction

When a Pre-Release is Published, any milestone sharing the same `<MAJOR>.<MINOR>.<PATCH>` revision as the releases tag will have its:
* Description updated to `Pre-release: [<RELEASE-TAG-NAME>](<RELEASE-URL>)`.

When a Release is Published, any milestone sharing the same `<MAJOR>.<MINOR>.<PATCH>` revision as the releases tag will have its:
* Description updated to `Release: [<RELEASE-TAG-NAME>](<RELEASE-URL>)`.
* State updated to 'closed'.