# World assets & credits

Traffic vehicles and zoo animals in this folder are repacked from the
**Kenney Car Kit** and **Gobkit Animal Packs**, both released under
**CC0 1.0 Universal (public domain)**. The **Kenney Mini Characters 1**
pack is retained for reference / optional GLB loading; the city crowd now
uses the procedural instanced rig plus the Quaternius near-field kit in
`crowd/`. No attribution is required, but we are happy to credit the authors.

- Car Kit — models by **Kenney** — https://kenney.nl/assets/car-kit
- Mini Characters 1 — models by **Kenney** — https://kenney.nl/assets/mini-characters-1
- Near-field crowd (Man / Woman Casual / Woman in Dress) — models by
  **Quaternius**, via [Poly Pizza](https://poly.pizza) — CC0 1.0; see
  `crowd/CREDITS.md`
- Animal packs (Elephant, Lion, Zebra, Tiger, Seal, Penguin, Flamingo,
  Peacock) — models by **Gobkit** — https://gobkit.com/freebies

License texts: `licenses/KenneyCarKit-License.txt`,
`licenses/KenneyMiniCharacters-License.txt` and
`licenses/GobkitAnimals-License.txt`.

The build script bakes each Kenney pack's colour map into vertex colours,
merges the vehicle bodies, extracts one canonical spinning wheel per model,
and strips the people textures while keeping their skin and animation clips.
The Gobkit animals keep their skinned rig, embedded texture and separate
`idle` / `walk` clips. The near-field crowd kit is local, CC0, and has its
own manifest and CREDITS under `crowd/`. All generated assets are local; the
game never fetches a third-party URL at runtime.

The 8,494-person instanced background crowd, the island, buildings,
landmarks and gameplay props remain procedural work created for Little Web
Hero; the near-field adults are the local Quaternius GLBs described above.

## Beach dressing

The beach towels, parasols, sandcastles, beach balls and two lifeguard towers
are **procedural** geometry baked into the shore's static batches (vertex
colours for the fabric/balls, one merged mesh per material). No new external
asset, texture or service is involved; the only map is the existing canvas
`blanketTexture()`.

## Reef props

`reef/` holds AI-generated hero coral and wreck props (anchor, cannon, ship's
wheel). Each model is a local GLB with one material and WebP-embedded maps,
produced on this machine:

1. reference image: Flux 2 Klein 4B (`tools/gen-asset.mjs image`)
2. image → mesh: Trellis 2 (`tools/workflows/trellis2-prop.api.json`)
3. cleanup: Blender 5.3 (base-centre origin, metres, 1 200 tris,
   512² maps, normal map named `*Normal*` for the lossless WebP pass)
4. compression: `npm run optimize:assets`

No third-party model, texture or service contributes to these files; the
reference prompts and seeds are recorded in `art-source/props/` (gitignored).
The reef's procedural coral is the fallback if `reef/` is missing.

## Street props

`props/` holds the AI-generated street props, produced with the same local
Flux → Trellis → Blender → WebP pipeline: hydrants (71), benches (269),
planters (175), bins (204), bollards (93), mailboxes (31), newspaper boxes
(22), A-frame signs (23) and rooftop AC units (20), plus 6 additional bus
shelters. The hydrants/benches/planters/bins replace their procedural
batches; the procedural glass bus shelters and rooftop clutter remain the
fallback if `props/` is missing.

## Generated surface maps

`../textures/` holds locally generated seamless surface maps: three asphalt
variants (`road-asphalt`, `road-asphalt-b`, `road-asphalt-c`) blended by the
road shader, and `reef-sand` for the reef seabed. They were produced on this
machine with Flux 2 Klein and `tools/build-textures.mjs` (seamless blend +
derived roughness). No third-party texture is used; the road/beach canvas
textures remain the fallback when a WebP is missing.
