# Ogilvy — Brand Guidelines

> **Derived view.** `charter.json` is the machine-readable source of truth; this file
> presents the same data for humans plus the usage context that doesn't fit in JSON.
> Regenerate whenever a charter promotion changes colours, fonts, logos or grammar.
>
> **Third-party brand.** Ogilvy is not a Stromy-owned identity. Everything here is
> recovered from public evidence (ogilvy.com, 2026-08-25) and reviewed by the operator
> — it is *our working model of the brand*, not an Ogilvy-issued standard. Where an
> official Ogilvy brand book is later supplied, it supersedes this document entirely.

Last updated: 2026-08-26 · Tier 2 (output) · Protection class: available

---

## 1. Foundation

| | |
|---|---|
| **Essence** | We make brands matter. |
| **Positioning** | We design the brand; we turn the brand into an experience; and we communicate the brand's story. |
| **Tagline** | We inspire brands and people to impact the world. |
| **Archetype** | Ruler (primary) · Creator (secondary) |
| **Industry** | Marketing & Advertising |
| **Domain** | ogilvy.com |

**Archetype rationale.** Category-authority posture — the "Network of the Year" award
ticker, 80+ country scale, and the David Ogilvy canon operating as institutional
doctrine — with Creator secondary keeping the work itself the hero. The homepage is a
gallery of exhibits, not a services list.

**Personality axes** (0 = left, 1 = right):

| Axis | Value | |
|---|---|---|
| Formal ←→ Casual | 0.35 | leans formal |
| Traditional ←→ Innovative | 0.55 | balanced |
| Reserved ←→ Expressive | 0.70 | expressive |
| Analytical ←→ Intuitive | 0.50 | balanced |
| Established ←→ Rebellious | 0.35 | leans established |

---

## 2. The five principles

1. **Single-accent discipline.** The Ogilvy Red is the sole non-neutral; pink is a tint
   of it, never a second hue.
2. **Red is a canvas, not only an accent.** Covers and heroes are full-bleed red fields.
3. **Editorial serif/sans pairing carries hierarchy** — restraint over ornament.
4. **The work is exhibited, not decorated.** Content sits in a strict gallery grid.
5. **Depth comes from occlusion and surface change**, never from shadow.

---

## 3. Colour

### Core

| Token | Hex | Role |
|---|---|---|
| `--color-accent` | `#EB3F43` | Ogilvy Red — accent **and** canvas |
| `--color-primary` / `--color-text` | `#231F20` | Ink |
| `--color-background` | `#FFFFFF` | White |
| `--color-background-alt` | `#F4F4F4` | Utility grey band |
| `--color-text-light` | `#6E6B6C` | Muted text |

### Red tints

| Token | Hex | Role |
|---|---|---|
| `--color-red-tint-100` | `#FBCECE` | Section bands, pull-quotes, callouts |
| `--color-red-tint-50` | `#FDE7E7` | Lightest wash step |

These are **tints of the accent**, which is why they don't breach the single-hue rule.
Introducing any other chromatic value does.

### Semantic

| State | Colour | Light fill | Text on light fill |
|---|---|---|---|
| Success | `#3F7A6A` | `#E9F0EE` | `#3F7A6A` |
| Warning | `#B98A3C` | `#F5EBDA` | **`#8F6A2C`** (`--color-warning-ink`) |
| Error | `#6E2A3C` | `#EFE0E4` | `#6E2A3C` |
| Info | `#231F20` (ink) | `#F4F4F4` | `#231F20` |

Warning is the one semantic whose base tone is too light to sit as text on its own
light fill (~3.2:1). Use `--color-warning-ink` for that pairing; the base tone stays
for solid fills carrying white text.

Desaturated, cool-leaning and print-like so they read as native to the palette. The
wine-toned error deliberately sits far from the brand red — the previous bootstrap
default (`#DC3545`) was close enough to be mistaken for it.

---

## 4. Typography

Ogilvy Serif and Ogilvy Sans are **proprietary and restricted**. They are never embedded,
shipped or redistributed. Deliverables name them first and fall back:

| Role | Family | Embed stand-in | Web-safe floor |
|---|---|---|---|
| Heading | Ogilvy Serif | Playfair Display | Georgia |
| Body | Ogilvy Sans | Inter | Arial |
| Wordmark / display | Ogilvy Serif | Playfair Display | Georgia |
| Label / eyebrow | Ogilvy Sans | Inter | Arial |

Every rendered deliverable carries a font-substitution warning in its brand context —
the on-screen face is the stand-in, not the real Ogilvy face. Say so when it matters.

### The eyebrow is a brand signal

The label role is **uppercase Ogilvy Sans, weight 600, 0.16em tracking** — the site's
oversized marquee rows scaled down to eyebrow size.

**Never set an eyebrow in monospace.** Left unspecified, every render surface collapses
onto a shared mono default and the brand loses a real identity signal.

---

## 5. Logo

| File | Use |
|---|---|
| `logos/logo.svg` | Primary — uses `currentColor`; inherits ink on light |
| `logos/logo-white.svg` | Dark and photographic backgrounds |
| `logos/logo-red.svg` | The brand's own on-white lockup (as the live nav renders it) |
| `logos/logo-black.png` / `logo-white.png` | Raster equivalents |
| `logos/favicon*.png`, `favicon.ico`, `apple-touch-icon.png` | Icon set |

**There is no standalone symbol mark.** No clean vector mark exists on the source site,
and one has deliberately not been invented — the favicon set is reused from ogilvy.com.
Where a mark-sized slot is unavoidable, use the cropped Big O motif, not a fabricated icon.

---

## 6. Visual grammar

All nine dimensions are captured and approved. This is what gives a rendered deliverable
its Ogilvy smell.

### 6.1 Backgrounds — "Red Gallery", 4 surfaces

| Surface | Fill | Ink | Used for |
|---|---|---|---|
| `canvas-red` | `#EB3F43` | white | cover, hero, section opener |
| `gallery-white` | `#FFFFFF` | ink | content, data, gallery |
| `band-pink` | `#FBCECE` | ink | section band, pull-quote, callout |
| `closing-ink` | `#231F20` | white | closing, back cover |

Content stays on `gallery-white`. Red is reserved for covers, heroes and section openers
so the field keeps its impact.

### 6.2 Gradients — section wash only

`linear-gradient(180deg, #EB3F43 0%, #FBCECE 55%, #FFFFFF 100%)`

The **only** gradient in the system, and only on section openers and dividers. Every
other surface is a flat field; a gradient on a content page is off-grammar.

### 6.3 Grid — "Gallery modular"

4 columns · 2.2% gutter · 5.5% outer margin · 3:2 default cell.
Spans of 2 or 4 cells are fine. Ragged and masonry layouts are not.

### 6.4 Motifs — "The Big O"

- **`big-o`** (structural) — the wordmark's *own* O glyph, oversized and cropped at the
  surface edge. Frame, crop mask and divider ornament. Extracted from `logos/logo.svg`
  programmatically; never redrawn.
  - One per composition · minimum 40% of the surface's short edge · must bleed off an edge.
  - Below that scale it reads as a letter rather than a device — that's the failure mode.
- **`rule-dot`** (micro) — dot-plus-hairline used as bullet, leader line, table rule and
  chart annotation.

### 6.5 Patterns — "Ghost grid"

The gallery grid drawn as 1px outlines at low opacity: 0.22 on red, 0.14 on pink, 0.10 on
white. Scale it to the full surface width — four columns across. A fine repeat reads as
graph paper, not as the brand's grid.

### 6.6 Iconography — pure ink line

1.5px line icons, square joins, circles only where a radius is needed, no filled shapes.
Ink by default; **red only marks the active or emphasised icon** — in iconography red is
a state, not a style.

### 6.7 Photography — "Campaign vivid"

Full colour, high vibrancy, **no filter, tint or duotone**. The absence of a treatment is
the treatment: the work is shown as the client made it. Presented as white-framed exhibit
cells on red, edge-to-edge on white.

**Do not set text over vivid imagery** — text belongs on the adjacent red, pink, white or
ink surface.

**Sourcing:** generated or licensed only. The campaign photography on ogilvy.com is
**client IP** and is never scraped or reused.

### 6.8 Elevation — flat + hairline

No shadows anywhere. Borders are 1px hairlines (`#E2DEDF` on white,
`rgba(255,255,255,0.35)` on red). Depth is achieved by surface-colour change and by
type/image occlusion. A drop shadow in an Ogilvy deliverable is off-grammar.

### 6.9 Motion — "Ticker energy"

| Primitive | Behaviour |
|---|---|
| `ticker-band` | Uppercase type band translating at constant velocity within its own band. 9s per cycle at 1920px, **linear**, never eases, never stops. |
| `settle-reveal` | Content rises 14px and fades in, then rests. 0.6s, 80ms stagger per section. Surfaces themselves never move. |

**Prohibited:** parallax · surface or background movement · easing on the ticker ·
looping on settle reveals.

**On static surfaces** (PDF, PPTX, deck stills) the ticker renders as a static uppercase
type-as-texture row in the same position. The Big O and the ghost grid carry the static
surfaces; the band carries the moving ones.

**Signature motion:** *An uppercase band glides continuously while everything else settles
over it — the red field itself never moves.*

---

## 7. Anti-patterns

These are hard rules. Each one is enforced in `charter.expression.antiPatterns`.

1. **A second brand hue.** The system is mono plus one red; pink is a tint of that red.
2. **Shipping the proprietary fonts.** Restricted — use the fallback stack.
3. **Drop shadows or any elevation effect.** Depth is occlusion only.
4. **A monospace eyebrow.** The label role is uppercase Ogilvy Sans, wide tracking.
5. **Filtering, duotoning or tinting campaign photography.** Imagery runs vivid and untreated.
6. **Decorative small-scale use of the Big O.** It is structural, minimum 40% of the short edge.
7. **Scraping or reusing ogilvy.com campaign imagery.** It is client IP.

---

## 8. Known gaps

- **No image library.** `images/` and `images/manifest.json` do not exist, so the format
  MCP's variance engine has no theme, cover or hero draws to make — consecutive
  deliverables will look more alike than the grammar allows. Selected theme: **Red Room**
  (objects and still-life staged on Ogilvy-red seamless, ~6 images). A single theme is
  enough to establish the look but thin for variance; consider a second theme before
  volume production.
- **No standalone symbol mark** (see §5) — by design, not omission.
- **No official Ogilvy brand book.** Everything here is evidence-recovered.
- Tier-1-only artefacts absent by design at tier 2: brand book, business cards,
  email signatures.
