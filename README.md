# 日本 AI 生態系 — Japan AI Ecosystem Explorer

> One HTML file. 149 organisations. Zero build step.

An interactive map of every partner on NVIDIA's Japan ecosystem wall (July 2026), sorted into eighteen sectors and rendered as a hanko-sheet — paper ground, vermilion seal, vertical sector labels.

**[→ Live demo](https://your-username.github.io/japan-ai-ecosystem/)**

---

## Why this exists

The original artefact is a wall of ~150 logos on a black background. It looks impressive and tells you nothing. Sorted, the shape of the thing becomes legible:

| | share |
|---|---|
| Industrial, semis & electronics | ~30% |
| AI startups (foundation + applied) | ~20% |
| Academia & national labs | ~18% |
| Everything else | ~32% |

The centre of gravity is **physical AI and sovereign compute** — robotics, factory automation, fab equipment, `Rapidus`, `ABCI`, `G-QuAT` — not consumer software. That's a materially different bet from the US ecosystem, and it's invisible until you sort the wall.

## Features

- **Proportional strip** — band width = sector count. Click to isolate a sector, click again to release.
- **Live search** across all 149 names, with match highlighting.
- **Type filter** — corporate / startup / academic / capital.
- **Silicon flag** — semiconductor-adjacent sectors carry a blue edge.
- **Responsive**, keyboard-navigable, `prefers-reduced-motion` respected.

## Design notes

| Token | Value | Role |
|---|---|---|
| `--washi` | `#EDE9E1` | paper ground |
| `--sumi` | `#171512` | ink |
| `--shu` | `#C4272E` | seal vermilion — active state only |
| `--ai` | `#2B4257` | indigo — silicon flag, focus rings |
| `--kin` | `#A8A093` | hairlines, muted labels |

Type: **Shippori Mincho** (display) / **Zen Kaku Gothic New** (body) / **IBM Plex Mono** (data + labels).

The one indulgence is *tategaki* — the sector labels run vertically, as they would on a printed Japanese index. Everything else stays quiet.

## Run it

```bash
git clone https://github.com/your-username/japan-ai-ecosystem.git
cd japan-ai-ecosystem
open japan-ai-ecosystem.html      # that's it — no deps, no bundler
```

Fonts load from Google Fonts. Offline, it falls back to system faces and still works.

## Embed in Notion

Notion's `/embed` block needs a public URL, not a local file.

**GitHub Pages**
```
Settings → Pages → Source: main / root
→ https://your-username.github.io/japan-ai-ecosystem/japan-ai-ecosystem.html
```
Paste that into `/embed`. Resize the block; the layout is responsive and will sit happily in a column.

**Netlify Drop** — drag the file onto [netlify.com/drop](https://app.netlify.com/drop) for an instant URL, no account required.

## Editing the data

Everything lives in the `SECTORS` array at the top of the `<script>` block:

```js
{ en:"Robotics", ja:"ロボティクス", silicon:false, items:[
    ["Mujin","Startup"],
    ["Telexistence","Startup"],
] }
```

| Field | Notes |
|---|---|
| `en` / `ja` | English rail label and vertical Japanese label |
| `silicon` | `true` adds the blue edge to every chip in the sector |
| `items` | `[name, kind]` where kind ∈ `Corporate` \| `Startup` \| `Academic` \| `Capital` |

Add a sector and the strip, the board, and the counts all update themselves — nothing is hard-coded to eighteen.

## Caveats

- Sector assignment is a judgement call. `Mercari` sits in consumer, `Silicon Studio` in applied AI despite the name, `Medicaroid` in robotics rather than healthcare. Reasonable people would file these differently.
- Transcribed from a logo wall image; a handful of smaller marks were low-resolution. Corrections welcome via PR.
- A snapshot, not a feed. The wall will have moved by the next GTC.

## Licence

MIT for the code. The organisation names are trademarks of their respective owners; this is an unofficial, non-commercial reference.
