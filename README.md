# Repolex Knowledge Graph of PyCQA/eradicate

RDF knowledge graph data for [PyCQA/eradicate](https://github.com/PyCQA/eradicate), parsed by [repolex](https://repolex.ai).

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
rlex download PyCQA/eradicate
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── d3f3d01e5cc9c65474d0f361e3f50fe1500b340c
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── d3f3d01e5cc9c65474d0f361e3f50fe1500b340c
│           └── chunk-001.nq.gz
├── blob
│   ├── 3fe1289a2191baecfc7717d8946d296072b46d51.nq.gz
│   ├── 4807b6578ada253da0fbff94279f9355d261db73.nq.gz
│   ├── 81f43962f940791bb4d2df5e579b444ea354811f.nq.gz
│   ├── 8215beb05f528ae5e69cd3a5de51744203599dc6.nq.gz
│   ├── bc3d54e6c66400ffebac3fdcf26aa5e9ab0d1361.nq.gz
│   ├── c0de24a9cbf46cf9bd6c4e152847ca4857f8fd98.nq.gz
│   ├── da70b5b9fc904ddee805e1f96faff1688df82ac4.nq.gz
│   ├── eb231a2bb91ab58a680e61e905a6d61346b69edd.nq.gz
│   ├── f5b6a51dd8731595a193d3b266c8223b7f3bf066.nq.gz
│   └── ffbe05ffa4d95f5ca2a1e228896eaa61dfd5d91d.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── d3f3d01e5cc9c65474d0f361e3f50fe1500b340c.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 18 files
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

[PyCQA/eradicate](https://github.com/PyCQA/eradicate)

---
*Parsed on 2026-10-19 by [repolex](https://repolex.ai)*
