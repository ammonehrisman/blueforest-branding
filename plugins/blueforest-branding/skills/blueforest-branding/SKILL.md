---
name: blueforest-branding
description: |
  Apply BlueForest Studios brand identity (logo, colors, fonts, icons) to HTML files and web designs. Use when the user asks to 'brand it', 'apply BlueForest branding', mentions 'BlueForest style', 'BFS brand', 'our brand', or 'company branding' in the context of BlueForest projects.
---

# BlueForest Studios Branding

Apply the BlueForest Studios brand identity to HTML designs. Follow these guidelines precisely.

## When to use this skill

When the user asks to apply BlueForest branding, style a page with "our brand", or mentions BFS/BlueForest styling for any HTML or web design.

## Brand Colors

Define these CSS custom properties in `:root` on every branded design:

```css
:root {
  /* Primary */
  --bfs-blue: #009DDC;           /* Primary brand blue — Pantone 299 */
  --bfs-dark: #231F20;           /* Near-black — body text, dark backgrounds */
  --bfs-white: #FFFFFF;          /* White */
  --bfs-silver: #B6B8BA;         /* Silver grey — Pantone 422, borders, muted text */

  /* Extended palette */
  --bfs-red: #DB3E26;            /* Vibrant Day Lily — accents, CTAs, warnings */
  --bfs-grey: #6C7B81;           /* French Grey — secondary text, subtle elements */
  --bfs-cream: #EFE6D8;          /* Toasted Oatmeal — warm backgrounds, cards */
  --bfs-ice: #D8E0E4;            /* Icy Waterfall — cool backgrounds, alternating rows */
}
```

### Color usage rules

- **Primary actions / links / key headings**: `var(--bfs-blue)`
- **Body text**: `var(--bfs-dark)`
- **Page background**: `var(--bfs-white)` or `var(--bfs-cream)` for warmth or `var(--bfs-ice)` for coolness
- **Secondary / muted text**: `var(--bfs-grey)` or `var(--bfs-silver)`
- **Accent / CTA buttons / alerts**: `var(--bfs-red)`
- **Borders and dividers**: `var(--bfs-silver)` or `var(--bfs-ice)`
- **Card backgrounds**: `var(--bfs-white)` with `var(--bfs-ice)` or `var(--bfs-cream)` for alternating sections

## Typography

The BlueForest brand font is **Diavlo** (geometric sans-serif). For web designs, use **Poppins** from Google Fonts as the closest available match.

Always include in `<head>`:

```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Poppins:ital,wght@0,300;0,400;0,500;0,600;0,700;1,400&display=swap" rel="stylesheet">
```

```css
body {
  font-family: 'Poppins', sans-serif;
  color: var(--bfs-dark);
}
```

### Type scale

- **h1**: 2.5rem, weight 700, color `var(--bfs-dark)` or `var(--bfs-blue)`
- **h2**: 1.75rem, weight 600
- **h3**: 1.25rem, weight 600
- **Body**: 1rem, weight 400, line-height 1.6
- **Small / captions**: 0.875rem, weight 400, color `var(--bfs-grey)`

## Logo

The BlueForest Studios logo SVGs are hosted at permanent public URLs. **Always use these URLs directly** — do NOT attempt base64 encoding or read the file contents.

The SVG files have a tightly cropped `viewBox` (no excess whitespace), so they will render at the correct visual size with simple CSS sizing. Do NOT add extra padding or scaling adjustments.

### Logo URLs

**Blue logo** (for light backgrounds):
```
https://raw.githubusercontent.com/ammonehrisman/blueforest-branding/main/plugins/blueforest-branding/skills/blueforest-branding/assets/BlueForestStudios_logo_blue.svg
```

**White logo** (for dark backgrounds):
```
https://raw.githubusercontent.com/ammonehrisman/blueforest-branding/main/plugins/blueforest-branding/skills/blueforest-branding/assets/BlueForestStudios_logo_white.svg
```

### How to embed the logo

Use the URL directly as the `src` attribute. Do not read the file, do not convert to base64.

```html
<!-- Light backgrounds -->
<img src="https://raw.githubusercontent.com/ammonehrisman/blueforest-branding/main/plugins/blueforest-branding/skills/blueforest-branding/assets/BlueForestStudios_logo_blue.svg" alt="BlueForest Studios" class="bfs-logo">

<!-- Dark backgrounds -->
<img src="https://raw.githubusercontent.com/ammonehrisman/blueforest-branding/main/plugins/blueforest-branding/skills/blueforest-branding/assets/BlueForestStudios_logo_white.svg" alt="BlueForest Studios" class="bfs-logo">
```

### Logo placement rules

- **Header/navbar**: Top-left, max-height 50px
- **Hero sections**: Centered, max-height 80px
- **Footers**: Centered or left-aligned, max-height 40px
- For dark-background sections (like footers), use the **white logo** variant — do NOT use CSS `filter: invert()` or `brightness()` hacks
- Always provide at least 16px clear space around the logo
- Never distort, crop, or recolor the logo

```css
.bfs-logo {
  max-height: 50px;
  height: auto;
  width: auto;
}
```

## Icons — Iconify Integration

**IMPORTANT**: Use the Iconify MCP server tools to enhance every design with professional vector icons. Search for relevant icons and embed them as inline SVG.

### Workflow

1. **Search** with `mcp__iconify__search-icons` using descriptive queries
2. **Get SVG snippet** with `mcp__iconify__get-icon-snippet` using framework `"raw-svg"`
3. **Embed inline** as SVG directly in the HTML

### Icon guidelines

- Use icons generously — navigation, buttons, feature cards, list items, section headers, stats, footers
- Prefer icon sets: `lucide`, `heroicons`, `tabler`, `mdi` for consistency
- Sizes: 16-20px inline, 24px buttons/nav, 32-48px feature cards, 48-64px hero
- Color with `currentColor` or brand color CSS variables
- Pair icons with text labels for accessibility

```css
.bfs-icon {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  flex-shrink: 0;
}
.bfs-icon svg {
  width: 1.25em;
  height: 1.25em;
  fill: currentColor;
}
.bfs-icon-feature svg {
  width: 48px;
  height: 48px;
  color: var(--bfs-blue);
}
```

## Layout Rules

### List items must have large, unique icons

Every bulleted or numbered list must display a unique, contextually relevant icon for each item. The icon should be **as large as the containing block allows** — typically 48–64px inside a styled icon container for primary list items, and 24–36px for nested sub-items. Each icon must be distinct and meaningfully represent the item's content (e.g. `sunrise` for establishing shots, `key` for real estate agents, `scissors` for post-production). Use the Lucide icon set via CDN (`<script src="https://unpkg.com/lucide@latest"></script>`) with `<i data-lucide="icon-name"></i>` syntax, and call `lucide.createIcons()` at the end of the body.

```css
.bfs-icon-list-item {
  display: flex;
  align-items: flex-start;
  gap: 1rem;
}
.bfs-icon-list-item .icon-container {
  width: 56px;
  height: 56px;
  min-width: 56px;
  border-radius: 12px;
  background: linear-gradient(135deg, rgba(0,157,220,0.1), rgba(0,157,220,0.05));
  display: flex;
  align-items: center;
  justify-content: center;
  color: var(--bfs-blue);
}
.bfs-icon-list-item .icon-container svg {
  width: 28px;
  height: 28px;
}
```

### No full-width text — always use split layouts

Text content must **never span the full width of the page**. Every section must use a two-column (or multi-column) layout where one side contains the text/list content and the other side contains a relevant visual element. Visual elements include:

- **CSS data visualizations** — bar charts, progress bars, funnels, meters
- **Stat callouts** — large numbers with labels and icons (e.g. "15 Towns", "2–5 min")
- **Icon compositions** — clusters of large related icons
- **Decorative panels** — key metrics, quote boxes, summary cards
- **Geometric/abstract graphics** — CSS shapes, gradients, patterns

Columns should stack vertically on mobile (below 900px). Use a 60/40 or 50/50 split depending on content density.

```css
.bfs-split {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 3rem;
  align-items: center;
}
.bfs-split-60-40 {
  grid-template-columns: 3fr 2fr;
}
.bfs-split-40-60 {
  grid-template-columns: 2fr 3fr;
}
@media (max-width: 900px) {
  .bfs-split, .bfs-split-60-40, .bfs-split-40-60 {
    grid-template-columns: 1fr;
  }
}
```

## Design Patterns

### Buttons

```css
.bfs-btn {
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  padding: 0.75rem 1.5rem;
  border-radius: 6px;
  font-family: 'Poppins', sans-serif;
  font-weight: 600;
  font-size: 0.9375rem;
  text-decoration: none;
  cursor: pointer;
  transition: all 0.2s ease;
  border: none;
}
.bfs-btn-primary {
  background: var(--bfs-blue);
  color: var(--bfs-white);
}
.bfs-btn-primary:hover {
  background: #0088c2;
  box-shadow: 0 4px 12px rgba(0, 157, 220, 0.3);
}
.bfs-btn-secondary {
  background: transparent;
  color: var(--bfs-blue);
  border: 2px solid var(--bfs-blue);
}
.bfs-btn-secondary:hover {
  background: var(--bfs-blue);
  color: var(--bfs-white);
}
.bfs-btn-accent {
  background: var(--bfs-red);
  color: var(--bfs-white);
}
.bfs-btn-accent:hover {
  background: #c23520;
}
```

### Cards

```css
.bfs-card {
  background: var(--bfs-white);
  border-radius: 12px;
  padding: 1.5rem;
  box-shadow: 0 2px 8px rgba(35, 31, 32, 0.08);
  transition: box-shadow 0.2s ease;
}
.bfs-card:hover {
  box-shadow: 0 8px 24px rgba(35, 31, 32, 0.12);
}
```

### Section backgrounds

Alternate between `var(--bfs-white)`, `var(--bfs-cream)`, and `var(--bfs-ice)` for visual rhythm. Use `var(--bfs-dark)` background with `var(--bfs-white)` text for dramatic/footer sections.

## Workflow

When applying BlueForest branding to a design:

1. **Apply the brand system**: colors as CSS variables, Poppins font, design patterns
2. **Embed the logo**: use the GitHub URL directly (never base64)
3. **Search Iconify** for relevant icons based on the page content — aim for 5-10+ icons minimum
4. **Use design patterns**: buttons, cards, section alternation from this guide
5. **Make it responsive**: viewport meta tag, flexbox/grid, mobile-friendly sizing
6. **Ensure self-contained output**: all CSS in a `<style>` tag, icons as inline SVG, fonts from Google Fonts CDN

## Quality Checklist

Before delivering, verify:
- `:root` CSS variables defined with all brand colors
- Poppins font loaded from Google Fonts
- Logo present in header and/or footer
- Multiple Iconify icons used throughout the design
- Every list item has a unique, large, contextually relevant icon
- No section has text spanning the full page width — all sections use split/multi-column layouts with a visual element alongside the text
- Buttons use `.bfs-btn` pattern with brand colors
- Cards use `.bfs-card` pattern with subtle shadows
- Sections alternate background colors for visual rhythm
- Responsive design (viewport meta, flexbox/grid)
- All colors use CSS custom properties, not hardcoded hex values
