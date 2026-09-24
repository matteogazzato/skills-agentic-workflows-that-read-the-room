---
name: update-github-info
description: Update GitHub information content from the latest GitHub Blog posts and changelog.
on:
  schedule: daily
  workflow_dispatch:
permissions:
  contents: read
tools:
  edit: true
  github:
    toolsets: [repos]
  web-fetch:
network:
  allowed:
    - github.blog
    - github.com
safe-outputs:
  create-pull-request:
    title-prefix: "[github-info] "
---

# Update GitHub Information

Keep `site/content/github-info.md` current for Mona to review.

1. Read `notes/mona-notes.md` with the GitHub repository API tools.
2. Fetch https://github.blog/latest/ with `web-fetch`.
3. Fetch https://github.blog/changelog/ with `web-fetch`.
4. Update `site/content/github-info.md` with concise, relevant, and accurate information informed by those sources and Mona's notes. Do not change other files.
5. Use the `create-pull-request` safe output to open a pull request for Mona to review. Summarize the source material and the content changes in the pull request body.
