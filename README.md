# plantUML-components

A PlantUML library providing reusable themes, functional macros, and 3rd-party icon wrappers for building consistent, professional diagrams.

## Quick Start

Add these lines to the top of your `.puml` file:

```plantuml
@startuml

!$COMPONENTS_PUML = "https://raw.githubusercontent.com/segFallt/plantUML-components/v2.0.1/dist"
!include $COMPONENTS_PUML/Common.iuml
!include $COMPONENTS_PUML/style/theme/ocean-blue-theme.iuml
!include $COMPONENTS_PUML/functional/sequence/commonSequenceFunctions.iuml

$setAutoNumber()
$addParticipant(Alice, "Alice")
$addParticipant(Bob, "Bob")

Alice -> Bob: Hello
Alice <-- Bob: Hi

@enduml
```

## Available Themes

| Theme | Include Path | Description |
|-------|-------------|-------------|
| Ocean Blue | `style/theme/ocean-blue-theme.iuml` | Blue tones with light backgrounds |
| Black & White | `style/theme/black-white-theme.iuml` | Clean monochrome palette |
| Mermaid Dark | `style/theme/mermaid-dark-theme.iuml` | Dark theme with blue accents |
| Random | `style/theme/random-theme.iuml` | Randomly generated colors using HSL |

Each theme combines a color scheme (`style/colorScheme/`) with a layout (`style/layout/lucid-style.iuml`). See [docs/themes.md](docs/themes.md) for details.

## Functional Macros

| Module | Include Path | Description |
|--------|-------------|-------------|
| Sequence | `functional/sequence/commonSequenceFunctions.iuml` | Auto-numbering, participant management, message sizing |
| Array | `functional/data/array.iuml` | Variable array utilities for dynamic data |
| Class | `functional/class/commonClassFunctions.iuml` | Schema, table, view, primary/foreign key helpers |
| Relational | `functional/relational/relationalDataCommonFunctions.iuml` | Empty namespace display control |
| Spacer | `functional/layout/spacer.iuml` | Invisible layout spacers for diagram alignment |

See [docs/functional-macros.md](docs/functional-macros.md) for usage details.

## 3rd-Party Integrations

| Integration | Include Path | Upstream Version |
|------------|-------------|-----------------|
| AWS (v14) | `3rdParty/aws14/AwsCommon.iuml` | aws-icons-for-plantuml v14.0 |
| AWS (v11) | `3rdParty/aws/AwsCommon.iuml` | aws-icons-for-plantuml v11.1 |
| Azure 2.1 | `3rdParty/azure2.1/azureCommon.iuml` | Azure-PlantUML release/2-1 |
| Kubernetes | `3rdParty/kubernetes/KubernetesCommon.iuml` | Custom sprites |
| PingIdentity | `3rdParty/pingIdentity/pingIdentityStyleAndComponents.iuml` | Custom sprites |
| OAuth2 Auth | `3rdParty/auth.iuml` | Auth flow sequence macros |

See [docs/3rdparty-integrations.md](docs/3rdparty-integrations.md) for details.

## Directory Structure

```
dist/
  Common.iuml                    # Entry point with version
  style/
    colorScheme/                  # Color variable definitions
    layout/                       # Layout/skinparam definitions
    theme/                        # Combined color + layout themes
  functional/
    data/                         # Array utilities
    sequence/                     # Sequence diagram helpers
    class/                        # Class/ER diagram helpers
    relational/                   # Relational data helpers
    layout/                       # Layout spacer utilities
  3rdParty/
    auth.iuml                     # OAuth2 auth flow macros
    aws/                          # AWS v11.1 wrappers
    aws11/                        # AWS v11.1 wrappers (alias)
    aws14/                        # AWS v14.0 wrappers
    azure2.1/                     # Azure 2.1 wrappers
    kubernetes/                   # Kubernetes icon wrappers
    pingIdentity/                 # PingIdentity icon wrappers
examples/
  sequence/                       # Sequence diagram examples
  aws/                            # AWS architecture examples
```

## Examples

See the [examples/](examples/) directory for working diagram files demonstrating each theme and integration.

## Contributing

See [docs/contributing.md](docs/contributing.md) for guidelines on adding themes, macros, and integrations.

## Versioning

This project uses [Semantic Versioning](https://semver.org/). The current version is defined in `VERSION` and `dist/Common.iuml`.

Pin your includes to a specific release tag (e.g., `v2.0.1`) to avoid breaking changes:

```plantuml
!$COMPONENTS_PUML = "https://raw.githubusercontent.com/segFallt/plantUML-components/v2.0.1/dist"
```
