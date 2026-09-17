# RAG MCP servers

This repository is the collection point for independent MCP servers built
around UltraRAG. Each server lives in its own Git repository and is included
here as a Git submodule pinned to a specific, tested commit.

## Included servers

| Server | Use it when you need |
|---|---|
| [`vanilla-ultra-rag-mcp-server`](vanilla-ultra-rag-mcp-server/) | Direct MCP access to UltraRAG's existing tools and prompts, with minimal gateway code and no UltraRAG source modifications. |
| [`research-ultra-rag-mcp-server`](research-ultra-rag-mcp-server/) | A project-isolated PDF/EPUB research workflow with simple agent tools, provenance, locators, metadata, and CPU BM25 retrieval. |

The servers remain independently installable and versioned. Follow the README
inside the selected submodule for installation, MCP client configuration, and
usage instructions.

## Clone the complete collection

```bash
git clone --recurse-submodules https://github.com/AhmedKishki/rag-mcp-servers.git
cd rag-mcp-servers
```

If you already cloned without submodules, initialize them with:

```bash
git submodule update --init --recursive
```

## Pull collection updates

```bash
git pull --ff-only
git submodule update --init --recursive
```

The parent repository deliberately pins each submodule to an exact commit.
Updating the parent therefore reproduces the selected server versions instead
of silently taking newer child commits.

## Work on one server

Treat each submodule as its own project. Commit and push changes from inside
that server first. Then record the new child commit in this collection:

```bash
git -C research-ultra-rag-mcp-server switch main
git -C research-ultra-rag-mcp-server pull --ff-only origin main
git add research-ultra-rag-mcp-server
git commit -m "Update research MCP server"
git push
```

Use the equivalent commands for `vanilla-ultra-rag-mcp-server` when updating
the vanilla server.
