---
layout: ../../../layouts/DocsLayout.astro
title: BentoTUI Rooms
description: Import-only layout geometry contracts for BentoTUI v0.5.4.
publishedAt: 2026-03-20
---

# Rooms

`registry/rooms` owns geometry and spatial composition.

## Responsibility

- Allocate width, height, and pane relationships.
- Keep layout deterministic across viewports.
- Stay geometry-only with no theme/color decisions.

## Recommended contracts

- `rooms.AppShell(w, h, content, footer)`
- `rooms.SidebarDetail(w, h, sidebarWidth, sidebar, detail, footer)`
- `rooms.Dashboard(w, h, topLeft, topRight, bottomLeft, bottomRight, footer)`
- `rooms.DiffWorkspace(w, h, railWidth, header, fileRail, diffMain, footer)`

## Core primitives

- Focus family: `Focus`, `Pancake`, `TopbarPancake`
- Rail/split: `Rail`, `RailFooterStack`, `HSplit`, `VSplit`, `HSplitFooter`
- Multi-pane: `HolyGrail`, `TripleCol`, `DrawerRight`, `DrawerChrome`
- Dashboard: `Dashboard2x2`, `Dashboard2x2Footer`
- Overlay/strip: `Modal`, `BigTopStrip`

## Contract

- Rooms are import-only and geometry-only.
- `Frame` era APIs are removed; use current room contracts.
- Compose room output through `surface` in app `View()`.
- Rooms do not import theme, bricks, or raw bubbles (guardrail-enforced).
