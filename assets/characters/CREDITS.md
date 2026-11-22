# Character assets & credits

The humanoid bases, hairstyles and animation clips in this folder come from
the **Quaternius Universal Base Characters** and **Universal Animation
Library** packs. Both are released under **CC0 1.0 Universal (public
domain)**. No attribution is required, but we are happy to credit the author.

- Universal Base Characters (Standard, free) — models by **@Quaternius**
  - https://quaternius.com/packs/universalbasecharacters.html
  - https://quaternius.itch.io/universal-base-characters
- Universal Animation Library (Standard, free) — models by **@Quaternius**
  - https://quaternius.com/packs/universalanimationlibrary.html
  - https://quaternius.itch.io/universal-animation-library

License text: `licenses/UniversalBaseCharacters-License.txt` and
`licenses/UniversalAnimationLibrary-License.txt`.

Modifications: the two runtime hero GLBs were rebuilt with embedded
textures resized (see `tools/prepare-character-textures.ps1` and
`tools/build-character-assets.mjs`), and on 2026-11-18 their embedded PNGs
were converted to WebP (normal maps lossless, everything else quality 90)
via `tools/optimize-assets.mjs` — roughly 52% smaller files with identical
geometry, rigs, materials and clips. `EXT_texture_webp` is used, which
three.js loads natively.

Everything else about the playable cast — the original character identities,
suit shells, colour palettes, visors, emblems, scarves, tails and enemy
designs — is original work created for Little Web Hero. Runtime assets live
locally; the game never fetches a model or animation from a third-party URL.
