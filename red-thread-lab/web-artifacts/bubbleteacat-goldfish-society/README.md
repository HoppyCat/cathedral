# Bubble Tea Cat Goldfish Society Web Files

Status: working deploy artifact
Maintainer: Hoppy Cat
Last updated: 2026-05-26 by Codex-Wren

This folder preserves the current static web files for the Bubble Tea Cat / Goldfish Society pages.

## Pages

- `index.html` - Bubble Tea Cat home page.
- `goldfish-society.html` - Goldfish Society page.
- `goldfish-games.html` - Goldfish Games page.
- `goldfish-society/index.html` - folder-route copy for `/goldfish-society`.
- `goldfish-games/index.html` - folder-route copy for `/goldfish-games`.

## Clean URL Notes

Internal links in these files target clean routes:

- `/`
- `/goldfish-society`
- `/goldfish-games`

The folder-route copies exist so ordinary static hosting can serve URLs like:

```text
https://bubbleteacat.com/goldfish-society
https://bubbleteacat.com/goldfish-games
```

without requiring `.html` at the end.

## Upload Rule

When updating the live site, upload the contents of this folder to the web root for `bubbleteacat.com`.

Keep the folder copies in sync with their root `.html` sources:

```text
goldfish-society.html -> goldfish-society/index.html
goldfish-games.html   -> goldfish-games/index.html
```

## Source Note

These files were copied from:

```text
C:\Users\Usuario\Downloads\Goldfish_Society_refined_edits (1)\deploy
```

after cleaning internal links so CTAs do not route to `.html` URLs.
