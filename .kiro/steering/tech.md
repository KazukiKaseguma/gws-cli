# Technology Stack

## Architecture

A two-phase parsing CLI. Phase 1 identifies the target service (e.g., `drive`) and fetches its Discovery Document (cached for 24h). Phase 2 dynamically builds a `clap::Command` tree from the document's resources and methods to execute the request.

## Core Technologies

- **Language**: Rust (CLI Core), TypeScript/Markdown (Agent Skills)
- **Framework**: `clap` for CLI parsing, `tokio` for async runtime
- **Runtime**: Node.js 18+ (for distribution/packaging), Rust (native execution)

## Key Libraries

- **Rust**: `clap` (CLI), `serde` (JSON), `reqwest` (HTTP), `dotenvy` (env vars)
- **API**: Google Workspace Discovery Service

## Development Standards

### Type Safety
- **Rust**: Strict ownership and type system. Use `anyhow` for error handling and `serde` for robust JSON modeling.

### Code Quality
- **Linting**: `cargo clippy -- -D warnings`
- **Formatting**: `rustfmt`

### Testing
- **Unit Tests**: `cargo test`
- **Integration**: Helper scripts for coverage (e.g., `./scripts/coverage.sh`)

## Development Environment

### Required Tools
- Rust (latest stable)
- pnpm (for Node.js/Skills management)

### Common Commands
```bash
# Dev Build
cargo build

# Test
cargo test

# Lint
cargo clippy

# Install all skills
npx skills add https://github.com/googleworkspace/cli
```

## Key Technical Decisions

- **Dynamic Discovery**: Opted for runtime schema fetching over static generation to ensure 100% API coverage without manual updates.
- **Structured JSON Output**: All commands output JSON by default to ensure interoperability with AI agents and scripts.
- **Hybrid Distribution**: Core is high-performance Rust, distributed via npm wrapper for ease of installation.

---
_Document standards and patterns, not every dependency_
