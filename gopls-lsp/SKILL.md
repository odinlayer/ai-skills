---
name: gopls-lsp
description: Configure and use Go language-server workflows (gopls) for navigation, diagnostics, refactors, and symbol-level code understanding in Go repositories.
license: MIT
metadata:
  repository: https://github.com/odinlayer/ai-skills/tree/main/gopls-lsp
  compatibility: Pi skill format; Go projects with local shell access.
---

# gopls LSP

Use this skill for `.go` projects when you need reliable language-intelligence support.

## Setup

1. Install:
   - `go install golang.org/x/tools/gopls@latest`
2. Ensure `$GOPATH/bin` or `$HOME/go/bin` is in `PATH`.
3. Verify:
   - `gopls version`

## Usage Guidance

- Prefer language-server diagnostics over ad hoc grep for symbol questions.
- Use LSP-backed navigation for definitions, references, and rename planning.
- Re-run `go test ./...` after structural edits.

## Fallback

If language-server support is unavailable, fall back to:

- `go fmt ./...`
- `go vet ./...`
- `go test ./...`
