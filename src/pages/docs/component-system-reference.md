---
layout: ../../layouts/DocsLayout.astro
title: BentoTUI Component System Reference
description: Contract-first component behaviors, naming conventions, and shared rendering primitives.
---

# BentoTUI Component System Reference

Status: Current

## Purpose

The component system defines a strict runtime contract so pages, dialogs, cards, and shared primitives all render consistently under size changes, key events, and focus transitions.

Components are organized into the architecture layers defined in [Layer Architecture](./layer-architecture):

- **Containers** (`ui/containers/`): panel, bar, dialog — manage borders and layout
- **Widgets** (`ui/widgets/`): card, input, list, table, text — render content only
- **Primitives** (`ui/primitives/`): row, frame, surface — low-level render helpers

## Core Contract

Every interactive component follows a predictable contract:

- `SetSize(width, height)` is required before rendering.
- `GetSize()` returns the active bounded size.
- rendering is bounded to assigned rows/columns.
- key routing is deterministic and owned by the active focus target.

This keeps layout ownership explicit and prevents ad hoc component behavior.

## Naming Direction

Card-first naming is the active convention across the UI stack:

- `Card`
- `Cards`
- `LeftCard`
- `RightCard`

Shared primitive verbs use the `Render*` form:

- `RenderRow`
- `RenderFrame`
- `RenderInputRow`

## Layout and Layering

The visual stack remains deterministic and stable for runtime composition:

- `body -> footer -> scrim -> dialog`

Components should preserve this layering order when opening overlays, handling dialog transitions, or repainting bounded regions.

## Layer Organization

### Containers (`ui/containers/`)

Complex UI components that manage borders, layout, and child positioning:

- **panel** — Bordered box holding widget content
- **bar** — Header/footer with card system
- **dialog** — Modal overlays

All containers implement `tea.Model` + `SetSize`/`GetSize` for bounded rendering.

### Widgets (`ui/widgets/`)

Simple content components with no border or layout management:

- **card** — Content card for use inside panels
- **input** — Input field widget
- **list** — List widget
- **table** — Table widget
- **text** — Text content widget

Widgets are used inside containers and implement `SetSize` for content fitting.

### Primitives (`ui/primitives/`)

Low-level rendering utilities used by containers (not directly by apps):

- **row** — `RenderRow` for consistent row rendering
- **frame** — `RenderFrame` for bordered frames
- **surface** — Background fills and surfaces

Near-term primitive targets:

1. modal frame
2. input surface
3. list row
4. footer card

## Validation Expectations

Framework changes to components and primitives should continue to validate with:

- `go test ./...`
- `go vet ./...`

## Related Docs

- [Layer Architecture](./layer-architecture)
- [BentoTUI Main Spec](./bentotui-main-spec)
- [Rendering System Design](./rendering-system-design)
- [Framework Progress Update](./next-steps)
- [Framework Roadmap](./framework-roadmap)
