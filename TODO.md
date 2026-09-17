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

## `memory-ultra-rag-mcp-server`

Status: concept agreed; detailed design and implementation deferred until
explicitly requested.

- Create an independent, project-scoped stdio MCP server for durable human and
  agent working memory.
- First evaluate UltraRAG's existing memory server and expose its unmodified
  behavior where it already satisfies the contract. Keep any necessary adapter
  code outside the UltraRAG source tree.
- Do not depend on `research-ultra-rag-mcp-server`, its tools, or its private
  storage. The memory server must install and operate on its own.
- Store all derived state beneath each project's `.ultrarag/memory/` directory
  and prevent implicit cross-project retrieval.
- Distinguish durable notes, interpretations, decisions, open questions, and
  project terminology from transient client-owned conversation context.
- Require an explicit MCP write call before anything becomes durable; never
  save ordinary conversations silently.
- Record author or origin, creation and edit times, memory type, tags, and any
  user-supplied evidence references.
- Treat evidence references as provenance links, not as proof that a memory is
  a source. Never present or cite remembered text as PDF/EPUB evidence.
- Expose focused tools for status, create, search, list, retrieve, update, and
  delete operations. Make deletion and editing transparent to the user.
- Default to CPU-only local retrieval and avoid a required external database
  service. Decide lexical, dense, or hybrid retrieval only after evaluation.
- Give the repository its own user README, agent guide, engineering contract,
  storage documentation, tests, and versioning before adding it to this
  collection's README.
