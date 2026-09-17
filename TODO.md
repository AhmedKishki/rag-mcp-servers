# TODO

## `embedded-c-ultra-rag-mcp-server`

Status: design agreed; implementation deferred until explicitly requested.

- Create an independent, project-scoped stdio MCP server for embedded C
  development.
- Use technical documentation and explicitly selected C reference code as its
  knowledge base; never execute ingested code.
- Initially support manuals, user guides, datasheets, HTML/Markdown reference
  documentation, and C source/header files.
- Treat vendor, product, document revision, protocol, language, and source type
  as filterable metadata.
- Treat registers, register fields, addresses or offsets, bit ranges, reset
  values, access modes, commands, constants, macros, and C symbols as structured
  entities tied to exact source evidence.
- Preserve PDF page/section/table locators and C file/line/symbol locators.
- Combine exact entity lookup, UltraRAG BM25, local Qdrant dense retrieval, and
  reciprocal-rank fusion; default to CPU-only operation with a future GPU path.
- Store generated state under each project's `.ultrarag/code/` directory and
  prevent cross-project retrieval.
- Expose focused tools for status, ingestion, search, register lookup, symbol
  lookup, evidence retrieval, source listing, and reviewed metadata.
- Keep UltraRAG unmodified and pin a verified upstream revision directly.
- Give the project a standalone user README and agent guidance. Add comparison
  text only to this collection after the server exists.

