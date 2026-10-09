---
name: update-github-info
description: Keep the GitHub information page current for Mona to review.
on:
  schedule:
    - cron: "0 9 * * *"
  workflow_dispatch:
permissions:
  contents: read
  pull-requests: read
tools:
  edit:
  github:
    toolsets: [repos]
  web-fetch:
network:
  allowed:
    - github.blog
    - github.com
    - awesome-copilot.github.com
safe-outputs:
  create-pull-request:
    title-prefix: "[Mona] "
    labels:
      - documentation
---

Read `notes/mona-notes.md` using GitHub repository API tools before making any changes. Read any repository guidance or reference files the same way; do not use terminal, CLI, or sandboxed commands to read them.

Use web-fetch to read https://github.blog/latest/, https://github.blog/changelog/, and https://awesome-copilot.github.com/workflows/. Update `site/content/github-info.md` with relevant, verified information, following the repository guidance and Mona's notes. Propose the change by opening a pull request for Mona to review. Do not write directly to the main branch.
