---
description: Search indexed collections with QMD (hybrid semantic + keyword)
---

# QMD Search

Search your indexed documentation using hybrid semantic search.

## Usage

```
/qmd:search <query> [--collection <name>] [--limit <n>]
```

## Parameters

- `query` - What to search for (natural language or keywords)
- `--collection` - Which collection to search (default: all)
- `--limit` - Max results (default: 10)

## Available Collections

Check what's indexed:

```bash
qmd list
```

Standard collections:
- `plugins` - All plugin documentation
- `protocols` - DeFi protocol skills
- `project` - Current project markdown
- `claude-md` - CLAUDE.md files

## Execute Search

Use the MCP tool `qmd_query` for hybrid search:

```
qmd_query(collection: "<collection>", query: "<user query>", limit: <n>)
```

If MCP unavailable, fall back to CLI:

```bash
qmd query "<user query>" --collection <collection> --limit <n> --format json
```

## Present Results

Format results clearly:

```
Found [N] relevant documents:

1. **[Title/Path]** (score: X.XX)
   > [Brief excerpt showing match]

2. **[Title/Path]** (score: X.XX)
   > [Brief excerpt showing match]
```

If no results: suggest refining the query or checking if the collection is indexed.
