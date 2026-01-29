# PolicyMe Rebrand VS Code/Cursor Theme Extension Plan

## Overview

Create a VS Code theme extension implementing PolicyMe's rebrand design system colors for in-house developer use. Cursor inherits VS Code's theming capabilities and supports VS Code themes (per [Cursor Themes docs](https://docs.cursor.com/configuration/themes)).

## PolicyMe Rebrand Color Palette

Extracted from `global-libjs-designsystem/src/palettes.ts` (lines 2319-2482):

### Primary Colors
| Token                | Hex       | Usage                    |
| -------------------- | --------- | ------------------------ |
| Primary CTA          | `#455326` | Buttons, primary actions |
| Primary CTA Hover    | `#566830` | Button hover states      |
| Primary CTA Disabled | `#9aa483` | Disabled states          |
| Primary Stroke       | `#30332a` | Borders, outlines        |

### Accent Colors
| Token             | Hex       | Usage                |
| ----------------- | --------- | -------------------- |
| Accent Fill Light | `#ffb850` | Highlights, badges   |
| Link              | `#a84300` | Links, active states |
| Link Hover        | `#803503` | Link hover           |

### Text Colors
| Token          | Hex       | Usage        |
| -------------- | --------- | ------------ |
| Headings       | `#30332a` | Primary text |
| Secondary Text | `#656a59` | Muted text   |

### Background Colors
| Token                 | Hex       | Usage                     |
| --------------------- | --------- | ------------------------- |
| Page Background       | `#fbf9f6` | Editor background (light) |
| Card Background       | `#ffffff` | Panel backgrounds         |
| Card Background 2     | `#dfe5cf` | Secondary panels          |
| Navigation Background | `#f2ede6` | Sidebar                   |

### Semantic/Alert Colors
| Token               | Hex       | Usage                              |
| ------------------- | --------- | ---------------------------------- |
| Alert Error         | `#db2200` | Error states, diagnostics          |
| Alert Error Bg      | `#fceeed` | Error background                   |
| Alert Warning       | `#ffb850` | Warning states                     |
| Alert Warning Bg    | `#fff4e5` | Warning background                 |
| Alert Success       | `#455326` | Success states                     |
| Alert Success Bg    | `#f1f3eb` | Success background                 |
| Alert Info          | `#0066cc` | Info states (verify in palette)    |

## Technical Approach

### Theme Type (Phased Approach)
**v1.0 - Light Theme Only:**
- **PolicyMe Light** - Primary theme matching webapp aesthetic
- Ship faster, validate color mappings and syntax highlighting with team

**v1.1 - Add Dark Theme:**
- **PolicyMe Dark** - Dark variant for developer preference
- Derive dark variants once light theme colors/contrast are proven
- ~60% of developers prefer dark themes, so this is a fast-follow priority

### Extension Structure
```
policyme-vscode-theme/
  package.json              # Extension manifest
  README.md                 # Installation instructions
  CHANGELOG.md              # Version history
  LICENSE                   # MIT license
  themes/
    policyme-light-color-theme.json
    policyme-dark-color-theme.json  # Added in v1.1
  images/
    icon.png                # 128x128 extension icon
```

### package.json Manifest (v1.0)
```json
{
  "name": "policyme-theme",
  "displayName": "PolicyMe Theme",
  "description": "PolicyMe brand colors for VS Code and Cursor",
  "version": "1.0.0",
  "publisher": "policyme",
  "engines": { "vscode": "^1.60.0" },
  "categories": ["Themes"],
  "contributes": {
    "themes": [
      {
        "label": "PolicyMe Light",
        "uiTheme": "vs",
        "path": "./themes/policyme-light-color-theme.json"
      }
    ]
  }
}
```
*Dark theme entry added in v1.1 once light theme is validated.*

### Key Workbench Colors to Customize
Priority color keys from VS Code theme-color reference:

**Editor:**
- `editor.background`, `editor.foreground`
- `editor.selectionBackground`, `editor.selectionHighlightBackground`
- `editor.lineHighlightBackground`
- `editorCursor.foreground`

**Activity Bar:**
- `activityBar.background`, `activityBar.foreground`
- `activityBarBadge.background`, `activityBarBadge.foreground`
- `activityBar.activeBorder`

**Side Bar:**
- `sideBar.background`, `sideBar.foreground`
- `sideBarTitle.foreground`
- `sideBarSectionHeader.background`

**Status Bar:**
- `statusBar.background`, `statusBar.foreground`
- `statusBarItem.remoteBackground`

**Title Bar:**
- `titleBar.activeBackground`, `titleBar.activeForeground`

**Tabs:**
- `tab.activeBackground`, `tab.activeForeground`
- `tab.inactiveBackground`, `tab.activeBorder`

**Terminal:**
- `terminal.background`, `terminal.foreground`
- ANSI color mappings

**Lists/Trees:**
- `list.activeSelectionBackground`
- `list.hoverBackground`

**Buttons/Inputs:**
- `button.background`, `button.foreground`
- `input.background`, `input.border`

### TextMate Token Colors (Syntax Highlighting)
Define `tokenColors` array for syntax highlighting (TextMate grammar scopes):

| TextMate Scope        | Light Theme | Dark Theme (v1.1) |
| --------------------- | ----------- | ----------------- |
| `comment`             | `#656a59`   | `#7d8571`         |
| `string`              | `#455326`   | `#8fb339`         |
| `keyword`             | `#a84300`   | `#ffb850`         |
| `entity.name.function`| `#455326`   | `#9ec46a`         |
| `variable`            | `#30332a`   | `#d4d4d4`         |
| `entity.name.type`    | `#803503`   | `#deb887`         |
| `constant.numeric`    | `#455326`   | `#b5cea8`         |
| `keyword.operator`    | `#656a59`   | `#9d9d9d`         |

**Note:** These are TextMate `tokenColors`, not VS Code semantic tokens (`semanticTokenColors`). Semantic token support can be added later for enhanced TypeScript/JavaScript highlighting.

## Implementation Steps

### v1.0 Milestones

**Phase 1: Setup**
1. Create extension directory structure
2. Initialize `package.json` with theme contribution points
3. Generate extension icon from PolicyMe logo

**Phase 2: Light Theme**
1. Create `policyme-light-color-theme.json`
2. Map PolicyMe rebrand colors to VS Code workbench colors
3. Map alert/error colors (`#db2200`, etc.) to diagnostic/diff colors
4. Define TextMate `tokenColors` for syntax highlighting
5. Test in Extension Development Host (F5)

**Phase 3: Validation & Distribution**
1. Test across file types (Python, TypeScript, JSON, YAML, Markdown)
2. Verify terminal colors, diff editor, git decorations
3. Package with `vsce package`
4. Distribute `.vsix` internally, gather team feedback

### v1.1 Milestones (Fast-Follow)

**Phase 4: Dark Theme**
1. Create `policyme-dark-color-theme.json`
2. Derive dark variants from rebrand palette
3. Ensure WCAG AA contrast compliance (4.5:1 for text)
4. Update `package.json` to include dark theme
5. Re-package and distribute

## Testing

### Local Development
```bash
# In extension directory
code --extensionDevelopmentPath=$(pwd)
```
Or press F5 in VS Code to launch Extension Development Host.

### Files to Test
- Python: `.py` files from our codebase
- TypeScript/JavaScript: `.ts`, `.tsx`, `.js`
- JSON/YAML: Config files
- Markdown: README files
- Shell scripts

### Cursor Compatibility
Cursor inherits VS Code's theming capabilities. Install `.vsix` via:
1. **Drag-and-drop**: Drag `.vsix` file into the Extensions pane ([Cursor docs](https://cursor.fan/tutorial/HowTo/managing-extensions-in-cursor))
2. **Command Palette**: `Cmd/Ctrl+Shift+P` → "Extensions: Install from VSIX..."
3. Select the packaged `.vsix` file

*Note: `cursor --install-extension` CLI flag is not officially documented; use the methods above.*

## Distribution Options

### Option 1: Internal VSIX (Recommended)
```bash
npm install -g @vscode/vsce
vsce package
# Produces policyme-theme-1.0.0.vsix
```
Share `.vsix` via internal channels.

**VS Code install:**
```bash
code --install-extension policyme-theme-1.0.0.vsix
```

**Cursor install:**
- Drag `.vsix` into Extensions pane, OR
- Command Palette → "Extensions: Install from VSIX..."

### Option 2: Private NPM Registry
Publish to internal registry if available.

### Option 3: Git Repository
Clone and symlink:
```bash
git clone <repo> ~/.vscode/extensions/policyme-theme
```

## Dependencies

**Development:**
- Node.js 20+ (required by `@vscode/vsce` per [package requirements](https://www.npmjs.com/package/@vscode/vsce))
- `@vscode/vsce` (packaging tool)

**Optional:**
- `yo generator-code` (scaffolding, not required for theme-only extensions)

## References

| Resource                      | URL                                                                            |
| ----------------------------- | ------------------------------------------------------------------------------ |
| VS Code Color Theme Guide     | https://code.visualstudio.com/api/extension-guides/color-theme                 |
| VS Code Theme Color Reference | https://code.visualstudio.com/api/references/theme-color                       |
| VS Code Extension Manifest    | https://code.visualstudio.com/api/references/extension-manifest                |
| VS Code Theming Overview      | https://code.visualstudio.com/api/extension-capabilities/theming               |
| Cursor Themes Documentation   | https://docs.cursor.com/configuration/themes                                   |
| Cursor Extensions Management  | https://docs.cursor.com/configuration/extensions                               |
| VSCE Publishing Tool          | https://code.visualstudio.com/api/working-with-extensions/publishing-extension |
| @vscode/vsce npm package      | https://www.npmjs.com/package/@vscode/vsce                                     |
| PolicyMe Design System        | `global-libjs-designsystem/src/palettes.ts`                                    |

## Notes

- Cursor inherits VS Code's theming capabilities; no Cursor-specific modifications needed for themes
- Theme extensions are the simplest extension type - no TypeScript compilation required
- The `-color-theme.json` suffix enables VS Code editor features (color pickers, hover hints)
- Semantic token highlighting (`semanticTokenColors`) can be added later for enhanced TS/JS support (available since VS Code 1.43)

## Risks / Considerations

1. **Dark theme derivation (v1.1)**: The rebrand palette is light-focused; dark variants need careful contrast tuning - mitigated by phased approach
2. **Terminal colors**: ANSI color mappings may need adjustment for readability
3. **Diff/merge colors**: Test with actual git operations to verify visibility
4. **Team adoption**: Include installation in onboarding docs for new devs
5. **Cursor extension compatibility**: While themes specifically work, Cursor docs note not all VS Code extensions may work identically due to verification and AI integration differences
