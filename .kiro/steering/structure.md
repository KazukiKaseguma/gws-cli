# Project Structure

## Organization Philosophy

Monorepo architecture separating the high-performance CLI core (Rust) from extensible agent-specific workflows (Skills).

## Directory Patterns

### Rust Crates
**Location**: `/crates/`  
**Purpose**: Core logic of the CLI and Google Workspace library.  
**Example**: `crates/google-workspace-cli` (Entry point), `crates/google-workspace` (Library).

### Agent Skills
**Location**: `/skills/`  
**Purpose**: Individual "Agent Skills" defined in `SKILL.md` for specific APIs or recipes.  
**Example**: `skills/gws-drive/SKILL.md`

### Distribution Wrapper
**Location**: `/npm/`  
**Purpose**: Node.js scripts for binary distribution via npm.  
**Example**: `npm/install.js`, `npm/run.js`.

### Maintenance Scripts
**Location**: `/scripts/`  
**Purpose**: Shell scripts for CI/CD, versioning, and coverage.  
**Example**: `scripts/coverage.sh`.

## Naming Conventions

- **Rust Files/Modules**: `snake_case` (standard Rust convention).
- **CLI Commands**: `kebab-case` for methods mapped from Discovery Service.
- **Helper Commands**: `+kebab-case` (e.g., `+send`, `+agenda`) to distinguish hand-crafted helpers from dynamic API methods.
- **Skills**: `gws-[service-name]` or `recipe-[task-name]`.

## Code Organization Principles

- **Discovery First**: Prefer dynamic schema mapping over hard-coded command logic.
- **JSON Standard**: All successful outputs and error messages must be structured JSON.
- **Modular Skills**: Keep agent skills self-contained in their respective directories.

---
_Document patterns, not file trees. New files following patterns shouldn't require updates_
