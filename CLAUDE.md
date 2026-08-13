# CLAUDE.md — Volara Lab website (volara.dev)

## What this is

The public website for Volara Lab, served at **volara.dev** (see `CNAME`).
Static HTML/CSS, no build step, no framework — deployed straight from this
repo (GitHub Pages style). Renamed from `volara-lab-legal` to
`volara-lab-web` on 13-aug-2026: it started as just the legal-pages hub but
had already grown into the whole public site (landing page + per-app detail
pages + legal pages), so the old name undersold it.

**This repo is web-only — app code and store-submission assets live
elsewhere.** Sibling repos in `../` (the `Volara Lab/` parent directory):
- `../volara-log/`, `../booknest/`, `../fdp-tracker/` — each app's own
  Flutter code. Not touched from here.
- `../branding/` — App Store/Play Store submission assets (screenshots,
  icons, feature graphics) per app. Not served on the web; separate concern
  from this repo's `assets/`.

## Layout

```
index.html          Landing page: Volara Lab logo, tagline, links to each app
style.css            Shared across every page on the site (one file, no
                     per-page inline styles) — CSS custom properties for
                     color/font tokens, Instrument Sans + Inter via Google
                     Fonts, one responsive breakpoint (860px)
assets/              Images used by the site (logos, screenshots), one
                     subfolder per app (assets/volara-log/, ...)
<app>/index.html     That app's own detail/landing page
<app>/privacy-policy.html
<app>/terms-of-service.html
<app>/delete-account.html   (Play Console / App Store data-deletion URL target)
<app>/delete-data.html      (same)
```

Currently `volara-log/` and `booknest/` exist as subfolders. **Only Volara
Log is finished and published** (App Store + Play). Booknest and
`fdp-tracker` are still in design — no real logos or screenshots for them
yet (Booknest's card/page currently uses a 📚 emoji placeholder in place of
a logo asset). Don't invent visual identity for an unpublished app; ask
Daniel or wait for real assets rather than guessing at colors/logo/screenshots.

## Working conventions

Same standing rules as `../volara-log/` — this project follows the same
conventions, not a separate set:

- **Commit locally as work completes; don't push speculatively mid-session.
  Always push when closing out a session** — no need to ask each time.
  If a session ends without an explicit close-out signal, err toward
  pushing anyway rather than leaving local commits stranded.
- **Keep this file current, not aspirational.** When something changes
  (a new app subfolder goes live, real branding lands for Booknest/
  fdp-tracker, the design system in `style.css` changes meaningfully),
  update this file in the same commit as the change — don't let it drift
  and get rewritten from scratch later. If something here turns out to be
  wrong, trust the actual files over this doc and fix the doc, not the
  other way around. Date-stamp notable changes inline (e.g. "13-aug-2026:
  redesigned...") rather than maintaining a separate changelog.
- Daniel does not review code himself — flag structural risks (broken
  links, missing assets referenced by `<img>`/`href`, accessibility gaps)
  proactively, don't wait to be asked.

## State as of 13-aug-2026

Redesigned all three main pages (root `index.html`, `booknest/index.html`,
`volara-log/index.html`) from bare inline-styled HTML to the shared
`style.css` design system described above. Work was local-only as of this
date (not committed) — check `git status` before assuming it matches what's
live at volara.dev.

Known gaps to close before this is publish-ready:
- No favicon declared anywhere on the site.
- Booknest has no real logo asset (`assets/` has no `booknest/` subfolder
  yet) — uses a 📚 emoji placeholder instead.
- `assets/volara-log/android_screenshot1.png`, `screenshot2.png`,
  `screenshot3.png` exist but aren't referenced by any page yet.
