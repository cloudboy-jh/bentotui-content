---
layout: ../../layouts/DocsLayout.astro
title: BentoTUI Framework Progress Update
description: Active framework baseline, architecture direction, current gaps, and next execution priorities.
---

# BentoTUI Framework Progress Update

Date: 2026-03-02  
Status: Active (early production)

## Current State

BentoTUI has moved from a rough harness into a structured framework baseline with a clear five-layer architecture:

- **core**: `shell`, `router`, `layout`, `focus`, `theme`, `msgs` — runtime orchestration
- **ui/containers**: `panel`, `bar`, `dialog` — complex UI with borders/layout
- **ui/widgets**: `card`, `input`, `list`, `table`, `text` — simple content components
- **ui/primitives**: `row`, `frame`, `surface` — low-level rendering utilities
- **ui/styles**: semantic style mapping from theme tokens

This separation is now documented and enforced through:

- [Layer Architecture](./layer-architecture)
- [Component System Reference](./component-system-reference)
- [Framework Roadmap](./framework-roadmap)

## Shipped Progress

- **New:** Layer architecture documented with five clear layers: core, containers, widgets, primitives, and styles.
- Footer-first shell API is in place (`WithFooterBar`, `WithFooter`).
- Dialog system is stabilized for routing and bounds behavior.
- Theme picker flow is functional and deterministic.
- Theme set is locked to:
  - `catppuccin-mocha` (default)
  - `dracula`
  - `osaka-jade`
- Theme persistence and reload behavior are active.
- Test harness command flow is now command-string based:
  - type `/pr`, `/issue`, `/branch` in input, run on Enter
  - legacy aliases (`/dialog`, `/theme`, `/page`) still resolve
  - `/` no longer auto-opens a modal
- Harness footer cards are command-first (`/pr`, `/issue`, `/branch`) and no longer tied to hotkeys.
- UI naming is now card-first across the stack (`Card`, `Cards`, `LeftCard`, `RightCard`).
- Shared primitive verbs are standardized as `Render*` (`RenderRow`, `RenderFrame`, `RenderInputRow`).
- README and changelog discipline are in place (`CHANGELOG.md`, early-production warning tag).

## Architecture Direction (Locked)

- **Five-layer architecture** is now the canonical structure:
  - `core` — runtime orchestration and layout
  - `ui/containers` — complex UI with borders (panel, bar, dialog)
  - `ui/widgets` — simple content components (card, input, list, table, text)
  - `ui/primitives` — low-level rendering utilities (row, frame, surface)
  - `ui/styles` — semantic style mapping
- No ad hoc components.
- Contract-first component behavior (`SetSize`/`GetSize`, bounded rendering, deterministic key routing).
- Visual direction: flat, minimal, solid card surfaces with low chrome.
- Dialog layering remains deterministic:
  - `body -> footer -> scrim -> dialog`

## Current Gaps

- Remaining visual gaps in some component rows still require bounded-row hardening.
- Focus manager needs a clearer API/state contract and stronger test coverage.
- Visual polish is improved but not fully normalized across all components/themes.

## Next Priorities

1. Footer card model and deterministic truncation contract.
2. Focus manager hardening (`SetRing`, `SetIndex`, `FocusBy`, events, wrap/enable behavior).
3. Shared UI primitives (modal frame, input surface, list row, footer card).
4. Broader regression coverage (dialog bounds, footer rendering, key routing).

## Validation Snapshot

Recent framework passes are consistently validated with:

- `go test ./...`
- `go vet ./...`

## Reference Docs

- [Layer Architecture](./layer-architecture) — Top-down five-layer architecture
- [BentoTUI Main Spec](./bentotui-main-spec) — Framework scope and modules
- [Component System Reference](./component-system-reference) — Component contracts and primitives
- [Framework Roadmap](./framework-roadmap) — Execution priorities
- [Rendering System Design](./rendering-system-design) — Renderer ADR
