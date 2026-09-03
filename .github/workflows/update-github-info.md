---
name: update-github-info
description: Keep the site GitHub information page current for Mona review.
on:
  schedule: daily
  workflow_dispatch:
permissions:
  contents: read
  pull-requests: read
engine: copilot
tools:
  edit:
  web-fetch:
  github:
    toolsets: [repos, pull_requests]
network:
  allowed:
    - defaults
    - github.blog
    - github.com
safe-outputs:
  create-pull-request:
    title-prefix: "Update GitHub info: "
    allowed-files:
      - site/content/github-info.md
    reviewers:
      - mona
strict: true
---

# Update GitHub Info

Update `site/content/github-info.md` with current, relevant GitHub information for Mona to review.

## Required Inputs

Read `notes/mona-notes.md` first and use it as the editorial brief for what Mona cares about. Use GitHub repository tools for repository guidance or reference files instead of terminal, CLI, or sandboxed commands.

Use the `web-fetch` tool to fetch these public sources:

- https://github.blog/latest/
- https://github.blog/changelog/

## Instructions

Compare the notes, current `site/content/github-info.md`, and fetched GitHub Blog sources. Update only `site/content/github-info.md` with concise, useful information that is relevant to the site and Mona's review.

Use the configured safe output `create-pull-request` to open a pull request for Mona to review. Do not write directly to `main`.
