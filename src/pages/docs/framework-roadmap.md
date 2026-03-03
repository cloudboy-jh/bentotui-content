---
layout: ../../layouts/DocsLayout.astro
title: BentoTUI Framework Roadmap
description: Current execution order and development milestones for BentoTUI.
---

# BentoTUI Framework Roadmap

**Status:** v0.2 Active Development

---

## Overview

BentoTUI is in early development — APIs and registry paths will change. This roadmap tracks execution order from the starter app through CLI tooling.

---

## Execution Order

### 1. ✅ Starter App — COMPLETE

Home screen with surface-backed rendering. Demonstrates:

- Full-screen cell buffer (Ultraviolet)
- Deterministic background painting
- Command parsing (`/theme`, `/dialog`)
- Live theme switching across 15 presets

**Run it:**
```bash
go run ./cmd/starter-app
```

---

### 2. → Tier 1 Components — IN PROGRESS

Core UI primitives that many bentos will depend on:

| Component | Description | Status |
|-----------|-------------|--------|
| `badge` | Inline colored label | 🔄 |
| `kbd` | Keyboard shortcut display (dim/bright pair) | 🔄 |
| `wordmark` | Large centered app name, theme-colored, responsive | 🔄 |
| `statusbar` | Standalone registry version of `bar` | 🔄 |

---

### 3. ○ Home-Screen Bento

First bento — mirrors the starter app as a copyable template:

**Components used:** `wordmark`, `input`, `kbd`, `badge`, `bar`, `surface`

A single `.go` file demonstrating real component composition that developers can copy and modify.

---

### 4. ○ Tier 2 Components

Interactive input components:

| Component | Description |
|-----------|-------------|
| `select` | Single-choice picker, opens inline |
| `checkbox` | Togglable boolean |
| `textarea` | Multi-line input, wraps `bubbles/textarea` |
| `spinner` | Loading indicator, wraps `bubbles/spinner` |
| `progress` | Progress bar with optional label |

---

### 5. ○ Remaining Bentos

Complete screen patterns:

| Bento | Components Used | Purpose |
|-------|-----------------|---------|
| `app-shell` | `panel`, `layout`, `bar`, `tabs`, `surface` | Main application frame |
| `dashboard` | `panel`, `badge`, `table`, `layout`, `surface` | Data overview screen |
| `detail-view` | `list`, `panel`, `layout`, `surface` | Item detail screen |
| `form` | `input`, `textarea`, `checkbox`, `badge`, `surface` | Settings/input form |

---

### 6. ○ Tier 3 Components

Advanced UI patterns:

| Component | Description |
|-----------|-------------|
| `command` | Command palette with fuzzy search |
| `toast` | Ephemeral notification, auto-dismisses, stacks |
| `tabs` | Horizontal tab switcher |
| `separator` | Horizontal or vertical rule |

---

### 7. ○ CLI Embed Wiring

Enable `bento add` to copy from embedded registry filesystem:

```bash
bento add input     # Copies from embedded fs to your project
bento add bar surface dialog
```

---

### 8. ○ `bento init` Template

Single-screen starter template:

```bash
bento init myapp    # Scaffolds a new TUI with surface + bar + input
```

---

## Philosophy

- **No framework lock-in** — You own the source after `bento add`
- **Copy-and-own** — Read it, modify it, delete what you don't need
- **No lifecycle hooks** — Components are plain Bubble Tea models
- **No "extend" API** — Compose, don't inherit
- **Bounded deterministic rendering** — `surface` cell buffer eliminates ANSI bleed

---

## Available Components (v0.2)

Already implemented and ready to use:

| Component | Description |
|-----------|-------------|
| `surface` | Full-screen cell buffer backed by Ultraviolet |
| `bar` | Status/nav bar with left + right slots |
| `input` | Single-line text input with left-border accent |
| `panel` | Titled, focusable content container |
| `dialog` | Modal manager — Confirm, Custom, ThemePicker |
| `list` | Scrollable log-style list |
| `table` | Header + data rows |
| `text` | Static styled label |

---

## Theme System

15 built-in presets, goroutine-safe global store:

```go
// Set once at startup
theme.SetTheme("tokyo-night")

// Components always call this in View() — never cache it
t := theme.CurrentTheme()
```

Available: `catppuccin-mocha` (default), `catppuccin-macchiato`, `catppuccin-frappe`, `dracula`, `tokyo-night`, `tokyo-night-storm`, `nord`, `gruvbox-dark`, `monokai-pro`, `kanagawa`, `rose-pine`, `ayu-mirage`, `one-dark`, `material-ocean`, `github-dark`.

---

## Quick Start

```bash
# Install the CLI
go install github.com/cloudboy-jh/bentotui/cmd/bento@latest

# Get core deps
go get github.com/cloudboy-jh/bentotui

# Copy components
bento add input bar surface

# Run the starter app
go run ./cmd/starter-app
```

---

## Related

- [Architecture](./architecture) — Component registry architecture and API reference
