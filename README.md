# BlueForest Branding — Claude Code Plugin

A Claude Code skill that applies BlueForest Studios brand identity to HTML designs.

## What it does

When triggered, this skill instructs Claude to:
- Apply **BlueForest brand colors** as CSS custom properties
- Load **Poppins** (Google Fonts substitute for Diavlo) as the brand typeface
- Embed the **BlueForest Studios logo** in headers and footers
- Use the **Iconify MCP server** to add professional vector icons throughout designs
- Apply consistent **buttons, cards, and layout patterns** matching brand guidelines

## Installation

### Prerequisites

This skill works best with the **Iconify MCP server** installed:

```bash
npm install -g iconify-mcp
claude mcp add iconify --scope user -- iconify-mcp
```

### Install the plugin

```bash
claude plugins add github:blueforeststudios/blueforest-branding
```

## Usage

### Slash command
```
/blueforest-branding
```

### Natural language triggers
- "Apply BlueForest branding to this page"
- "Brand it with our BlueForest style"
- "Make this match the BFS brand"

## Brand Colors

| Name | Hex | Usage |
|------|-----|-------|
| BlueForest Blue | `#009DDC` | Primary brand color, links, headings |
| Dark | `#231F20` | Body text, dark backgrounds |
| Silver | `#B6B8BA` | Borders, muted text |
| Vibrant Day Lily | `#DB3E26` | Accents, CTAs |
| French Grey | `#6C7B81` | Secondary text |
| Toasted Oatmeal | `#EFE6D8` | Warm backgrounds |
| Icy Waterfall | `#D8E0E4` | Cool backgrounds |
