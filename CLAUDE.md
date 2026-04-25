# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this repo is

Public documentation for the **Adobe Analytics Component Manager for Google Sheets** — a Google Sheets Add-on by [Datacroft](https://datacroft.de/en/component-manager/) that helps Adobe Analytics admins manage components (segments, calculated metrics, eVars, etc.) in bulk.

This is a **GitBook documentation repository** — there is no application code, build system, or test suite. All content is Markdown rendered via GitBook and synced from GitHub.

## Content structure

- `SUMMARY.md` — the GitBook table of contents / navigation tree. Every page that should appear in the published docs must be linked here.
- `README.md` — the landing page of the docs site.
- `getting-started-with-the-component-manager/` — installation and credential setup (OAuth V2 is current; JWT is legacy/deprecated).
- `main-functions/` — one file per feature tab of the add-on.
- `.gitbook/assets/` — all screenshots and images referenced in the docs.

## GitBook syntax conventions

Pages use GitBook-flavored Markdown with these non-standard elements:

```markdown
---
description: Short page description shown as subtitle on GitBook
---
```

```
{% hint style="info" %} ... {% endhint %}       # callout boxes (info/warning/danger)
{% content-ref url="..." %} ... {% endcontent-ref %}  # page card links
{% embed url="..." %} ... {% endembed %}         # embedded media (YouTube etc.)
```

Images are referenced with `<figure>` tags:
```markdown
<figure><img src=".gitbook/assets/image (N).png" alt=""><figcaption></figcaption></figure>
```

## Key product context

- **Authentication**: OAuth V2 Server-to-Server is current. JWT is deprecated — do not suggest or document JWT for new setups.
- **Free vs. Premium**: Most advanced features (bulk edits, Component Usage, Alerts, full Report Getter, etc.) are Premium-only. See `free-vs.-premium-version.md` for the full feature matrix.
- **Base Report Suite ID**: A central config concept — segments/calc metrics/date ranges are account-wide, but dimensions (eVars/props) and metrics (success events) are report-suite-specific. VRS features also depend on this setting.
- **Data privacy**: The add-on only accesses component metadata and account usage logs, never report data. Credentials and user emails are not stored on Datacroft servers.

## Adding or updating pages

1. Write the page in Markdown with a `description` frontmatter block.
2. Add the page to `SUMMARY.md` in the correct position to make it appear in navigation.
3. Place any new screenshots in `.gitbook/assets/` and reference them with the `<figure>` pattern above.
