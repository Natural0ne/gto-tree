# GTO Talent · Soul · Trait Builder

A single-page app for building and tracking characters in the Grand Terra Online TTRPG homebrew.

## File structure

```
index.html              The app (HTML, CSS, JS). ~70KB.
data/                   All game content, as JSON. Edit these to add
                        talents, effects, synergies, etc. — no code changes.
  flags.json            Story flags shared by talents and effects.
  talents.json          The Talent Tree.
  soul-categories.json  Mechanical-kind tags for Soul Effects.
  soul-themes.json      Thematic tags that drive synergies.
  soul-effects.json     The Soul Effects library.
  soul-synergies.json   Synergy groups (fire when enough effects share a theme).
  soul-slot-growth.json Auto slot gains at certain levels + flag-gated slots.
  traits.json           The current player Traits.
```

## Hosting

Any static host works. Just upload the whole folder.

### GitHub Pages (recommended)

1. Create a public repo (any name — `gto-tree` works).
2. Upload all files to the root of the repo (`index.html`, `data/`, etc).
3. In the repo's **Settings → Pages**, enable Pages from the main branch.
4. Visit `https://<username>.github.io/<repo>/` in a minute or so.

### Updating content

1. Edit a JSON file in your repo (via GitHub's web editor or locally).
2. Commit and push.
3. Players refresh the page to see the new content.

The app fetches JSON with `cache: 'no-cache'`, so updates appear on the next page load.

## Local testing

```
cd gto-site
python3 -m http.server 8000
```

Then open `http://localhost:8000/` in your browser. You cannot just double-click
`index.html` — browsers block `fetch()` on `file://` URLs. The HTTP server is
required for local testing.

## Player builds

Each player's build (unlocked talents, Soul composition, Trait, level, points)
saves to their browser's localStorage, keyed by this origin. The app has
Export and Import buttons so a player can carry their build between devices
or back up their state.
