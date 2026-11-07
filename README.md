# UI-md 📱✨

> **The Definitive Apple HIG Design System & AI Coding Agent Architecture for iOS / iPadOS**

[![Swift](https://img.shields.io/badge/Swift-5.9%2B-orange.svg?style=flat&logo=swift)](https://swift.org)
[![iOS](https://img.shields.io/badge/iOS-17.0%2B-blue.svg?style=flat&logo=apple)](https://developer.apple.com/ios/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Apps Catalog](https://img.shields.io/badge/Apps%20Reverse--Engineered-200-brightgreen.svg)](references/UI_REFERENCES_INDEX.md)
[![Apple HIG](https://img.shields.io/badge/Apple%20HIG-100%25%20Compliant-purple.svg)](rules/ios_core_hig.md)
[![App Store Review](https://img.shields.io/badge/App%20Store%20Review-Section%2010%20Ready-success.svg)](rules/app_store_review_rules.md)

**UI-md** is an open-source, battle-tested design framework and AI instruction toolkit built for mobile software engineers, product designers, and AI coding agents (Cursor, Windsurf, Claude Code, Antigravity, Copilot).

It pairs **200 reverse-engineered design systems** from top iOS applications (Airbnb, Spotify, Duolingo, Tinder, Notion, Cash App, Apple Wallet, etc.) with strict **Apple Human Interface Guidelines (HIG)** rules, App Store approval checklists, and native Swift CLI tooling.

---

## 🧭 Table of Contents

- [Why UI-md?](#-why-ui-md)
- [Repository Architecture](#-repository-architecture)
- [The 4 Core Pillars](#-the-4-core-pillars)
  - [1. 200 Reverse-Engineered Apps Catalog](#1-200-reverse-engineered-apps-catalog)
  - [2. Apple HIG & App Store Review Guardrails](#2-apple-hig--app-store-review-guardrails)
  - [3. Portable AI Agent Integration (Cursor, Claude, Windsurf)](#3-portable-ai-agent-integration)
  - [4. Native Swift CLI Tooling (`designmd-swift`)](#4-native-swift-cli-tooling)
- [Quick Start Guide](#-quick-start-guide)
- [Reference Implementation: ChronoQuest](#-reference-implementation)
- [DESIGN.md Specification](#-designmd-specification)
- [Contributing](#-contributing)
- [License](#-license)

---

## 💡 Why UI-md?

Modern AI agents often produce web-like, un-ergonomic iOS interfaces with arbitrary hex codes, undersized touch targets (< 44pt), linear animations, and lack of Dynamic Type or Dark Mode.

**UI-md solves this once and for all:**
* **Zero Guessing Tokens:** Machine-readable YAML front matter paired with human-readable Markdown.
* **Apple HIG by Default:** Guarantees 44×44pt touch targets, Taptic Engine feedback, Spring physics (`.spring(response: 0.35, dampingFraction: 0.75)`), and Safe Area / Dynamic Island respect.
* **App Store Rejection Proof:** Built-in verification against Section 10 UI criteria (no fake buttons, no webview wrappers, proper iconography).

---

## 🏛️ Repository Architecture

```
UI-md/
├── README.md                      # Global master documentation & index
├── PORTABLE_IOS_DESIGN_RULES.md   # All-in-one portable rule set for any iOS project
├── AGENTS.md                      # AI agent entry point & behavior instructions
├── LICENSE                        # MIT Open Source License
├── CONTRIBUTING.md                # Community contribution guidelines
├── rules/                         # Core Apple & design system specifications
│   ├── ios_core_hig.md           # Apple HIG interaction rules (44pt, Haptics, Spring)
│   ├── app_store_review_rules.md  # Section 10 App Store review rejection criteria
│   ├── adaptive_m3_ios.md         # Material Design 3 adaptation for iOS
│   └── design_md_spec.md          # YAML Frontmatter + Markdown DESIGN.md spec
├── references/
│   └── UI_REFERENCES_INDEX.md     # Master catalog indexing 200 world-class apps
├── ui-references/                 # 200 reverse-engineered app design systems
│   ├── dating/                   # 12 apps (Tinder, Bumble, Hinge, etc.)
│   ├── finance/                  # 22 apps (Apple Wallet, Cash App, Robinhood, etc.)
│   ├── fitness/                  # 19 apps (Calm, AllTrails, Apple Fitness, etc.)
│   ├── food/                     # 16 apps (DoorDash, Deliveroo, Starbucks, etc.)
│   ├── messaging/                # 16 apps (Discord, Telegram, iMessage, etc.)
│   ├── misc/                     # 20 apps (Duolingo, ChatGPT, Amazon, etc.)
│   ├── music/                    # 14 apps (Apple Music, Spotify, Audible, etc.)
│   ├── productivity/             # 22 apps (Notion, Asana, Bear, Google Calendar, etc.)
│   ├── social/                   # 23 apps (Instagram, BeReal, Bluesky, etc.)
│   ├── travel/                   # 20 apps (Airbnb, Apple Maps, Uber, etc.)
│   └── video/                    # 16 apps (Netflix, Disney+, YouTube, Twitch, etc.)
├── agents/
│   └── ios-ui-architect.md        # Specialized iOS UI/UX Lead Architect prompt
└── designmd-swift/                # Native Swift CLI tool (Linter & Theme.swift generator)
```

---

## ⚡ The 4 Core Pillars

### 1. 200 Reverse-Engineered Apps Catalog

Explore tokenized color palettes, typography scales, corner radii, elevation curves, and production-grade SwiftUI component patterns across 11 industries:

| Category | Apps Count | Prominent Examples | Directory |
| :--- | :---: | :--- | :--- |
| **Dating** | 12 | Bumble, Tinder, Hinge, Raya, Feeld | [`ui-references/dating/`](ui-references/dating/) |
| **Finance** | 22 | Apple Wallet, Cash App, Binance, Robinhood, Revolut | [`ui-references/finance/`](ui-references/finance/) |
| **Fitness** | 19 | Apple Fitness, Calm, Fitbit, Strava, Nike | [`ui-references/fitness/`](ui-references/fitness/) |
| **Food & Drink** | 16 | DoorDash, Deliveroo, Starbucks, Domino's | [`ui-references/food/`](ui-references/food/) |
| **Messaging** | 16 | Discord, iMessage, Telegram, KakaoTalk, GroupMe | [`ui-references/messaging/`](ui-references/messaging/) |
| **Misc & AI** | 20 | Duolingo, ChatGPT, Character AI, Amazon | [`ui-references/misc/`](ui-references/misc/) |
| **Music** | 14 | Apple Music, Spotify, Audible, Bandcamp | [`ui-references/music/`](ui-references/music/) |
| **Productivity** | 22 | Notion, Asana, Bear, Apple Notes, Google Calendar | [`ui-references/productivity/`](ui-references/productivity/) |
| **Social** | 23 | Instagram, BeReal, Bluesky, TikTok, Twitter/X | [`ui-references/social/`](ui-references/social/) |
| **Travel** | 20 | Airbnb, Apple Maps, Uber, Booking.com, Waze | [`ui-references/travel/`](ui-references/travel/) |
| **Video & Streaming** | 16 | Netflix, Apple TV, Disney+, YouTube, Twitch | [`ui-references/video/`](ui-references/video/) |

👉 **[View the Complete Interactive 200-App Table](references/UI_REFERENCES_INDEX.md)**

---

### 2. Apple HIG & App Store Review Guardrails

Every rule in [`rules/`](rules/) is non-negotiable:
1. **44 × 44 pt Touch Target:** Every interactive element has `.contentShape(Rectangle())` with at least 44pt hit dimensions.
2. **Spring Physics Motion:** Strict ban on linear animations. Always uses `.spring(response: 0.35, dampingFraction: 0.75)`.
3. **Tactile Haptic Feedback:** Taptic engine triggers on snaps, selection changes, success, and errors.
4. **Dynamic Type & Semantic Colors:** Adaptive Light/Dark mode via semantic system colors and Dynamic Type scaling without layout clipping.
5. **Thumb Zone Ergonomics:** Primary action buttons anchored at 54pt height in the bottom thumb zone with Safe Area padding.

---

### 3. Portable AI Agent Integration

You can integrate UI-md into **any existing iOS project in 10 seconds**:

#### In Cursor (`.cursorrules`):
Copy [`PORTABLE_IOS_DESIGN_RULES.md`](PORTABLE_IOS_DESIGN_RULES.md) into your project root and add this to `.cursorrules`:
```markdown
Refer to PORTABLE_IOS_DESIGN_RULES.md for all UI/UX guidelines:
- Enforce 44x44pt touch targets on all buttons and handles.
- Use spring animations (.spring(response: 0.35, dampingFraction: 0.75)).
- Use semantic colors with Dark Mode support and WCAG 4.5:1 contrast.
- Ensure Dynamic Type support and App Store Section 10 compliance.
```

#### In Claude Code, Windsurf, or Antigravity:
Simply copy [`PORTABLE_IOS_DESIGN_RULES.md`](PORTABLE_IOS_DESIGN_RULES.md) and [`AGENTS.md`](AGENTS.md) into your repo root.

---

### 4. Native Swift CLI Tooling (`designmd-swift`)

A native Swift tool to lint `DESIGN.md` files and generate production `Theme.swift` code:

```bash
cd designmd-swift
swift build -c release

# Lint a DESIGN.md file
.build/release/designmd lint /path/to/DESIGN.md

# Generate Swift Theme
.build/release/designmd generate /path/to/DESIGN.md --output Sources/Theme.swift
```

---

## 🎮 Reference Implementation

Check out how UI-md was used to design and architect **ChronoQuest**—an interactive time and calendar puzzle game built with 100% Apple HIG compliance, polar coordinate drag gestures, dynamic atmospheric clock dial, and haptic feedback.

---

## 📄 DESIGN.md Specification

Every `DESIGN.md` in UI-md adheres to a dual-layer specification:
* **Machine Layer (YAML Front Matter):** Explicit token values (`colors`, `typography`, `spacing`, `motion`).
* **Human Layer (Markdown):** Rationale, UX patterns, and interaction mechanics.

```yaml
---
name: AppName
platform:
  os: [iOS, iPadOS]
  minimumDeployment: "17.0"
colors:
  primary:
    light: "#1C1C1E"
    dark: "#F2F2F7"
  accent: "#007AFF"
touchTargets:
  minimum: 44pt
  buttonHeight: 54pt
motion:
  springDefault:
    response: 0.35
    dampingFraction: 0.75
---
```

---

## 🤝 Contributing

We welcome contributions! Please read our [Contributing Guidelines](CONTRIBUTING.md) to add new apps, refine design tokens, or improve CLI tooling.

---

## 📜 License

Distributed under the **MIT License**. See [LICENSE](LICENSE) for more information.

---

<p align="center">
  Crafted with ❤️ for the Apple & AI Developer Community by <b>Ali Beysülen</b>
</p>

