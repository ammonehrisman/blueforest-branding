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

The BlueForest Studios logo is hosted at a permanent public URL. **Always use this URL directly** — do NOT attempt base64 encoding, do NOT use Read/Glob to find local asset files. This avoids wasting tool calls and context window on large image data.

### Logo URL

```
https://raw.githubusercontent.com/ammonehrisman/blueforest-branding/main/plugins/blueforest-branding/skills/blueforest-branding/assets/BlueForestStudios_logo_blue.svg
```

### How to embed the logo

Use the URL directly as the `src` attribute. One line, no tool calls needed.

```html
<img src="https://raw.githubusercontent.com/ammonehrisman/blueforest-branding/main/plugins/blueforest-branding/skills/blueforest-branding/assets/BlueForestStudios_logo_blue.svg" alt="BlueForest Studios" class="bfs-logo">
```

### Logo placement rules

- **Header/navbar**: Top-left, max-height 50px
- **Hero sections**: Centered, max-height 80px
- **Footers**: Centered or left-aligned, max-height 40px
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
2. **Embed the logo**: use the GitHub URL directly (never base64, never Read/Glob for assets)
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
- Buttons use `.bfs-btn` pattern with brand colors
- Cards use `.bfs-card` pattern with subtle shadows
- Sections alternate background colors for visual rhythm
- Responsive design (viewport meta, flexbox/grid)
- All colors use CSS custom properties, not hardcoded hex values
