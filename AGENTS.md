# AGENTS.md

This is a collection repository. Its two implementation directories are Git
submodules and independent projects:

- `vanilla-ultra-rag-mcp-server/`
- `research-ultra-rag-mcp-server/`

## Working rules

- Retain the prominent UltraRAG acknowledgement in `README.md`, the root
  `NOTICE`, upstream project links, license information, and independent-project
  disclaimer. Do not imply upstream endorsement.
- Read the selected submodule's own `AGENTS.md` before changing its code.
- Make, test, commit, and push implementation changes inside the child
  repository first.
- Update a submodule pointer here only after its referenced commit is available
  from the child's remote repository.
- Do not duplicate child source files in the parent or couple their release
  histories.
- Keep the parent limited to collection-level documentation, automation, and
  pinned submodule references.
- Do not edit `.gitmodules` casually; the canonical child remotes are the
  AhmedKishki GitHub repositories named above.

## Validation

Before committing a collection change, run:

```bash
git submodule status --recursive
git -C vanilla-ultra-rag-mcp-server status --short --branch
git -C research-ultra-rag-mcp-server status --short --branch
git diff --check
```

A leading `-` in `git submodule status` means a child is not initialized. A
leading `+` means the checked-out child commit differs from the commit recorded
by the parent.
