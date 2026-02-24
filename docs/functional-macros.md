# Functional Macros

## Sequence Diagram Functions

**File:** `dist/functional/sequence/commonSequenceFunctions.iuml`

Provides helper procedures for sequence diagrams. Automatically includes the array utility.

### Procedures

#### `$setAutoNumber($start, $increment)`

Enables auto-numbering on sequence messages.

- `$start` (default: `"1"`) - Starting number
- `$increment` (default: `"1"`) - Increment step

```plantuml
$setAutoNumber()
$setAutoNumber("10", "5")
```

#### `$setMaxMessageSize($size)`

Sets the maximum width of message labels before wrapping.

```plantuml
$setMaxMessageSize(200)
```

#### `$setTeoz()`

Enables the Teoz rendering engine (`!pragma teoz true`).

```plantuml
$setTeoz()
```

#### `$addParticipant($variable, $label)`

Declares a participant and registers it for label printing.

```plantuml
$addParticipant(Alice, "Alice")
$addParticipant(Bob, "Bob Service")
```

#### `$addSequenceMember($variable, $label, $memberType)`

Declares a sequence member of any type (participant, actor, boundary, etc.).

```plantuml
$addSequenceMember(User, "End User", actor)
$addSequenceMember(API, "API Gateway", participant)
```

#### `$printParticipantLabels()`

Prints floating labels over all registered participants.

```plantuml
$printParticipantLabels()
```

### Aliases

Pascal-case aliases are available: `AddParticipant()`, `AddSequenceMember()`, `PrintParticipantLabels()`.

---

## Array Utilities

**File:** `dist/functional/data/array.iuml`

Provides simulated array data structures using PlantUML variables. Used internally by the sequence functions.

### Functions and Procedures

#### `$addValueToArray($arrayName, $value)`

Appends a value to the named array.

#### `$getArrayValue($arrayName, $index)`

Returns the value at the given 1-based index.

#### `$getArrayIndexValue($arrayName)`

Returns the current length of the array.

---

## Class / ER Diagram Functions

**File:** `dist/functional/class/commonClassFunctions.iuml`

Provides procedures for building entity-relationship diagrams.

### Procedures

#### `$schema($name, $slug)`

Creates a package styled as a schema container.

```plantuml
$schema("public", public_schema)
```

#### `$table($name, $slug)`

Creates an entity styled as a database table with an orange `T` marker.

```plantuml
$table("users", users_table)
```

#### `$view($name, $slug)`

Creates an entity styled as a database view with an aquamarine `V` marker.

```plantuml
$view("active_users", active_users_view)
```

#### `$pk($name)`

Renders a primary key field with a gold key icon.

#### `$fk($name)`

Renders a foreign key field with a silver key icon.

#### `$column($name)`

Renders a regular column field.

### Example

```plantuml
$schema("public", public_schema) {
  $table("users", users) {
    $pk("id")
    $column("name")
    $fk("org_id")
  }
}
```

---

## Relational Data Functions

**File:** `dist/functional/relational/relationalDataCommonFunctions.iuml`

#### `$showEmptyNamespaces($show)`

Controls whether intermediate packages are displayed.

- `$show` (default: `"true"`) - `"true"` to show, `"false"` to hide

```plantuml
$showEmptyNamespaces("false")
```

---

## Layout Spacer

**File:** `dist/functional/layout/spacer.iuml`

Provides invisible spacer elements for controlling diagram layout.

### Procedures

#### `Spacer($alias, $count)`

Creates an invisible rectangle containing `$count` nested invisible rectangles for spacing.

#### `SpacerLink($spacer, $obj1, $obj2)`

Creates hidden links from `$obj1` through `$spacer` to `$obj2`.

#### `SpacerAndLink($alias, $count, $obj1, $obj2)`

Combines `Spacer` and `SpacerLink` in one call.

```plantuml
SpacerAndLink(mySpacer, 3, ComponentA, ComponentB)
```
