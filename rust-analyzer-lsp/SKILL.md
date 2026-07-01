---
name: rust-analyzer-lsp
description: Configure and use rust-analyzer language-server workflows for Rust diagnostics, symbol navigation, and refactor-safe code editing.
license: MIT
metadata:
  repository: https://github.com/odinlayer/ai-skills/tree/main/rust-analyzer-lsp
  compatibility: Pi skill format; Rust projects with local shell access.
---

# Rust Analyzer LSP

Use this skill for `.rs` projects when you need language-aware editing and diagnostics.

## Setup

Install rust-analyzer with one of:

- `rustup component add rust-analyzer` (recommended)
- `brew install rust-analyzer` (macOS)
- `sudo apt install rust-analyzer` (Ubuntu/Debian)

Verify:

- `rust-analyzer --version`

## Usage Guidance

- Use LSP diagnostics before large refactors.
- Prefer symbol references/rename flows over manual search-replace.
- Validate changes with:
  - `cargo fmt`
  - `cargo clippy --all-targets --all-features`
  - `cargo test`

## Fallback

If LSP is unavailable, rely on `cargo check`, `clippy`, and tests before merge.
