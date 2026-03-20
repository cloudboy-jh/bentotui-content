---
layout: ../../../layouts/DocsLayout.astro
title: BentoTUI Bentos
description: Runnable template apps for fast BentoTUI remix and delivery.
publishedAt: 2026-03-20
---

# Bentos

`registry/bentos/*` ships runnable template apps for fast remix.

## Responsibility

- Orchestrate app flow and model-owned state.
- Compose rooms and bricks into complete experiences.
- Provide production-oriented starting points instead of toy demos.

## Shipped bentos

- `home-screen` - starter entry screen with theme picker/dialog examples
- `dashboard` - 2x2 metrics/table composition with anchored footer
- `app-shell` - canonical workspace shell with command palette and theme flow
- `detail-view` - list/detail split and session card
- `dashboard-brick-lab` - component showcase and layout test bed
- `vimstatus-demo` - recipe-driven demo for vim-style status line

Primary docs emphasis: `home-screen`, `app-shell`, and `detail-view`.

## v0.5.4 app-shell notes

- Command palette action ordering is deterministic.
- Dialog lifecycle handling is explicit with `dialog.OpenMsg` and `dialog.CloseMsg`.
- Theme propagation updates footer, center deck, and dialog manager consistently.

## Contract

- Bentos consume rooms and bricks; they do not duplicate those responsibilities.
- Bentos avoid raw `bubbles/*` imports (spinner exception, guardrail-enforced).
- Bento `View()` should not call `theme.CurrentTheme()` directly; theme state belongs to the model.
