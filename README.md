# Little Web Hero — playable build

This repository is the **public, prebuilt mirror** of
[`Nomoshkar/little-web-hero`](https://github.com/Nomoshkar/little-web-hero).
It contains only the Vite production output (`index.html`, hashed `assets/`,
`icons/`, `manifest.webmanifest`) and is served by GitHub Pages:

**https://nomoshkar.github.io/little-web-hero-web/**

## Do not edit this repository by hand

There is no source here on purpose. Every file is regenerated from the source
repo's `dist/` folder:

```bash
# in the source repo (little-web-hero)
npm run publish:web
```

That builds the game, replaces the files in this repo, writes `.nojekyll` and
commits/pushes. Any manual change outside the preserved files below will be
deleted by the next publish.

Preserved across publishes: `.git/`, `.gitattributes`, `.gitignore`,
`.nojekyll`, `README.md`, `LICENSE`, `CNAME`, `.github/`.

## How updates flow

1. Change the game in `little-web-hero`.
2. Verify there: `npm test`, `npm run lint`, `npm run build`,
   `npm run check:mobile`, and `npm run validate` for gameplay changes.
3. `npm run publish:web` (or let the source repo's *Publish playable build*
   GitHub Action do it when `WEB_REPO_TOKEN` is configured).
4. GitHub Pages redeploys this branch. Check the commit starts with
   `Build <source-sha>` and matches `git rev-parse --short HEAD` in the source
   repo.

The source repo's [`.agent/deployment.md`](https://github.com/Nomoshkar/little-web-hero/blob/main/.agent/deployment.md)
is the full runbook: Pages settings, the optional Actions mirror, what ships,
and the mobile/touch contract.

## GitHub Pages settings

- Source: **Deploy from a branch**
- Branch: **`main`**
- Folder: **`/ (root)`**
- No custom build command is needed; `.nojekyll` disables Jekyll processing.

## Playing on a phone

Open the URL above and use the on-screen steering ball, **SWING** and
**BOOST** buttons; tap the glowing interaction pill at doors. On first launch
a phone/tablet starts on the **Phone** performance preset, and Settings →
Display → Touch controls offers Auto / On / Off. Adding the page to your home
screen uses the bundled manifest and icons.

The first load is roughly 30 MB (city textures + character models). Hashed
filenames keep later visits cheap; a new deploy only downloads the changed
chunks.
