---
layout: ../../layouts/DocsLayout.astro
title: Rendering and Coloring Rules
description: Surface composition and explicit background ownership rules.
publishedAt: 2026-03-20
---

# Rendering and Coloring Rules

These rules keep BentoTUI rendering predictable across themes and layouts.

## Core rendering rule

Every row drawn to surface-backed layouts should have explicit background ownership, via `styles.Row(...)` or equivalent width + background rendering, to avoid bleed and gaps.

## Room and surface usage

- Rooms are geometry-only and return layout structure.
- Compose room output through `surface` in app `View()`.
- Avoid mixing geometry concerns with local color logic.

## Theme and token usage

- Theme is interface-driven and model-owned.
- Use semantic tokens; avoid local hard-coded palette overrides.
- Include diff and syntax token roles where full theme contracts are documented.

## Reliability guardrails

- Rooms do not import theme, bricks, or raw bubbles.
- Bricks do not import other bricks.
- Bentos/recipes/starter/scaffold avoid raw `bubbles/*` imports (spinner exception).
- Bento `View()` methods do not call `theme.CurrentTheme()` directly.

## Related

- [Theme Engine](./theme-engine)
- [Rooms API](./architecture/rooms)
- [Architecture Contract](./architecture)
