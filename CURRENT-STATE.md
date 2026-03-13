# CURRENT-STATE

This file captures the current working state of the `RAIkeep` umbrella workspace so a future session can resume quickly.

## Role of this repo

`RAIkeep` is the umbrella workspace for the related C# libraries:

- `JsonPit`
- `OsLib`
- `RaiUtils`
- `RaiImage`

The intent is to keep package repos independent while using `RAIkeep` as the cross-library integration workspace.

## Verified baseline

The umbrella solution baseline was verified successfully.

Command:

```bash
dotnet test RAIkeep.slnx
```

Verified result at the time of this note:

- total: 149
- failed: 0
- succeeded: 144
- skipped: 5

## Current aligned package version

The workspace is currently aligned on version `3.3.0` for:

- `JsonPit`
- `OsLib`
- `RaiUtils`
- `RaiImage`

## Solution structure

`RAIkeep.slnx` includes:

- `JsonPit/JsonPit.csproj`
- `JsonPit/JsonPit.Tests/JsonPit.Tests.csproj`
- `OsLib/OsLib.csproj`
- `OsLib/OsLib.Tests/OsLib.Tests.csproj`
- `RaiUtils/RaiUtils.csproj`
- `RaiUtils/tests/RaiUtils.Tests/RaiUtils.Tests.csproj`
- `RaiImage/RaiImage.csproj`
- `RaiImage/RaiImage.Tests/RaiImage.Tests.csproj`

The missing OsLib and RaiUtils test projects were added to the umbrella solution during this session.

## JsonPit.Tests sunset

Decision:

- package-owned JsonPit tests now live in the `JsonPit` repo
- the separate `JsonPit.Tests` repository is being sunset and archived

Status:

- the standalone `JsonPit.Tests` README was updated with an archival notice
- the archival notice points to `JsonPit` for package tests and `RAIkeep` for integration work

Recommended GitHub sequence:

1. Commit and push the archival README change in `JsonPit.Tests`
2. Archive the `JsonPit.Tests` GitHub repository
3. Keep it archived for historical reference instead of deleting it immediately

## Rename direction

Decision:

- the parent umbrella repo is intended to be `RAIkeep`
- renaming from `JsonPitSolution` to `RAIkeep` makes architectural sense now that the repo truly acts as the umbrella workspace

Recommended sequence:

1. Push child repo changes first if submodule SHAs changed
2. Push the umbrella repo changes last
3. Rename the GitHub repo from `JsonPitSolution` to `RAIkeep`
4. Update local `origin` URL after the rename

## PlantUML artifacts added or updated

At the `RAIkeep` root:

- `RAIkeep-Package-Dependencies.puml`
- `RAIkeep-Library-Dependencies.puml`

Under `OsLib`:

- `Os-ClassDiagram.puml`

## PlantUML conventions established in this session

For package layout:

- hidden `right` links are useful for defining columns
- hidden `down` links are useful for defining rows
- `..[norank]>` helps keep visible dependency arrows from dominating layout

For built-in UML icons:

- `show circle` restores class and enum header icons
- `hide circle` removes those header icons
- `classAttributeIconSize` controls the visibility size of member glyphs

For static members:

- explicit `Ⓢ` markers work well in class diagrams

For package/member text diagrams:

- `Ⓒ` was used for production-class markers
- `Ⓣ` was used for test-class markers

## Important files

- `RAIkeep.slnx`
- `README.md`
- `.gitmodules`
- `RAIkeep-Package-Dependencies.puml`
- `RAIkeep-Library-Dependencies.puml`
- `OsLib/Os-ClassDiagram.puml`

## Suggested prompt for a future session

```text
Please read CURRENT-STATE.md in the RAIkeep repo root first, then continue from there.
```