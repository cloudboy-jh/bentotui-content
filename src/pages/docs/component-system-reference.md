---
layout: ../../layouts/DocsLayout.astro
title: BentoTUI Component System Reference
description: Contract-first component behaviors, naming conventions, and shared rendering primitives.
---

# BentoTUI Component System Reference

Status: Current

## Purpose

The component system defines a strict runtime contract so pages, dialogs, cards, and shared primitives all render consistently under size changes, key events, and focus transitions.

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

## Shared Primitive Scope

Shared primitives in `ui/primitives` are responsible for consistent building blocks used across component rows, dialog surfaces, and footer cards.

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

- `project-docs/bentotui-main-spec.md`
- `project-docs/layer-architecture.md`
- `project-docs/next-steps.md`
- `project-docs/framework-roadmap.md`
