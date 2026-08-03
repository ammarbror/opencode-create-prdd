# opencode-create-prdd

A shareable [opencode](https://opencode.ai) slash command that creates a **bilingual Product Requirements & Design Document (PRDD)** — Bahasa Indonesia + English — directly into your Obsidian vault.

It walks you through a **9-section interview** (one section per turn), then writes two files:

- `PRDD - <Name> (ID).md` — Bahasa Indonesia
- `PRDD - <Name> (EN).md` — English

...under `01 Projects/PRDs/<Project>/` in your vault, and appends the new document to the `Daftar PRDD.md` index.

## What it covers

| # | Section | Type |
|---|---------|------|
| 1 | Overview & Problem Statement | PRD |
| 2 | Goals & Success Metrics (+ Non-Goals) | PRD |
| 3 | User Stories / Use Cases | PRD |
| 4 | Functional Requirements (MoSCoW P0/P1/P2) | PRD |
| 5 | System Architecture (Mermaid flowchart) | Tech Doc |
| 6 | Database Schema / ERD (Mermaid erDiagram) | Tech Doc |
| 7 | API Contract (Mermaid sequenceDiagram) | Tech Doc |
| 8 | Non-Functional Requirements | Tech Doc |
| 9 | Dependencies & Risks | Both |

All diagrams are Mermaid, rendered inside Obsidian code fences.

## Requirements

- [opencode](https://opencode.ai) (this is an opencode command)
- An Obsidian vault (path is configurable, see below)

## Installation

### Option A — Global (available in every project)

Copy the command file into your global opencode commands directory:

```sh
mkdir -p ~/.config/opencode/command
cp .opencode/command/create-prdd.md ~/.config/opencode/command/create-prdd.md
```

Restart opencode, then run `/create-prdd [Product Name]`.

### Option B — Per-project

Either clone this repo and run opencode from inside it, or copy the file into your project:

```sh
mkdir -p .opencode/command
cp .opencode/command/create-prdd.md .opencode/command/create-prdd.md
```

## Configuration

The command writes into an Obsidian vault at a **hardcoded path**:

```markdown
VAULT = /Users/ammarbror/Documents/Obsidian Vault
```

To point it at your own vault, edit `.opencode/command/create-prdd.md` and change that `VAULT` constant in the **Save Flow** section (search for `VAULT =`). Everything else works out of the box.

## Usage

```
/create-prdd MyApp
```

Or run `/create-prdd` with no arguments and the command will ask for the product name first. During the interview, answer briefly per section — or type `TBD` to leave a section open. If a section doesn't apply (e.g. no database), answer `N/A`.

## Notes

- Old PRDs already in `01 Projects/PRDs/*` are left untouched — they are not migrated to the PRDD format.
- File names keep the original product name (with spaces, original case); only the folder name is sanitized (lowercase, hyphenated).
- After installing or editing the command, **restart opencode** for changes to take effect.
