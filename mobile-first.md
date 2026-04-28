# Mobile-First Notes — thai-mas-web

If this site were built mobile-first, the core philosophy would flip: **start from a single narrow column, then layer on complexity for larger screens** using `min-width` media queries instead of `max-width`.

---

## 1. CSS Architecture
- **Base styles = mobile.** No media query needed for the default layout.
- **Desktop enhancements** wrapped in `@media (min-width: 769px) { ... }` rather than `@media (max-width: 768px)`.
- Cards would be `width: 100%` by default and only shrink to `250px` on desktop.

## 2. Header & Navigation
- **Current problem:** On mobile, the header becomes a tall stack (logo → nav → font switcher) before the user even sees the hero.
- **Mobile-first fix:** Logo on the left, hamburger icon on the right. Nav links hidden behind a toggle menu. The font switcher could tuck into that menu or become a small settings icon. Everything expands horizontally only when space is available.

## 3. Hero Section
- **H1:** Start at `32px` on mobile, scale up to `48px` at `min-width: 769px`.
- **Padding:** Tighter vertical padding by default (e.g., `40px 16px`), then increase to `50px 20px` on desktop.
- **CTA button:** Full-width (`width: 100%`) on mobile so it is easy to tap with a thumb. Shrink to `auto` inline-block on desktop.

## 4. Typography
- **Touch targets:** Nav links, CTA, and footer links would get `min-height: 44px` to meet accessibility standards.
- **Readability:** Serif fonts like Playfair/Merriweather can feel cramped on small screens. Base `font-size` could increase slightly (e.g., `17px` vs. `16px`) with `line-height: 1.6` maintained.
- **Font loading:** Load only the active font (via the switcher) plus a system fallback. On mobile networks, loading two Google Font families is noticeable.

## 5. Cards (Services & Pricing)
- **Mobile:** One card per row, full width, generous internal padding.
- **Desktop:** Flex row with `gap: 30px` kicks in at `min-width: 769px`.
- This is the opposite of the current approach, where cards have a fixed width and are forced to `100%` inside a `max-width` breakpoint.

## 6. Background Image
- Use `background-position: center top` or a cropped focal point on mobile so the important part of the spa image remains visible in a tall narrow viewport.
- Consider a lighter-weight image variant for mobile to save data.

## 7. Footer
- Keep the single-column stack (that part is already mobile-friendly).
- Increase tap target size for the phone and email links.

---

**Bottom line:** The visual result would look almost identical on desktop, but the mobile experience would feel less like a "shrunken desktop site" and more like a native, thumb-first interface.
