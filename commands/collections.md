---
description: List and manage QMD search collections
---

# QMD Collections

View and manage your indexed collections.

## Usage

```
/qmd:collections [action]
```

## List Collections

```bash
qmd list
```

Shows all indexed collections with:
- Name
- Document count
- Last indexed time
- Description

## Collection Details

```bash
qmd stats <collection>
```

Shows:
- Total documents
- Total chunks
- Index size
- Glob pattern used

## Remove Collection

```bash
qmd remove <collection>
```

## Standard Collections

| Collection | Purpose | Recommended Pattern |
|------------|---------|---------------------|
| `plugins` | Plugin docs | `~/.claude/plugins/**/*.md` |
| `protocols` | Protocol skills | `~/.claude/plugins/**/skills/**/*.md` |
| `project` | Current project | `./**/*.md` |
| `claude-md` | Config files | `**/CLAUDE.md` |
| `notes` | Personal notes | `~/notes/**/*.md` |

## Present Output

```
QMD Collections:

| Collection | Docs | Chunks | Last Indexed |
|------------|------|--------|--------------|
| plugins    | 42   | 380    | 2h ago       |
| protocols  | 156  | 1,240  | 1d ago       |
| project    | 12   | 85     | 5m ago       |

Total: 3 collections, 210 documents, 1,705 chunks
```

If no collections exist, guide user to `/qmd:index` or `/qmd:setup`.
