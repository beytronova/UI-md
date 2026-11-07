# Contributing to UI-md 🎨

Thank you for your interest in contributing to **UI-md**! This repository aims to be the most comprehensive, battle-tested Apple HIG design system reference and AI coding agent rule set for iOS & iPadOS apps.

---

## 🌟 How You Can Contribute

1. **Add a New App Design System (`ui-references/`):**
   - Reverse-engineer an industry-leading iOS application.
   - Follow the `rules/design_md_spec.md` specification (YAML front matter tokens + Markdown).
   - Provide both `DESIGN.md` (Design tokens & system) and `DESIGN-swiftui.md` (SwiftUI implementations).
   - Update `references/UI_REFERENCES_INDEX.md` with the new entry and relative link.

2. **Improve iOS HIG & Architecture Rules (`rules/`):**
   - Keep Apple HIG, Adaptive Material 3, and App Store Review standards updated with the latest iOS releases (iOS 17, 18+).

3. **Enhance AI Agent Prompts (`agents/` & `PORTABLE_IOS_DESIGN_RULES.md`):**
   - Optimize prompts for Cursor, Windsurf, Claude Code, GitHub Copilot, and Google Antigravity.

4. **Improve CLI Tooling (`designmd-swift/`):**
   - Add features to the native Swift linter and Theme generator.

---

## 📋 Pull Request Guidelines

- Ensure all markdown links in your PR use relative paths (`../ui-references/...`).
- Keep YAML front matter valid and adhering to `rules/design_md_spec.md`.
- Test that any SwiftUI code compiles with Swift 5.9+.
- Provide a clear PR description explaining the changes or the app reverse-engineered.

---

## 📄 License

By contributing to UI-md, you agree that your contributions will be licensed under the [MIT License](LICENSE).
