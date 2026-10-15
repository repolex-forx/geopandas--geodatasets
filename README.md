# Repolex Knowledge Graph of geopandas/geodatasets

RDF knowledge graph data for [geopandas/geodatasets](https://github.com/geopandas/geodatasets), parsed by [repolex](https://repolex.ai).

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
rlex download geopandas/geodatasets
```

Consult `rlex --help` for other options, including SPARQL queries, HTTP server, and interactive visualization.

## Data structure

All data is stored as gzip-compressed [N-Quads](https://www.w3.org/TR/n-quads/) (`.nq.gz`), a standard RDF format that can be loaded into any triplestore or graph database.

```
.
├── aggregate
│   ├── ast
│   │   └── ef8bcc9b6778a47dfaea689fa9e772276d1d6d73
│   │       └── chunk-001.nq.gz
│   └── repolex
│       └── ef8bcc9b6778a47dfaea689fa9e772276d1d6d73
│           └── chunk-001.nq.gz
├── blob
│   ├── 014505316c10c2f0e3bd76b273bf1de21a87cc20.nq.gz
│   ├── 1d82b17d8a3037206020830808e35e51e845af1d.nq.gz
│   ├── 1e124a40bb89e32b5e0f7eddefd7ca89c88ce076.nq.gz
│   ├── 1fee98ab5143a29d4d8218f166e050a5f9b7495b.nq.gz
│   ├── 287d3c1be2acba33380d43af8e96060896c66c90.nq.gz
│   ├── 2c81ba4752761e45b5fc769d2c8a8a78ec717e2c.nq.gz
│   ├── 2eed60379b2c4cbdf623e93392ed2e160ec15367.nq.gz
│   ├── 33dd34f845d0a8fcfbac11264a0ebe6043a22bb7.nq.gz
│   ├── 406d0567aa0dd785ecfd5fe526bc842e65590fd1.nq.gz
│   ├── 41d837119cbb6d0a204b013298d045935826b3b6.nq.gz
│   ├── 45c88da9075245af803b16737f2d285e596c3c8f.nq.gz
│   ├── 4ba7a2179d8a692f0b42611f5e0ad2df6677f77c.nq.gz
│   ├── 51074595e9ee563fc78eb25162d656abd58b384a.nq.gz
│   ├── 600c5f4d443bcce385caa895385de5aac76eaf49.nq.gz
│   ├── 6247f7e231716482115f34084ac61030743e0715.nq.gz
│   ├── 800f69d7b93edeecfabe5f1de32a4ffb0f0fa55b.nq.gz
│   ├── 8280b281da2d84ee480f1b08639397591f7d768a.nq.gz
│   ├── 85e8f2a0e5676daa9ba519f9fec82f9ebc301c55.nq.gz
│   ├── 93a3dcb8580c5e7aa5d3c0bd0e92261d722063d3.nq.gz
│   ├── 943413cd34deecaaacb7f11a3bfef25cd3d204c9.nq.gz
│   ├── 944546b90b911b837665489f0acb91a8541e434d.nq.gz
│   ├── 9840fddef1c10a382851e93a194dcb88d7d4632b.nq.gz
│   ├── 9a869f6da0dc8966e5b7a42fadb67745234f4f13.nq.gz
│   ├── aa0a74cbbe07fcea2ab1f8e5e2c06794c998bede.nq.gz
│   ├── ad684954fbd5aa2fcfed88ef3be0806718c08889.nq.gz
│   ├── b3305cb5d5b3a65cd2ebbce2012ab6580b7713aa.nq.gz
│   ├── bfa135d3996955f8154d7965c329554f6e1d45c2.nq.gz
│   ├── c398d1062d6a1b2a58aea8205f3436833d0ab431.nq.gz
│   ├── c89c19a8bb0b8bc86e59d4a9aae3cee351c5edae.nq.gz
│   ├── c909595ec3a49be52ae78ea665eaaf1a996e5813.nq.gz
│   ├── d0c3cbf1020d5c292abdedf27627c6abe25e2293.nq.gz
│   ├── d1053454c4930bf4c11d573816ee02a777704e21.nq.gz
│   ├── d64680a38eb386273e799aa040fe523440ea29f5.nq.gz
│   ├── de98a72e4ac11539d6675732517d48e94423722c.nq.gz
│   ├── e69de29bb2d1d6434b8b29ae775ad8c2e48c5391.nq.gz
│   └── fefb688747f22486f6134a5e2fe47870ac03fd15.nq.gz
├── branch
│   └── branch.nq.gz
├── commit
│   └── commit.nq.gz
├── filetree
│   └── ef8bcc9b6778a47dfaea689fa9e772276d1d6d73.nq.gz
├── issue
│   └── issue.nq.gz
├── pr
│   └── pr.nq.gz
└── tag
    └── tag.nq.gz

13 directories, 44 files
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

[geopandas/geodatasets](https://github.com/geopandas/geodatasets)

---
*Parsed on 2026-10-15 by [repolex](https://repolex.ai)*
