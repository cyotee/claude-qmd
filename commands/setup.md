---
description: Set up QMD for first-time use with standard collections
---

# QMD Setup

Configure QMD and create initial indexes.

## Prerequisites

Check QMD is installed:

```bash
qmd --version
```

If not installed:

```bash
bun install -g qmd
```

## Setup Steps

### 1. Verify Installation

```bash
# Check qmd works
qmd --help

# Check index location
ls -la ~/.cache/qmd/
```

### 2. Index Standard Collections

Run these to set up the standard collections:

```bash
# Plugin documentation (all your Claude plugins)
qmd index plugins --path ~/.claude/plugins --pattern "**/*.md" --description "Claude Code plugin documentation and skills"

# Protocol-specific skills (DeFi protocols)
qmd index protocols --path ~/.claude/plugins --pattern "**/skills/**/*.md" --description "DeFi protocol technical documentation - Aave, Balancer, Uniswap, etc."

# Current project docs
qmd index project --path . --pattern "**/*.md" --description "Current project documentation"
```

### 3. Verify MCP Configuration

This plugin includes `.mcp.json` which adds:

```json
{
  "mcpServers": {
    "qmd": {
      "command": "qmd",
      "args": ["mcp"]
    }
  }
}
```

After installing this plugin, restart Claude Code to enable MCP tools.

### 4. Test Search

```bash
# Keyword search
qmd search "flash loan" --collection protocols

# Semantic search
qmd vsearch "how to borrow assets" --collection protocols

# Hybrid with reranking
qmd query "liquidation mechanism" --collection protocols --limit 5
```

## First Run Notes

On first search/index, QMD downloads models (~1.9GB):
- This is one-time
- Models stored in `~/.cache/qmd/models/`
- All processing stays local

## Troubleshooting

**"qmd: command not found"**
```bash
bun install -g qmd
```

**MCP tools not appearing**
- Restart Claude Code after plugin install
- Check `~/.claude/settings.json` for mcpServers entry

**Index seems slow**
- First index downloads models
- Large directories take time for embeddings
- Use more specific glob patterns
