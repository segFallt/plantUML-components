# Contributing

## Project Structure

All library files live under `dist/`. Examples go in `examples/`. Documentation goes in `docs/`.

```
dist/
  style/colorScheme/     # Color variable definitions
  style/layout/          # Layout skinparam definitions
  style/theme/           # Combined theme files
  functional/            # Macro modules
  3rdParty/              # 3rd-party icon wrappers
examples/
  sequence/              # Sequence diagram examples
  aws/                   # AWS architecture examples
docs/                    # Documentation
```

## Adding a Theme

1. Create a color scheme file at `dist/style/colorScheme/<name>.iuml`
   - Define all required color variables (`$PRIMARY`, `$SECONDARY`, `$LIGHT`, `$DARK`, `$SUCCESS`, `$INFO`, `$WARNING`, `$DANGER`, `$BACKGROUND`, `$FOREGROUND`, and all derived variables)
   - See existing color schemes for the full template
2. Create a theme file at `dist/style/theme/<name>-theme.iuml`:
   ```plantuml
   !include ../colorScheme/<name>.iuml
   !include ../layout/lucid-style.iuml
   ```
3. Add an example at `examples/sequence/sequence-using-<name>-theme.puml`
4. Update `README.md` and `docs/themes.md`

## Adding Functional Macros

1. Create or update a `.iuml` file under the appropriate `dist/functional/` subdirectory
2. Use relative includes for any internal dependencies (e.g., `../data/array.iuml`)
3. Document the procedures and functions in `docs/functional-macros.md`

## Adding a 3rd-Party Integration

1. Create a directory at `dist/3rdParty/<name>/`
2. Add an entry point `.iuml` file (e.g., `<Name>Common.iuml`)
3. Use relative includes for sibling files within the integration
4. For upstream sprites, include via full URL (pinned to a specific release tag)
5. Add an example under `examples/`
6. Document the integration in `docs/3rdparty-integrations.md`

## File Naming Conventions

- Color schemes: `dist/style/colorScheme/<name>.iuml` (lowercase, hyphenated)
- Themes: `dist/style/theme/<name>-theme.iuml`
- Library include files: `.iuml` extension
- Diagram files: `.puml` extension
- Library files must NOT contain `@startuml`/`@enduml` (they are included, not rendered directly)

## Pull Request Process

1. Create a feature branch from `main`
2. Make your changes in `dist/`
3. Add or update examples in `examples/`
4. Update documentation in `docs/` and `README.md`
5. Test locally: patch examples to use local `dist` paths and render with PlantUML
6. Open a PR against `main`
7. CI will validate the `dist/` structure and render all examples

## Versioning

- Version is tracked in `VERSION` (root) and `dist/Common.iuml`
- Both must be updated together when releasing a new version
- Follow [Semantic Versioning](https://semver.org/):
  - **Major**: Breaking changes to include paths or variable names
  - **Minor**: New themes, macros, or integrations
  - **Patch**: Bug fixes, documentation updates
