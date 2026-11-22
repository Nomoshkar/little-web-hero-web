# Near-field crowd kit — credits

All character bases are **CC0 1.0 Universal (public domain)** by
[Quaternius](https://quaternius.com), downloaded from
[Poly Pizza](https://poly.pizza). No runtime request leaves the origin.

| File | Source | Licence |
|---|---|---|
| `man.glb` | [Man](https://poly.pizza/m/HMnuH5geEG) by Quaternius | CC0 1.0 |
| `man-hi.glb` | `man.glb` subdivided one level + smoothed | CC0 1.0 |
| `woman-casual.glb` | [Woman Casual](https://poly.pizza/m/jpKRgGDxhk) by Quaternius | CC0 1.0 |
| `woman-casual-hi.glb` | `woman-casual.glb` subdivided one level + smoothed | CC0 1.0 |
| `woman-dress.glb` | [Woman in Dress](https://poly.pizza/m/zMyPlQXBzq) by Quaternius | CC0 1.0 |
| `woman-dress-hi.glb` | `woman-dress.glb` subdivided one level + smoothed | CC0 1.0 |

## Modifications

- The source material colours are baked into a per-face-corner float
  attribute (`_PARTID`: 0 skin, 1 top, 2 bottom, 3 eye white, 4 shoes,
  5 hair, 6 iris, 7 pupil, 8 glint).
- Every mesh uses one neutral `CrowdBody` material; the game replaces it
  with a palette shader so each actor can be tinted independently.
- The source eye spheres are kept as the sclera; small iris, pupil and
  glint spheres are added in the head bone's rest space and weighted to the
  head, so they move with every animation.
- The animation set is trimmed/expanded to `Idle`, `Standing`, `Walk`, `Run`,
  `Sitting`, `Clapping`, `Jump`, `Lay`, `Swim`, `Dance`, `Kneel` and
  `SitGround`. `Sitting` is the upright chair pose, `SitGround` is the low
  ground-sit loop; `Lay`, `Swim`, `Dance` and `Kneel` are lightweight
  authored variants of the source clips (hip pitch / clap / sit bases).
- The mid-LOD meshes are exported as one primitive per base (one draw call
  each). The high-LOD meshes are welded, subdivided one level, smooth-shaded
  and split into palette-part meshes so the slow, close-up shader path can
  use polygon offsets between skin, clothes, hair and eyes.
- Kids are not separate downloads: the runtime reuses these bases at a
  shorter height and scales the `Head` bone up for a child head-to-body
  ratio.

The original licence texts are available at
<https://creativecommons.org/publicdomain/zero/1.0/>.
