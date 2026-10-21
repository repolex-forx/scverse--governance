# Repolex Knowledge Graph of scverse/governance

RDF knowledge graph data for [scverse/governance](https://github.com/scverse/governance), parsed by [repolex](https://repolex.ai).

> **Note**: This data is experimental and subject to change without notice.

## How to use this data

The easiest way to get started is to install the [rlex](https://github.com/repolex-ai/rlex) query tool:

```bash
cargo install --git https://github.com/repolex-ai/rlex
```

Verify the install:

```bash
rlex --help
```

**rlex is designed to be used primarily by LLMs in a terminal.** Start up your favorite AI assistant and ask it to use rlex. It handles the SPARQL — you just ask questions in plain English.

To load this repo's data:

```bash
rlex download scverse/governance
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 74bd25edb86d70abda9246176b5bcb82a3343994
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── 74bd25edb86d70abda9246176b5bcb82a3343994
│           └── chunk-001.nq.gz
├── blob
│   ├── 015842e85cf2c304265c0c6f829bb2b6613de93d.nq.gz
│   ├── 042404ed990f94409b50e18b9d67b9507d06c5a5.nq.gz
│   ├── 08b046606161682300b3e81e12d4a4ed7b4c1c7e.nq.gz
│   ├── 2159e2b3e5ea7ca6f4132ac63b8b380b7d27a57d.nq.gz
│   ├── 27225594566cbd7da03d5eeb0415356e3d7aa051.nq.gz
│   ├── 3ce13cd17be6691bc418dad28d4ebd9342862ee6.nq.gz
│   ├── 53c789c650c7fc30926ce4db7cdd1fa728961585.nq.gz
│   ├── 99ddf52f7f7b331d7d7a390889e851772d9dcfd4.nq.gz
│   ├── a459ae8802f621f6d63a7a489b5ba9ee50e40c6b.nq.gz
│   ├── b6e47617de110dea7ca47e087ff1347cc2646eda.nq.gz
│   └── ec7bd4c51ff5a46c2555aba02d8641612bfb7a1c.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 74bd25edb86d70abda9246176b5bcb82a3343994.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 19 files
```

| Directory | What it contains |
|-----------|-----------------|
| `blob/` | Per-file AST graphs, content-addressed by git blob SHA. Each file in the source repo gets its own graph. |
| `aggregate/ast/` | Combined AST graph per parsed commit. Merges all blob graphs for a snapshot of the entire codebase at that point. |
| `aggregate/lsp/` | Language Server Protocol enrichment: resolved symbols, definitions, references, and type information. |
| `aggregate/dataflow/` | Interprocedural data flow edges between functions and modules. |
| `aggregate/repolex/` | Combined graph (AST + LSP + dataflow) per commit. |
| `commit/` | Git commit metadata (author, date, message, parent links). |
| `branch/` | Branch metadata. |
| `tag/` | Tag metadata. |
| `filetree/` | File tree snapshots per commit (which files existed and their blob SHAs). |
| `audit/` | Code architecture and graph audit reports per commit. |

## Source repository

[scverse/governance](https://github.com/scverse/governance)

---
*Parsed on 2026-10-21 by [repolex](https://repolex.ai)*
