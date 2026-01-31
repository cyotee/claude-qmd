# QMD - Query Markdown Documents

```
    ╭──────────────╮
    │  🔍  QMD     │
    │  ═══════════ │
    │  LOCAL       │
    │  SEMANTIC    │
    │  SEARCH      │
    ╰──────────────╯
```

Your on-device search engine for everything you need to remember.

---

## What This Is

QMD indexes markdown files and makes them searchable through:
- **BM25** - Fast keyword matching
- **Vector search** - Semantic similarity via embeddings
- **Hybrid** - Both combined with LLM reranking

All processing happens locally. No data leaves your machine.

## MCP Tools Available

When the QMD MCP server is running, you have access to:

| Tool | Purpose |
|------|---------|
| `qmd_search` | BM25 keyword search |
| `qmd_vsearch` | Vector semantic search |
| `qmd_query` | Hybrid search with reranking |

## Standard Collections

This plugin maintains these collections:

| Collection | Contents | Glob Pattern |
|------------|----------|--------------|
| `plugins` | All installed plugin docs | `~/.claude/plugins/**/*.md` |
| `protocols` | DeFi protocol skills | `~/.claude/plugins/**/skills/**/*.md` |
| `project` | Current project docs | `./**/*.md` |
| `claude-md` | All CLAUDE.md files | `**/CLAUDE.md` |

## When to Use QMD

**Use qmd_query for:**
- "How do I do X in protocol Y?" → searches protocol skills
- "What commands are available for Z?" → searches plugin docs
- Cross-protocol patterns → "liquidation mechanisms across protocols"

**Use qmd_search for:**
- Exact function names or error messages
- Specific keywords you know exist

**Use qmd_vsearch for:**
- Conceptual questions
- Finding related documentation

## Automatic Behavior

The context-retrieval skill should:
1. Before complex tasks, search for relevant context
2. On protocol questions, query the `protocols` collection
3. On plugin questions, query the `plugins` collection

## Keep Index Fresh

```bash
# Re-index after plugin updates
qmd index plugins --path ~/.claude/plugins --pattern "**/*.md"

# Re-index current project
qmd index project --path . --pattern "**/*.md"
```

---

*Search everything. Remember nothing.*
