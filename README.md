# Before the Bell

A class prep tracker. You enter your courses, your deadlines, and the reading or
problem sets you owe before each session; the page lays them out on a day-by-day
spine and separates *prep* (be ready for class) from *due* (submit it).

Prep items break into their own checklist — reading, video, problem set — each
with its own checkbox, so the item only counts as done when all of it is.

## Running it

It's a single static HTML file with no build step and no dependencies. Open
`index.html` directly, or serve the folder:

```bash
python3 -m http.server 4321
```

## Deploying

Any static host serves it as-is. For GitHub Pages: push this folder to a repo,
then Settings → Pages → Source: *Deploy from a branch*, branch `main`, folder
`/ (root)`.

## Where the data lives

In each visitor's own browser (`localStorage`) — nothing is uploaded and nothing
is shared between people. Clearing site data wipes it, and it doesn't sync across
devices; the **Backup** button copies the data out as text and pastes it back in
elsewhere.

## PWA

`manifest.webmanifest` and `sw.js` make it installable to a phone home screen and
usable offline. The service worker only registers over HTTPS, so it's inactive on
`localhost` — it activates once deployed.

The service worker is network-first, so a redeploy reaches visitors on their next
online load. Bump `CACHE` in `sw.js` if you ever need to force-evict old files.

## Editing

`index.html` is generated — the page markup, styles and script all live in it
directly, so edit it in place. There is no source/build split to keep in sync.
