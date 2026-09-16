# Repolex Knowledge Graph of kr/text

RDF knowledge graph data for [kr/text](https://github.com/kr/text), parsed by [repolex](https://repolex.ai).

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
lexq download kr/text
```

This will automatically download essential data files from the last parsed commit. Consult `lexq --moreinfo` for other options, including downloading multiple commits, blobs, etc.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── 702c74938df48b97370179f33ce2107bd7ff3b3e
│   │       └── chunk-001.nq.gz
│   ├── lsp
│   │   └── 702c74938df48b97370179f33ce2107bd7ff3b3e.nq.gz
│   └── repolex
│       └── 702c74938df48b97370179f33ce2107bd7ff3b3e
│           └── chunk-001.nq.gz
├── blob
│   ├── 1c1f4e683931bb6f3abccdd1e4295b0dbfc260bc.nq.gz
│   ├── 3a9ec2db4f2eeb6a37e928ba89a7292968bc3cbe.nq.gz
│   ├── 4239aa43caa16a2391e5d3126ff48c1e45166cc9.nq.gz
│   ├── 480a328059998359c8fe481fb3dc6fc100c0fd2a.nq.gz
│   ├── 4ebac45c09251a797326982682b9dbceb1d60417.nq.gz
│   ├── 519ddc00a13090b688c369eaccb54ddba056a374.nq.gz
│   ├── 5818cf8dbb47dfd7172eee60fc7b9b81900706f2.nq.gz
│   ├── 5c723eee855267c1edbe5938947ff2009c187227.nq.gz
│   ├── 634b6e8ebb9235ad06627728425445d8f1e903b5.nq.gz
│   ├── 7302ce9f7a885f8b8bb3562190bb49d9015b58e4.nq.gz
│   ├── 7e6e7c0687b38783e15a299ca3bbc4b4b323f323.nq.gz
│   ├── 91d6b986a9e45474b2b574975918557f408e505c.nq.gz
│   ├── 93ac3fe15e3a5bd5133cb5081a967094cfcd578f.nq.gz
│   ├── 9a8cf78caed3f96d3b923a7eae916755a6236c0f.nq.gz
│   ├── b09bb03736dcdaa2e95234c0578a0b04b10048f4.nq.gz
│   ├── ce388f5a260e8d69b843aa1a6900cf299f98c657.nq.gz
│   └── cf4c198f9558f1f6065be321828b4e252dfa286a.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── 702c74938df48b97370179f33ce2107bd7ff3b3e.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

14 directories, 26 files
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

[kr/text](https://github.com/kr/text)

---
*Parsed on 2026-09-16 by [repolex](https://repolex.ai)*
