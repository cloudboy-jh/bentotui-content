---
layout: ../../layouts/DocsLayout.astro
title: Untouchable Theme Engine
description: Official visual semantics contract for BentoTUI.
publishedAt: 2026-03-15
---

# Untouchable Theme Engine

The Untouchable Theme Engine is the official visual contract for BentoTUI.

## Definition

The theme engine is not a skin layer. It is a contract layer.

- Bentos consume theme semantics for screen-level behavior.
- Rooms consume theme semantics for spacing and split readability.
- Bricks consume theme semantics for component rendering and contrast.

When this contract is stable, app teams can compose quickly without per-screen color glue.

## Scope

- Centralize visual semantics across all bentos, rooms, and bricks.
- Prevent ad-hoc per-screen color glue and style drift.
- Keep rendering predictable across themes and snapshots.

## Architecture Placement

- Shared style helpers moved from `styles/` to `theme/styles/`.
- Theme values are consumed by components as semantic roles, not hard-coded colors.
- Validation scenarios treat theme switching as a first-class input.

## Contract Rules

1. Theme decisions happen globally, not per feature screen.
2. Bricks render using semantic tokens and must preserve contrast guarantees.
3. Rooms do not invent local color systems.
4. Bentos should remain theme-agnostic in behavior logic.

## Validation Expectations

Theme regressions should always be reproducible using the frozen tuple:

`scenario + viewport + theme + focus + snapshot`

`registry/bentos/app-shell` is the proving ground for this behavior and should stay deterministic.

## Current State

- Shared style helpers moved from `styles/` to `theme/styles/`.
- Themes now drive global visual intent instead of local overrides.
- Validation scenarios use theme changes as first-class regression inputs.

## Outcome

Teams can compose faster because layout and component behavior remain stable while theme semantics apply globally.

## Related

- [Architecture Freeze](./architecture)
- [Roadmap](./roadmap)
