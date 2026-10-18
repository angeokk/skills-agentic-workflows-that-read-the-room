---
name: update-github-info
description: Keep Mona's GitHub Info content current with GitHub Blog, Changelog, and Awesome Copilot workflows.
on:
  schedule: daily
  workflow_dispatch:
permissions:
  contents: read
engine:
  id: copilot
  copilot-sdk: true
tools:
  edit:
  web-fetch:
network:
  allowed:
    - defaults
    - github.blog
    - github.com
    - awesome-copilot.github.com
safe-outputs:
  create-pull-request:
---

# Update GitHub Info for Mona

Keep the website content fresh using official GitHub sources and Awesome Copilot workflows, and submit all proposed changes for Mona to review in a pull request.

## Research

1. Read `notes/mona-notes.md` and follow its editorial guidance.
2. Use the `web-fetch` tool to fetch and review:
   - https://github.blog/latest/
   - https://github.blog/changelog/
    - https://awesome-copilot.github.com/workflows/
3. Select recent, useful updates and workflow recommendations that help developers learn or use GitHub. Verify titles, summaries, and source URLs against the fetched pages. Include dates for Blog and Changelog items only when the source provides them; do not invent details or dates.

## Update

Edit only `site/content/github-info.md`. Preserve its existing purpose and Markdown organization, including the editorial angle and homepage themes. Add or refresh concise entries for the most useful recent Blog and Changelog items, with a clear title, practical summary, publication date, and direct source link for each. Also add a small selection of useful Awesome Copilot workflows with their title, practical summary, and direct source link. Attribute each item to GitHub Blog, GitHub Changelog, or Awesome Copilot, and remove stale or duplicate updates where appropriate.

Keep the content compatible with the site's Markdown-driven homepage: use `##` section headings and `###` headings for individual updates, with summaries and source details beneath each update. Do not modify application code, styling, workflow files, or any other repository files.

## Review and publish

Review the final diff to confirm that it changes only `site/content/github-info.md`, every update is supported by an official source, and the notes' guidance is followed. If there is a meaningful content change, use the `create-pull-request` safe output to open a pull request for Mona to review. Include a concise title and explain the selected updates and sources in the pull request description. Never push changes directly to `main` or use any other write mechanism. If there is nothing worth changing, do not open an empty pull request.