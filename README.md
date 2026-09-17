# Repolex Knowledge Graph of codecov/codecov-python

RDF knowledge graph data for [codecov/codecov-python](https://github.com/codecov/codecov-python), parsed by [repolex](https://repolex.ai).

> **Note**: This data is experimental and subject to change without notice.

## How to use this data

The easiest way to get started is to install the [lexq](https://github.com/repolex-ai/lexq) query tool using [uv](https://docs.astral.sh/uv/getting-started/installation/).

If you have uv installed, just copy/paste this into your terminal:

```bash
uv tool install git+https://github.com/repolex-ai/lexq
```

This installs lexq onto your system, in your user context. Verify the install:

```bash
lexq --help
```

**lexq is designed to be used primarily by LLMs in a terminal.** Start up your favorite LLM and ask it to use the lexq tool. It's that easy!

To load this repo's data:

```bash
lexq download codecov/codecov-python
```

This will automatically download essential data files from the last parsed commit. Consult `lexq --moreinfo` for other options, including downloading multiple commits, blobs, etc.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── a78512e4b00e67cfb3fccb530c9ca97a6c42eae5
│   │       └── chunk-001.nq.gz
│   ├── lsp
│   │   └── a78512e4b00e67cfb3fccb530c9ca97a6c42eae5.nq.gz
│   └── repolex
│       └── a78512e4b00e67cfb3fccb530c9ca97a6c42eae5
│           └── chunk-001.nq.gz
├── blob
│   ├── 00ef8a0900c12f55d79652951b4cebb479c8bc7d.nq.gz
│   ├── 1025c49bfe71d0cb4ab91b7c929baa9a92a5f92b.nq.gz
│   ├── 21e9b214fc2eaf333dbc22bbc01b73d5e20e6e1e.nq.gz
│   ├── 27531afdf4a4f9b592cb6de8d8496e49d190a15c.nq.gz
│   ├── 2a9acf13daa95e85642ea255d3e3bd1ef8252804.nq.gz
│   ├── 2e65efe2a145dda7ee51d1741299f848e5bf752e.nq.gz
│   ├── 491deae0af2cae800a8fd1bc1ffb5ecd09221266.nq.gz
│   ├── 60d08bb38b97db5ded6dc8dafae69855edb4cbeb.nq.gz
│   ├── 79d2d87e675c54cbd745d4f938942b408ee55fe8.nq.gz
│   ├── 7dbe1dda2f9041030d1e72231c52d3856cff4420.nq.gz
│   ├── 84880fa643a705f39f2a9efe02da727bbe4c342b.nq.gz
│   ├── 88cac4801351873e7291e4862b0f36b93f70a93b.nq.gz
│   ├── 98a4412ad63b9da5cf429eeb603543e42edcdfc5.nq.gz
│   ├── 99109edfa9d476c079c58a8d1dd2bdc0e173f911.nq.gz
│   ├── 9f1f3a55e51dc493ff28b90b7ffade44db4188b6.nq.gz
│   ├── b07bc8fb14d787b5cdd349c612530d9873609ae2.nq.gz
│   ├── cc2be9564e0c74f6a34f46fe90cf3d1640599f12.nq.gz
│   ├── d5eb65e549cb94934173bab6d1684dd7cfe6dedb.nq.gz
│   ├── d93121bfbaecd41693f28d5237afed79b03426ac.nq.gz
│   ├── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
│   ├── f69f56d8bc0cf2a409420b0f5765ce7700a17e6b.nq.gz
│   └── fae2de1e0d38af084140b7f127131149f2d7a904.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── dep
│   └── a78512e4b00e67cfb3fccb530c9ca97a6c42eae5.nq.gz
├── filetree
│   └── a78512e4b00e67cfb3fccb530c9ca97a6c42eae5.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

15 directories, 32 files
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

## Source repository

[codecov/codecov-python](https://github.com/codecov/codecov-python)

---
*Parsed on 2026-09-17 by [repolex](https://repolex.ai)*
