---
name: update-github-info
description: Draft website updates for Mona's GitHub Info site from official GitHub sources.
on:
  workflow_dispatch:
  schedule:
    - cron: '17 9 * * *'
engine:
  id: copilot
  model: gpt-4.1
safe-outputs:
  create-pull-request:
    title-prefix: "[mona] "
    draft: true
    fallback-as-issue: false
tools:
  edit:
  web-fetch:
  bash: ["web-fetch:*", "curl:*"]
network:
  allowed:
    - github.com
    - github.blog
    - awesome-copilot.github.com
---

# Update Mona's GitHub Info website

Read `notes/mona-notes.md` before making changes.

Use these sources:
- `notes/mona-notes.md`
- GitHub Blog: https://github.blog/latest/
- GitHub Changelog: https://github.blog/changelog/
- Awesome Copilot workflows: https://awesome-copilot.github.com/workflows/

Fetch each URL above by running `curl -s <url>` as a shell command and
reading its output. Do not look for a separate fetch tool or skill by
name; `curl` is the approved way to read these pages in this sandbox.

Update `site/content/github-info.md` with concise,
practical updates for readers and include source context when content comes
from the GitHub Blog or GitHub Changelog.

Open a pull request for Mona to review.
Use a pull request title that mentions Mona or GitHub Info.
Do not write directly to `main`;
rely on `safe-outputs` with `create-pull-request`.
