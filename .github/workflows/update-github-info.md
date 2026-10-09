---
name: update-github-info
description: Keep the GitHub Info page current with practical updates from GitHub Blog, Changelog, and Awesome Copilot workflows.
on:
  schedule: daily
  workflow_dispatch:
permissions:
  contents: read
engine: copilot
tools:
  edit: {}
  web-fetch: {}
network:
  allowed:
    - defaults
    - github.blog
    - github.com
    - awesome-copilot.github.com
safe-outputs:
  noop: {}
  create-pull-request:
    allowed-files:
      - site/content/github-info.md
    title-prefix: "[github-info] "
    reviewers:
      - mona
    draft: true
---

# Update GitHub Info

Read `notes/mona-notes.md` first and follow its editorial guidance. Then web fetch and review these sources:

- https://github.blog/latest/
- https://github.blog/changelog/
- https://awesome-copilot.github.com/workflows/

Update `site/content/github-info.md` only when a recent item provides a useful, accurate, practical update for developers. Keep the summaries short, preserve the existing themes and structure, and identify the source for every addition as GitHub Blog, GitHub Changelog, or Awesome Copilot workflows. Do not infer details that are not supported by the fetched pages.

If there is no material update to make, leave the file unchanged and report a no-op. Otherwise, make the smallest focused edit to `site/content/github-info.md` and use the create-pull-request safe output to open a draft pull request for Mona to review. Include a concise summary and links to the source posts in the pull request description. Do not write directly to the default branch or modify any other files.

