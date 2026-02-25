---
layout: ../../layouts/DocsLayout.astro
title: BentoTUI Main Spec
description: Canonical BentoTUI framework specification.
---

# BentoTUI Main Spec

The application framework for Bubble Tea. Compartmentalized layouts, composable components, shipped apps.

---

## Overview

BentoTUI is a Go framework that sits between Charm's Bubble Tea primitives and production TUI applications. Every polished terminal app built today (Crush, OpenCode, lazygit, k9s) independently reinvents the same architectural patterns: layout systems, focus management, dialog overlays, command palettes, and component composition. BentoTUI extracts these patterns into importable, composable building blocks.

Charm gives you bricks. BentoTUI gives you rooms.

```go
import "github.com/cloudboy-jh/bentotui"
```

### Implementation Update (Current)

- v0.1 foundation is now implemented in code (`app`, `router`, `layout`, `focus`, `theme`, `ui/components/dialog`, `ui/components/footer`, `ui/components/panel`)
- Rendering moved from plain string concatenation to styled surfaces with Lip Gloss v2
- Horizontal composition now uses ANSI-aware joining to avoid escape-sequence width drift
- Dialogs are rendered through a layer/canvas composition path and centered in the app shell
- Internal harness app added at `cmd/test-tui` for daily framework regression checks

## What This Is

- An application-level framework built on top of Bubble Tea
- A layout and composition system for terminal UIs
- A set of higher-order components that every TUI app needs
- The missing layer between `bubbletea.Model` and a shipped product

## What This Is Not

- A replacement for Bubble Tea, Bubbles, or Lip Gloss
- A widget library (Bubbles already does that)
- A styling library (Lip Gloss already does that)
- A terminal rendering engine
- A React/declarative UI system (that's OpenTUI's lane)

## Architecture

### The Gap

```text
BUBBLE TEA              BENTOTUI                    YOUR APP
(primitives)            (application patterns)      (domain logic)
─────────────           ──────────────────          ──────────────
tea.Model          →    App shell + router      →   Pages
tea.Msg            →    Message routing tree    →   Business events
tea.WindowSizeMsg  →    Responsive layout       →   Panel config
lipgloss.Style     →    Theme system            →   Brand colors
lipgloss.Join*     →    Panel composition       →   Layout definition
lipgloss.Layer     →    Dialog/overlay system   →   Modals
bubbles/*          →    Enhanced components     →   Domain widgets
(nothing)          →    Focus management        →   Navigation
(nothing)          →    Command palette         →   App commands
(nothing)          →    Status bar              →   Context help
```

### Component Model

```go
type Component interface {
    tea.Model
}

type Sizeable interface {
    Component
    SetSize(width, height int)
    GetSize() (width, height int)
}

type Focusable interface {
    Component
    Focus()
    Blur()
    IsFocused() bool
}

type Positional interface {
    Component
    SetPosition(x, y int)
}

type Bindable interface {
    Component
    Bindings() []key.Binding
}
```

### Message Routing

```text
App
├── Router (page switching)
│   ├── Page A
│   │   ├── Panel (focused) ← receives input
│   │   ├── Panel
│   │   └── StatusBar
│   └── Page B
├── DialogManager ← captures input when active
│   └── Active Dialog
└── Palette ← captures input when open
```

## Modules

### Core

#### `app` — Application Shell

```go
app := bentotui.New(
    bentotui.WithTheme(myTheme),
    bentotui.WithPages(
        bentotui.Page("home", newHomePage),
        bentotui.Page("settings", newSettingsPage),
    ),
    bentotui.WithFooterBar(true),
)

p := tea.NewProgram(app)
```

#### `router` — Page System

```go
func switchPage() tea.Msg {
    return router.Navigate("settings")
}

type Page interface {
    Component
    Sizeable
    Title() string
}
```

#### `layout` — Responsive Panel System

```go
layout := layout.Horizontal(
    layout.Fixed(30, sidebar),
    layout.Flex(1, mainContent),
)

layout = layout.Vertical(
    layout.Fixed(1, header),
    layout.Flex(1, body),
    layout.Fixed(5, editor),
)
```

#### `focus` — Focus Management

```go
focus := focus.New(
    focus.Ring(editor, messages, sidebar),
    focus.Keys(
        key.NewBinding(key.WithKeys("tab"), key.WithHelp("tab", "next panel")),
        key.NewBinding(key.WithKeys("shift+tab"), key.WithHelp("shift+tab", "prev panel")),
    ),
)
```

#### `theme` — Color System

```go
theme := theme.Preset("catppuccin-mocha")
```

### Components

#### `ui/components/dialog` — Modal Overlay System

```go
func confirmDelete() tea.Msg {
    return dialog.Open(dialog.Confirm{
        DialogTitle: "Delete secret?",
        Message: "This cannot be undone.",
        OnConfirm: func() tea.Msg { return deleteMsg{} },
    })
}
```

#### `palette` — Command Palette

```go
palette := palette.New(
    palette.Command("/new", "New session", newSessionCmd),
    palette.Command("/models", "Switch model", openModelPickerCmd),
)
```

#### `picker` — Searchable Grouped Picker

```go
picker := picker.New(
    picker.Group("Recent",
        picker.Item("GPT-5.3 Codex", "OpenAI"),
    ),
    picker.WithSearch(true),
)
```

#### `ui/components/footer` — Context-Aware Footer Bar

```go
footer := footer.New(
    footer.Left("~/projects/porter:main"),
    footer.Right("v1.2.10"),
    footer.HelpFrom(focusedComponent),
)
```

#### `ui/components/panel` — Bordered Content Panel

```go
panel := panel.New(
    panel.Theme(theme.Preset("catppuccin-mocha")),
    panel.Title("Messages"),
    panel.Content(viewport),
)
```

## Design Principles

1. Additive — sits on top of Bubble Tea
2. Opt-in — use full shell or cherry-pick components
3. Explicit — no hidden magic
4. Minimal deps — Bubble Tea + Bubbles + Lip Gloss
5. Dogfood-driven — validated by real apps
6. Convention over configuration — sensible defaults

## Build Targets

BentoTUI builds on Bubble Tea v2 (beta) and Lip Gloss v2 (beta).

```go
go 1.23+

require (
    charm.land/bubbletea/v2
    charm.land/bubbles/v2
    charm.land/lipgloss/v2
)
```

## Validation Plan

Run the internal harness:

```bash
go run ./cmd/test-tui
```

Current checks:

- shell composition (`header` + `main` + `footer`)
- live theme switching and persistence
- dialog overlays and command paths
- focus handling (`tab`, `shift+tab`)
- primitive-first rendering behavior on fullscreen alt-screen

## Scope — v0.1

- [x] `app`
- [x] `router`
- [x] `layout`
- [x] `focus`
- [x] `theme`
- [x] `dialog`
- [x] `ui/components/footer`
- [x] `panel`

Not in v0.1:

- Command palette (v0.2)
- Picker component (v0.2)
- Responsive breakpoints (v0.2)
- Event bus (v0.2)

## References

- [Rendering System Design (ADR-0001)](./rendering-system-design)
- [Implementation Next Steps](./next-steps)
- [TUI Framework Research Doc](./tui-framework-research)
- [Crush TUI Architecture](https://deepwiki.com/charmbracelet/crush/5.1-tui-architecture)
- [Bubble Tea](https://github.com/charmbracelet/bubbletea)
- [Bubbles](https://github.com/charmbracelet/bubbles)
- [Lip Gloss](https://github.com/charmbracelet/lipgloss)
- [OpenTUI](https://github.com/sst/opentui)
