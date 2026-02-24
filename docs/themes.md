# Themes

## How the Theme System Works

Themes in plantUML-components follow a two-layer architecture:

1. **Color Scheme** (`style/colorScheme/*.iuml`) - Defines color variables
2. **Layout** (`style/layout/lucid-style.iuml`) - Consumes color variables to apply comprehensive skinparam and `<style>` settings

Each theme file (`style/theme/*.iuml`) simply includes both layers:

```plantuml
!include ../colorScheme/ocean-blue.iuml
!include ../layout/lucid-style.iuml
```

## Color Variables

Every color scheme defines these variables, which the layout consumes:

| Variable | Description |
|----------|-------------|
| `$PRIMARY` | Primary color for borders, arrows, and emphasis |
| `$SECONDARY` | Secondary color for backgrounds and accents |
| `$LIGHT` | Light utility color |
| `$DARK` | Dark utility color |
| `$SUCCESS` | Success/positive color (green tones) |
| `$INFO` | Informational color |
| `$WARNING` | Warning color (orange tones) |
| `$DANGER` | Danger/error color (red tones) |
| `$BACKGROUND` | Diagram background |
| `$FOREGROUND` | Element foreground/fill color |
| `$LIGHTEN_DARKEN_FACTOR` | Amount to lighten/darken derived colors (default: 20) |
| `$TRANSPARENCY_LEVEL` | Transparency suffix for semi-transparent colors (default: 90) |

### Derived Variables

These are computed automatically from the base variables:

| Variable | Derivation |
|----------|-----------|
| `$PRIMARY_LIGHT` | `%lighten($PRIMARY, $LIGHTEN_DARKEN_FACTOR)` |
| `$PRIMARY_DARK` | `%darken($PRIMARY, $LIGHTEN_DARKEN_FACTOR)` |
| `$PRIMARY_TEXT` | Text color on primary backgrounds |
| `$SECONDARY_LIGHT` | `%lighten($SECONDARY, $LIGHTEN_DARKEN_FACTOR)` |
| `$SECONDARY_DARK` | `%darken($SECONDARY, $LIGHTEN_DARKEN_FACTOR)` |
| `$SECONDARY_TEXT` | Text color on secondary backgrounds |
| `$INFO_LIGHT` | Lightened info color |
| `$INFO_TEXT` | Text color for info elements |
| `$SUCCESS_LIGHT` | Lightened success color |
| `$SUCCESS_TEXT` | Text color for success elements |
| `$WARNING_LIGHT` | Lightened warning color |
| `$WARNING_TEXT` | Text color for warning elements |
| `$DANGER_LIGHT` | Lightened danger color |
| `$DANGER_TEXT` | Text color for danger elements |
| `$ARROW` | Arrow color (typically `$PRIMARY_DARK`) |
| `$BOX_BACKGROUND` | Sequence box background |
| `$PARTICIPANT_BACKGROUND` | Sequence participant background |

## Built-in Themes

### Ocean Blue

Light theme with blue primary color (`#4881b3`) and white backgrounds.

```plantuml
!include $COMPONENTS_PUML/style/theme/ocean-blue-theme.iuml
```

### Black & White

Monochrome theme with black primary and white secondary, transparent backgrounds.

```plantuml
!include $COMPONENTS_PUML/style/theme/black-white-theme.iuml
```

### Mermaid Dark

Dark theme inspired by Mermaid.js dark mode. Blue accent (`#81B1DB`) on dark backgrounds (`#2A303C`).

```plantuml
!include $COMPONENTS_PUML/style/theme/mermaid-dark-theme.iuml
```

### Random

Generates all colors randomly using HSL. Every render produces a unique color scheme.

```plantuml
!include $COMPONENTS_PUML/style/theme/random-theme.iuml
```

## Creating a Custom Theme

1. Create a new color scheme file at `dist/style/colorScheme/my-theme.iuml`
2. Define all required color variables (see table above)
3. Create a theme file at `dist/style/theme/my-theme-theme.iuml`:

```plantuml
!include ../colorScheme/my-theme.iuml
!include ../layout/lucid-style.iuml
```

### Debugging Colors

Include the color logging utility to print all resolved color values:

```plantuml
!include $COMPONENTS_PUML/style/colorScheme/my-theme.iuml
!include $COMPONENTS_PUML/style/colorScheme/color_logging.iuml
```

This logs all variable values via `!log` during rendering.
