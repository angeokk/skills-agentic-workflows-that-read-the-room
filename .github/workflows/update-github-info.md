---
name: update-github-info
description: Keep Mona's GitHub Info content current with official GitHub Blog and Changelog updates.
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
safe-outputs:
  create-pull-request:
---

# Update GitHub Info for Mona

Keep the website content fresh using official GitHub sources, and submit all proposed changes for Mona to review in a pull request.

## Research

1. Read `notes/mona-notes.md` and follow its editorial guidance.
2. Use the `web-fetch` tool to fetch and review:
   - https://github.blog/latest/
   - https://github.blog/changelog/
3. Select recent, useful updates that help developers learn or use GitHub. Verify each title, date, summary, and source URL against the fetched official pages. Do not invent details or dates.

## Update

Edit only `site/content/github-info.md`. Preserve its existing purpose and Markdown organization, including the editorial angle and homepage themes. Add or refresh concise entries for the most useful recent Blog and Changelog items, with a clear title, practical summary, publication date, and direct source link for each. Attribute every item to GitHub Blog or GitHub Changelog, and remove stale or duplicate updates where appropriate.

Keep the content compatible with the site's Markdown-driven homepage: use `##` section headings and `###` headings for individual updates, with summaries and source details beneath each update. Do not modify application code, styling, workflow files, or any other repository files.

## Review and publish

Review the final diff to confirm that it changes only `site/content/github-info.md`, every update is supported by an official source, and the notes' guidance is followed. If there is a meaningful content change, use the `create-pull-request` safe output to open a pull request for Mona to review. Include a concise title and explain the selected updates and sources in the pull request description. Never push changes directly to `main` or use any other write mechanism. If there is nothing worth changing, do not open an empty pull request.