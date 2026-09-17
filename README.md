# RAG MCP servers

This repository is the collection point for independent MCP servers built
around UltraRAG. Each server lives in its own Git repository and is included
here as a Git submodule pinned to a specific, tested commit.

## Credit to UltraRAG

Both servers are directly based on
[`OpenBMB/UltraRAG`](https://github.com/OpenBMB/UltraRAG). UltraRAG's upstream
team describes it as a joint project of
[`THUNLP`](https://nlp.csai.tsinghua.edu.cn/) at Tsinghua University,
[`NEUIR`](https://neuir.github.io/) at Northeastern University,
[`OpenBMB`](https://www.openbmb.cn/home), and
[`AI9stars`](https://github.com/AI9Stars), together with the
[`UltraRAG contributors`](https://github.com/OpenBMB/UltraRAG/graphs/contributors).
Their work provides the MCP architecture and RAG implementation underlying this
collection.

UltraRAG is licensed under the
[`Apache License 2.0`](https://github.com/OpenBMB/UltraRAG/blob/main/LICENSE.txt).
These are independent projects, not official UltraRAG releases, and are not
affiliated with or endorsed by the upstream organizations. See [`NOTICE`](NOTICE)
and the notice inside each server repository for version-specific attribution.

## Included servers

| Server | Use it when you need |
|---|---|
| [`vanilla-ultra-rag-mcp-server`](vanilla-ultra-rag-mcp-server/) | UltraRAG's existing Vanilla RAG stages—retrieval, RAG prompt, generation, extraction, and evaluation—with minimal gateway code and no UltraRAG source modifications. |
| [`research-ultra-rag-mcp-server`](research-ultra-rag-mcp-server/) | A research adaptation with project-isolated PDF/EPUB ingestion, UltraRAG BM25 + project-local Qdrant hybrid retrieval, optional CPU reranking, metadata, provenance, and locators; the connected agent generates from returned evidence. |

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
