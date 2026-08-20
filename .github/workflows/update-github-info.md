---
name: update-github-info
description: Keep the GitHub Info website current with practical developer updates.
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
network:
  allowed:
    - github.blog
    - github.com
    - awesome-copilot.github.com
safe-outputs:
  create-pull-request:
    draft: true
    title-prefix: "[github-info] "
---

# Update GitHub Info

Keep the GitHub Info website current with concise, practical updates for developers.

## Sources

1. Read `notes/mona-notes.md` and follow its editorial guidance.
2. Use the `web-fetch` tool to read https://github.blog/latest/.
3. Use the `web-fetch` tool to read https://github.blog/changelog/.
4. Use the `web-fetch` tool to read https://awesome-copilot.github.com/workflows/.

## Update

Review the fetched material for recent changes that help developers learn GitHub faster. Update `site/content/github-info.md` with only useful, accurate items. Keep summaries short and practical, and mention the source whenever an item comes from the GitHub Blog or GitHub Changelog. Preserve the existing structure and style of the content file, and do not make unrelated changes.

When an update is warranted, use the `edit` tool to modify the file, then request exactly one `create-pull-request` safe output with a concise title and body describing the changes and source links. The pull request must propose the changes for Mona to review; do not write directly to the default branch. If no worthwhile update is found, do not modify files and do not request a pull request.