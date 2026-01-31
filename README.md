# QMD Plugin for Claude Code

Local semantic search for your documentation, protocol skills, and project knowledge.

## What is QMD?

[QMD (Query Markdown Documents)](https://github.com/tobi/qmd) is an on-device search engine that indexes markdown files and makes them searchable through:

- **BM25** - Fast keyword matching
- **Vector search** - Semantic similarity via embeddings
- **Hybrid** - Both combined with LLM reranking

All processing happens locally using GGUF models. No data leaves your machine.

## Installation

### 1. Install QMD

```bash
bun install -g qmd
```

### 2. Install this plugin

```bash
claude plugins add cyotee/claude-qmd
```

### 3. Set up indexes

```bash
# Run setup command
/qmd:setup
```

Or manually:

```bash
# Index plugin docs
qmd index plugins --path ~/.claude/plugins --pattern "**/*.md"

# Index protocol skills
qmd index protocols --path ~/.claude/plugins --pattern "**/skills/**/*.md"

# Index current project
qmd index project --path . --pattern "**/*.md"
```

## Commands

| Command | Description |
|---------|-------------|
| `/qmd:search <query>` | Hybrid semantic + keyword search |
| `/qmd:protocols <query>` | Search DeFi protocol documentation |
| `/qmd:index [collection]` | Index or re-index collections |
| `/qmd:collections` | List and manage indexed collections |
| `/qmd:setup` | First-time setup wizard |

## MCP Integration

This plugin configures QMD as an MCP server, giving Claude direct access to:

- `qmd_search` - BM25 keyword search
- `qmd_vsearch` - Vector semantic search
- `qmd_query` - Hybrid search with reranking

## Standard Collections

| Collection | Contents |
|------------|----------|
| `plugins` | All Claude Code plugin documentation |
| `protocols` | DeFi protocol skills (Aave, Balancer, Uniswap, etc.) |
| `project` | Current project markdown files |
| `claude-md` | All CLAUDE.md configuration files |

## Use Cases

- **Cross-protocol search**: "How do different protocols handle liquidation?"
- **Skill discovery**: "What commands handle git commits?"
- **Documentation lookup**: "Flash loan implementation in Aave"
- **Context augmentation**: Automatically retrieve relevant docs before tasks

## Requirements

- [Bun](https://bun.sh) 1.0.0+
- ~1.9GB disk space for models (downloaded on first use)
- SQLite (usually pre-installed)

## License

MIT
