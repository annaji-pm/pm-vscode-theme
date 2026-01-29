# Changelog

All notable changes to the PolicyMe Theme extension will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.1.0] - 2026-01-27

### Added
- **PolicyMe Dark theme** - Dark variant with green-tinted dark backgrounds
- Dark theme uses brightened accent colors for visibility:
  - Primary green: `#9ec46a` (brightened from `#455326`)
  - Accent orange: `#ffb850` (kept as-is, good dark contrast)
  - Error red: `#ff6b4a` (brightened from `#db2200`)
  - Info blue: `#5a9fd4`
  - Class/decorator purple: `#c77dbb`
- Dark theme backgrounds derived from primary green hue:
  - Editor: `#1a1d16`
  - Sidebar: `#1e211a`
  - Panels: `#252820`

## [1.0.0] - 2026-01-27

### Added
- Initial release of PolicyMe Light theme
- Comprehensive workbench colors based on PolicyMe rebrand design system
- TextMate syntax highlighting for:
  - Python (including self, magic methods)
  - TypeScript/JavaScript (including type annotations)
  - JSON/YAML
  - Markdown
  - CSS/SCSS
  - Shell/Bash
  - HTML/JSX
- Semantic token colors for enhanced TypeScript/JavaScript highlighting
- Full terminal ANSI color mapping
- Git decoration colors
- Diff editor colors
- Debug and testing colors
- Chat/inline chat colors for AI features

### Color Sources
- Primary CTA: `#455326` (dark green)
- Link/Accent: `#a84300` (orange/brown)
- Page Background: `#fbf9f6` (light beige)
- Body Text: `#30332a` (dark gray)
- Alert Error: `#db2200` (red)
- All colors sourced from `global-libjs-designsystem/src/palettes.ts` (policyme_rebrand)

## [Unreleased]

### Planned
- High contrast variants (if requested)
