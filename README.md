# PolicyMe Theme for VS Code / Cursor

A VS Code color theme based on PolicyMe's rebrand design system. Built for in-house developer use.

![PolicyMe Theme](https://img.shields.io/badge/PolicyMe-VS_Code_Theme-455326?style=for-the-badge&labelColor=fbf9f6)

## Features

- **Light theme** matching PolicyMe webapp aesthetic
- **Dark theme** with green-tinted dark backgrounds, derived from rebrand palette
- Colors extracted from `global-libjs-designsystem` rebrand palette
- Comprehensive syntax highlighting for Python, TypeScript, JavaScript, JSON, YAML, Markdown, and more
- Semantic highlighting support for enhanced TypeScript/JavaScript coloring

## Color Palette

### Light Theme
| Element | Color | Hex |
|---------|-------|-----|
| Primary Green | ![#455326](https://img.shields.io/badge/-%23455326-455326) | `#455326` |
| Accent Orange | ![#a84300](https://img.shields.io/badge/-%23a84300-a84300) | `#a84300` |
| Background | ![#fbf9f6](https://img.shields.io/badge/-%23fbf9f6-fbf9f6) | `#fbf9f6` |
| Text | ![#30332a](https://img.shields.io/badge/-%2330332a-30332a) | `#30332a` |
| Error | ![#db2200](https://img.shields.io/badge/-%23db2200-db2200) | `#db2200` |

### Dark Theme
| Element | Color | Hex |
|---------|-------|-----|
| Primary Green | ![#9ec46a](https://img.shields.io/badge/-%239ec46a-9ec46a) | `#9ec46a` |
| Accent Orange | ![#ffb850](https://img.shields.io/badge/-%23ffb850-ffb850) | `#ffb850` |
| Background | ![#1a1d16](https://img.shields.io/badge/-%231a1d16-1a1d16) | `#1a1d16` |
| Text | ![#e8e8e4](https://img.shields.io/badge/-%23e8e8e4-e8e8e4) | `#e8e8e4` |
| Error | ![#ff6b4a](https://img.shields.io/badge/-%23ff6b4a-ff6b4a) | `#ff6b4a` |

## Installation

### VS Code

**Option 1: Install from VSIX file**
```bash
code --install-extension policyme-theme-1.0.0.vsix
```

**Option 2: Command Palette**
1. Open Command Palette (`Cmd+Shift+P` / `Ctrl+Shift+P`)
2. Type `Extensions: Install from VSIX...`
3. Select the `.vsix` file

### Cursor

**Option 1: Drag and drop**
- Drag the `.vsix` file into the Extensions pane

**Option 2: Command Palette**
1. Open Command Palette (`Cmd+Shift+P` / `Ctrl+Shift+P`)
2. Type `Extensions: Install from VSIX...`
3. Select the `.vsix` file

## Activating the Theme

1. Open Command Palette (`Cmd+Shift+P` / `Ctrl+Shift+P`)
2. Type `Preferences: Color Theme`
3. Select **PolicyMe Light**

## Building from Source

### Prerequisites
- Node.js 20+
- npm

### Package the extension
```bash
npm install -g @vscode/vsce
cd pm_vscode_theme
vsce package
```

This produces `policyme-theme-1.0.0.vsix`.

## Development

### Testing locally
1. Open this folder in VS Code
2. Press `F5` to launch Extension Development Host
3. The theme will be available in the new window

### File structure
```
pm_vscode_theme/
  package.json                              # Extension manifest
  README.md                                 # This file
  CHANGELOG.md                              # Version history
  LICENSE                                   # MIT license
  themes/
    policyme-light-color-theme.json         # Light theme definition
  opus_policyme_vscode_theme_plan.md        # Implementation plan
```

### Adding an icon (optional)
To add an extension icon:
1. Create a 128x128 PNG file
2. Save as `images/icon.png`
3. Add to `package.json`: `"icon": "images/icon.png"`

## Roadmap

- [x] v1.0.0 - PolicyMe Light theme
- [x] v1.1.0 - PolicyMe Dark theme

## Feedback

For issues or suggestions, reach out to the engineering team.

## License

MIT - See [LICENSE](LICENSE) file.
