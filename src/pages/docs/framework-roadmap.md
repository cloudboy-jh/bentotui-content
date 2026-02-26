---
layout: ../../layouts/DocsLayout.astro
title: BentoTUI Framework Roadmap
description: Execution roadmap focused on contract hardening, primitive reuse, and regression coverage.
---

# BentoTUI Framework Roadmap

Status: Active

## Direction

BentoTUI is in early production with a locked architecture direction:

- no ad hoc components
- contract-first behavior
- bounded deterministic rendering
- deterministic input and focus routing
- flat, minimal card surfaces with low chrome

## Current Baseline

The framework baseline is organized into clear layers:

- runtime/core: `shell`, `router`, `layout`, `focus`, `surface`, `theme`, `core`
- UI components: `ui/components/*`
- shared primitives: `ui/primitives`
- style layer: `ui/styles`

Theme set remains locked and deterministic:

- `catppuccin-mocha` (default)
- `dracula`
- `osaka-jade`

## Active Workstream

1. Footer card model and deterministic truncation contract.
2. Focus manager hardening (`SetRing`, `SetIndex`, `FocusBy`, events, wrap/enable behavior).
3. Shared UI primitives (modal frame, input surface, list row, footer card).
4. Broader regression coverage (dialog bounds, footer rendering, key routing).

## Command-First Harness Model

The harness is now command-string based and footer-card driven:

- primary commands: `/pr`, `/issue`, `/branch`
- legacy aliases still resolve: `/dialog`, `/theme`, `/page`
- `/` no longer auto-opens a modal

This keeps interaction deterministic and aligned with the shell/footer card model.

## Success Criteria

Roadmap milestones are considered stable when behavior is deterministic under resize, focus transitions, and overlay routing, and when validation passes remain consistent:

- `go test ./...`
- `go vet ./...`

## Related Docs

- `project-docs/bentotui-main-spec.md`
- `project-docs/component-system-reference.md`
- `project-docs/layer-architecture.md`
- `project-docs/next-steps.md`
