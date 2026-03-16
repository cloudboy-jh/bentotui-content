---
layout: ../../layouts/DocsLayout.astro
title: Untouchable Theme Engine
description: Official visual semantics contract for BentoTUI.
publishedAt: 2026-03-15
---

# Untouchable Theme Engine

The Untouchable Theme Engine is the official visual contract for BentoTUI.

## Purpose

- Centralize visual semantics across all bentos, rooms, and bricks.
- Prevent ad-hoc per-screen color glue and style drift.
- Keep rendering predictable across themes and snapshots.

## Current State

- Shared style helpers moved from `styles/` to `theme/styles/`.
- Themes now drive global visual intent instead of local overrides.
- Validation scenarios use theme changes as first-class regression inputs.

## Outcome

Teams can compose faster because layout and component behavior remain stable while theme semantics apply globally.
