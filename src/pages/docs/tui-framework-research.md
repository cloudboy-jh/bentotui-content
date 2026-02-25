---
layout: ../../layouts/DocsLayout.astro
title: TUI Application Framework Research
description: Research document behind BentoTUI's architecture and scope.
---

# TUI Application Framework Research

Building the missing layer between Bubble Tea and shipped apps.

Author: Jack Horton  
Date: February 23, 2026  
Status: Research Phase

---

## 1. Executive Summary

Every polished TUI application built on Charm's Bubble Tea framework (Crush, OpenCode, lazygit, k9s) independently reinvents the same architectural patterns: layout systems, focus management, dialog overlays, command palettes, and component composition. None of these patterns are provided by Bubble Tea or its companion libraries.

The thesis: there is a well-defined architectural layer between "Bubble Tea primitives" and "shipped application" that nobody has packaged into a reusable, importable framework.

## 2. The Charm Ecosystem — What Exists Today

### 2.1 Bubble Tea

Provides:

- Program lifecycle management
- Message-based event loop
- Framerate-based renderer
- Mouse support and focus reporting
- Alternate screen buffer
- Inline and fullscreen modes

Does not provide:

- Component composition system
- Focus system across panes
- Multi-panel app layout policy
- Multi-page app shell conventions

### 2.2 Bubbles

Pre-built components implementing `tea.Model` (`textinput`, `textarea`, `viewport`, `list`, `table`, `help`, `key`, etc.).

Gap: no architectural composition layer across multiple widgets.

### 2.3 Lip Gloss

Provides styling and composition primitives, including v2 `Layer` and `Canvas`.

Gap: no flexbox or high-level responsive layout engine.

### 2.4 Other Charm Libraries

Useful but non-foundational for the app-shell gap (Harmonica, BubbleZone, Gum, VHS, Log).

## 3. Crush (formerly OpenCode) — The Reference Implementation

### 3.1 Background

Crush is Charm's AI coding agent. It and OpenCode independently evolved similar TUI patterns after their fork.

### 3.2 Crush TUI Architecture

Root app model includes:

- `pages[]` (page system)
- `dialog` manager
- `completions` popup
- `status` bar/help
- current page routing state
- terminal dimensions

### 3.3 Component Interface System

Interfaces used in practice:

- `util.Model`
- `layout.Sizeable`
- `layout.Focusable`
- `layout.Positional`
- `layout.Help`
- `util.Cursor`

This interface stack is effectively the skeleton for BentoTUI.

### 3.4 Message Routing Pattern

Messages route hierarchically: `appModel -> page -> component`.

Each layer can handle, forward, or ignore.

### 3.5 Rendering Pipeline

1. Active page renders content.
2. Status bar appends.
3. Base layer created.
4. Dialog/completions layers composed.
5. Canvas composited.
6. Cursor positioned from focused component.

### 3.6 Focus Management

Tab/Shift+Tab cycles focus across panes. Focus changes both input routing and visual style.

### 3.7 Dialog System

Modal overlays capture input, render above base content, and open/close via typed messages.

## 4. OpenTUI — The TypeScript Alternative

### 4.1 Architecture

- Zig-based native rendering engine with TS bindings
- Solid and React reconcilers
- Declarative model

### 4.2 Why It's Too Niche (for this goal)

1. TS/Zig dependency chain
2. Zig install requirement
3. Different mental model for Go-first teams
4. Early-stage stability profile
5. Closer coupling to SST ecosystem

### 4.3 What It Gets Right

- Right abstraction level
- Framework-level packaging
- Scaffolding workflows
- AI-friendly conventions

### 4.4 Takeaways for BentoTUI

- Ship in Go, for Go developers
- Add templates/scaffolding later
- Keep docs and patterns AI-readable
- Avoid exotic build dependencies

## 5. Shipped TUI Apps — Pattern Analysis

Common repeated patterns across major apps:

- Multi-panel layout
- Focus management
- Command palette/slash commands
- Modal dialogs
- Searchable pickers
- Status bar + key help
- Responsive mode handling
- Theme/color systems

What every app rebuilds:

1. App shell and page routing
2. Layout engine and size math
3. Focus ring and input ownership
4. Overlay and modal composition
5. Command palette + fuzzy behavior
6. Grouped/searchable pickers
7. Contextual status and help bar
8. Theme token coordination

## 6. Gap Analysis — Framework Surface

### 6.1 What Charm Provides vs. What Apps Need

Charm provides primitives. Apps need architecture. BentoTUI fills this middle layer.

### 6.2 Proposed Framework Modules

Core:

- `app`
- `layout`
- `focus`
- `router`
- `theme`

Components:

- `dialog`
- `palette`
- `picker`
- `statusbar`
- `editor`
- `panel`

Utilities:

- `keys`
- `events`
- `size`

## 7. Competitive Landscape

Closest analogue by abstraction level: Textual (Python).  
Go ecosystem has strong primitives but no dominant application-shell framework.

## 8. Design Principles

1. Additive, not replacement
2. Opt-in complexity
3. Zero magic
4. Minimal dependencies
5. Dogfood-driven
6. Convention over configuration

## 9. Open Questions

1. Bubble Tea v2 timing and risk profile
2. Lip Gloss v2 Layer/Canvas adoption timeline
3. Final naming and positioning
4. v0.1 minimum viable surface
5. Flexbox strategy in terminal layout

## 10. Recommended Next Steps

1. Audit Crush `internal/tui/` deeply
2. Audit OpenCode `internal/tui/` divergence
3. Prototype layout + focus as standalone packages
4. Build a framework-only demo app
5. Freeze public API design early

## Sources

- https://github.com/charmbracelet/crush
- https://deepwiki.com/charmbracelet/crush/5.1-tui-architecture
- https://github.com/opencode-ai/opencode
- https://github.com/sst/opentui
- https://github.com/charmbracelet/bubbletea
- https://github.com/charmbracelet/bubbles
- https://github.com/charmbracelet/lipgloss
- https://github.com/charmbracelet/lipgloss/issues/166
- https://github.com/76creates/stickers
- https://leg100.github.io/en/posts/building-bubbletea-programs/
