---
layout: ../../layouts/DocsLayout.astro
title: Theme Engine
description: Theme interface, presets, and token contract for BentoTUI v0.5.4.
publishedAt: 2026-03-20
---

# Theme Engine

The theme engine is the visual semantics contract for BentoTUI.

## Model

- `Theme` is an interface, not a struct token bag.
- Bricks support `WithTheme(t)` and runtime `SetTheme(t)` updates.
- If no explicit theme is set, bricks may fall back to `theme.CurrentTheme()`.

## Built-in presets

16 built-in presets:

`catppuccin-mocha` (default), `catppuccin-macchiato`, `catppuccin-frappe`, `dracula`, `tokyo-night`, `tokyo-night-storm`, `nord`, `bento-rose`, `gruvbox-dark`, `monokai-pro`, `kanagawa`, `rose-pine`, `ayu-mirage`, `one-dark`, `material-ocean`, `github-dark`.

## Global manager (optional)

- `theme.CurrentTheme()`
- `theme.CurrentThemeName()`
- `theme.SetTheme(name)`
- `theme.PreviewTheme(name)`
- `theme.AvailableThemes()`
- `theme.RegisterTheme(name, t)`

## Token surface

Theme covers app UI tokens and extended token domains:

- UI semantics for app shell, cards, text, borders, accents, and states
- Diff tokens for added/removed/context backgrounds and intraline highlights
- Syntax tokens such as `SyntaxKeyword`, `SyntaxType`, `SyntaxFunction`, and related roles

## Contract Rules

1. Theme decisions are model-owned and consistent across views.
2. Rooms are geometry-only and do not own color decisions.
3. Bricks consume semantic theme roles, not ad-hoc hard-coded colors.
4. Bento `View()` methods should not call `theme.CurrentTheme()` directly.

## Related style helpers

Use `theme/styles` helpers for reliable row rendering:

- `Row`
- `RowClip`
- `ClipANSI`

## Related

- [Architecture Contract](./architecture)
- [Rendering and Coloring Rules](./rendering-and-coloring-rules)
- [Product Direction and Roadmap](./roadmap)
