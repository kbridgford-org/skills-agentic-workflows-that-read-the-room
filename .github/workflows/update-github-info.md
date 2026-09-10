---
name: update-github-info
on:
  schedule:
    - cron: "17 9 * * *"
  workflow_dispatch: {}

permissions:
  contents: read

tools:
  github:
    toolsets:
      - repos
  web-fetch:
  edit:

network:
  allowed:
    - github.blog
    - github.com

safe-outputs:
  create-pull-request:
---

Use GitHub repository API tools—not terminal, CLI, or sandboxed commands—to read `notes/mona-notes.md` and any repository guidance or reference files.

Use web-fetch to read external public guidance from:

- https://github.blog/latest/
- https://github.blog/changelog/

Update `site/content/github-info.md` with relevant current information while preserving its established style and structure. Use the `create-pull-request` safe output to open a pull request for Mona to review. Do not write directly to `main`.
