# Design Guidelines — thai-mas-web

Master reference for the current and future design of the Thajské masáže Třeboň website.

---

## 1. Design Philosophy

- **Thai luxury, local warmth.** The palette evokes traditional Thai elegance (burgundy and gold) on a warm cream base.
- **Restraint with gold.** Gold is used for CTAs, accents, and highlights — never as a dominant background.
- **Readability first.** Dark text on light backgrounds; light text only on the dark footer.
- **Centered, calm geometry.** Symmetrical layouts, rounded cards, generous whitespace.

---

## 2. Color Palette

| Role | Hex | Usage |
|---|---|---|
| Page background | `#F9F4F0` | Body, header, hero gradient overlay |
| Primary / headings | `#81053D` | H1–H3, card titles, price emphasis, footer bg |
| Accent | `#D4AF37` | CTA bg, borders, hover highlights, footer headings |
| Body text | `#2D2D2D` | Paragraphs, nav links, card descriptions |
| Secondary text | `#4A4A4A` | Subtitles, captions, muted descriptions |
| Light text | `#F9F4F0` | Text on burgundy backgrounds (footer) |
| CTA text | `#fff` | White text on gold CTA button |

---

## 3. Typography

### Primary font
- **Playfair Display** (serif) — used for *all* text in the `_jana` variant.
- **Merriweather** (serif) — used for *all* text in the `_jana2` variant.
- The only difference between `_jana` and `_jana2` is the typeface; weights, sizes, and spacing are identical.

### Weights
- Headings (`h1, h2, h3`): **700**
- CTA button: **700**
- Body / nav / card text: **400**
- Footer hours / price emphasis: **600**

### Scale
| Element | Size | Notes |
|---|---|---|
| H1 (hero) | 48px | Main page |
| H1 (page) | 42px | Pricing page hero |
| H2 (footer) | 20px | |
| H3 (card / table) | 20px | |
| Nav links | 15px | Normal case, no uppercase |
| Subtitle | 20px | Playfair/Merriweather, gold color |
| Body | 16px | Hero intro |
| Card body | 15px | |
| Footer body | 14px | |

---

## 4. Layout & Geometry

### Header
- `padding: 12px 50px`
- Flexbox: `justify-content: space-between; align-items: center`
- Bottom border: `1px solid #D4AF37`
- Background: `#F9F4F0`
- **Logo:** Garuda icon (`garuda.png`), height `45px`, left-aligned, links to home
- **Nav:** normal case, 15px, `margin-left: 20px`

### Hero
- `text-align: center`
- `padding: 50px 20px 40px`
- Background image with cream gradient overlay:
  ```css
  background: linear-gradient(rgba(249, 244, 240, 0.68), rgba(249, 244, 240, 0.68)), url('bg_jana.jpg');
  background-size: cover;
  background-position: center;
  ```
- Vertical rhythm inside hero:
  - H1 → `margin-bottom: 8px`
  - Subtitle → `margin-bottom: 18px`
  - Body paragraph → `margin-bottom: 18px` (implicit via next element spacing)
  - CTA → `margin-top: 18px`

### CTA Button
- `padding: 14px 36px`
- Background: `#D4AF37`
- Text: `#fff` (white)
- Border-radius: `50px` (pill shape)
- Box-shadow: `0 4px 15px rgba(212, 175, 55, 0.3)`
- Hover: background `#81053D`, text `#F9F4F0`, `transform: translateY(-2px)`

### Service / Pricing Cards
- Background: `white`
- Border: `1px solid #eee`
- Border-radius: `15px`
- Padding: `30px`
- Width: `250px` (services) / `280px` (pricing)
- Text-align: `center`
- Box-shadow: `0 5px 15px rgba(0,0,0,0.05)`
- Layout: flex row, `justify-content: center`, `flex-wrap: wrap`, `gap: 30px`

### Pricing Cards (specific)
- Same card geometry as services
- Title: burgundy, 20px, 700
- Price rows: flex `space-between`, `padding: 10px 0`, border-bottom `1px solid #eee`
- Price value: `#81053D`, 600 weight

### Footer
- Background: `#81053D`
- Text: `#F9F4F0`
- Padding: `40px 20px`
- Text-align: `center`
- Single column, centered
- Hours line: `#D4AF37`, 16px, 600 weight
- Phone and email are clickable: `tel:+420732468022` and `mailto:penzionutrebonskemadony@gmail.com`

---

## 5. Assets

| File | Role | Source |
|---|---|---|
| `garuda.png` | Header logo | Original website |
| `bg_jana.jpg` | Hero background | V1 mockup (Unsplash spa photo) |
| `bg.jpg` | Hero background | Original website (gold botanical) — **pre-fork only** |

---

## 6. Site Structure

### Homepage (`index_jana.html` / `index_jana2.html`)
1. Header (icon + nav)
2. Hero (H1 + subtitle + body paragraph + CTA)
3. Services (5 cards)
4. Footer

### Pricing Page (`cenik_jana.html` / `cenik_jana2.html`)
1. Header (icon + nav)
2. Hero (H1 "Ceník" + subtitle)
3. Pricing (5 cards)
4. Footer

### Navigation
- Úvodní stránka → `index_*.html`
- Ceník → `cenik_*.html`

---

## 7. Version History

### Pre-fork (`index.html` / `cenik.html`)
- **Hero:** Left-aligned text, no centering. Background: `bg.jpg` (gold botanical banner from original site) with no gradient overlay.
- **CTA:** Gold background with burgundy text, `border-radius: 4px` (square corners).
- **Services:** Grid layout (`auto-fit, minmax(280px, 1fr)`), cards with `border-top: 2px solid #D4AF37` instead of white rounded cards.
- **Footer:** Two-column flex layout (`space-between`), larger padding (`60px 10%`).
- **Header:** No gold bottom border.
- **Fonts:** Playfair Display (headings) + Roboto Condensed (body).
- **Intro paragraph:** Separate section below hero, not inside it.

### Current fork — `_jana`
- Centered hero with cream gradient over `bg_jana.jpg`.
- Pill-shaped CTA (50px radius).
- White rounded cards with shadow, flex-centered.
- Single-column centered footer.
- Gold header border.
- All text in Playfair Display (no sans serif).
- Intro paragraph moved inside hero; CTA placed below paragraph.
- Smaller header (`12px` padding, `45px` icon).
- No uppercase, no italic anywhere.

### Alt variant — `_jana2`
- Identical to `_jana` in every respect **except** the typeface:
  - **Merriweather** replaces Playfair Display for all text.

---

## 8. Temporary Components

### Font switcher (`_jana` and `_jana2`)
- Small `<select>` dropdown placed in the header, to the right of nav links.
- Options: Playfair Display, Merriweather, Georgia.
- Uses CSS custom property `--font-main` and JavaScript `localStorage` for persistence.
- In `_jana`: gold border, cream background, burgundy text.
- In `_jana2`: translucent white border/background, white text (adapted for the burgundy header overlay).
- **Note:** Temporary tool for comparison; will be removed later.

### Burgundy header & footer overlay (`_jana2` experiment)
- **Header:** `position: absolute` over the hero, with `background-color: rgba(129, 5, 61, 0.75)`, padding `20px 50px`.
- **Footer:** same background image with burgundy overlay `rgba(129, 5, 61, 0.85)`, padding `60px 20px`.
- **Hero gradient:** lighter at the top (`0.3` opacity) transitioning to normal `0.68` at `30%`, so the image remains visible under the tinted header bar.
- **Text color:** all header and footer text is gold `#D4AF37`. Nav hover is white `#fff`.
- **Garuda icon:** gold tint via `filter: invert(1) sepia(1) saturate(8) brightness(0.85)`.
- **CTA:** soft rectangle (`border-radius: 8px`) instead of pill.
- Mobile requires extra hero top padding (`150px`) to clear the stacked header.

## 9. Rules for Future Changes

- Do not introduce new colors without documenting them here.
- Do not introduce uppercase or italic styling.
- Keep all internal links consistent with the file suffix (`_jana` links to `_jana`, `_jana2` links to `_jana2`).
- Any new page must reuse the header, footer, and card components exactly.
- Document every design iteration in `development log.md`.
- Update `design-guidelines.md` after every design change.
