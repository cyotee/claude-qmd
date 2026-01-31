---
description: Index or re-index markdown collections for QMD search
---

# QMD Index

Create or update search indexes for markdown collections.

## Usage

```
/qmd:index [collection] [--path <dir>] [--pattern <glob>]
```

## Quick Index Commands

### Index All Standard Collections

```bash
# Plugin documentation
qmd index plugins --path ~/.claude/plugins --pattern "**/*.md" --description "Claude Code plugin documentation"

# Protocol skills specifically
qmd index protocols --path ~/.claude/plugins --pattern "**/skills/**/*.md" --description "DeFi protocol technical documentation"

# Current project
qmd index project --path . --pattern "**/*.md" --description "Project documentation and notes"

# All CLAUDE.md files
qmd index claude-md --path ~ --pattern "**/CLAUDE.md" --description "Claude configuration and instructions"
```

### Index Custom Collection

```bash
qmd index <name> --path <directory> --pattern "<glob>" --description "<context>"
```

## Re-index After Changes

When plugins are updated or new docs added:

```bash
# Re-index specific collection
qmd index plugins --path ~/.claude/plugins --pattern "**/*.md"

# Re-index all (spawns indexer agent)
```

For full re-index, spawn the indexer agent:

```
Use Task tool with:
- subagent_type: "general-purpose"
- model: "haiku"
- prompt: "Read plugins/qmd/agents/indexer.md and execute full re-index"
```

## Check Index Status

```bash
qmd list
qmd stats
```

## First-Time Setup

On first index, QMD downloads ~1.9GB of models:
- EmbeddingGemma (300M) - vector embeddings
- Qwen3-Reranker (0.6B) - relevance scoring
- Query expansion model (1.7B) - search variations

This is one-time. Subsequent indexes are fast.
