# Simon Latham Music Archive

An independent archive of Simon Latham's music history, Soundsation documentation, progressive-house and trance research, personal memories, and documented DJ support.

This repository is deliberately separate from [TRAX](https://github.com/simonlatham155-tech/trax). TRAX remains the digital audio workstation project; historical articles, evidence, and music-industry data live here.

## Archive contents

| Path | Purpose |
| --- | --- |
| `articles/` | Canonical Markdown articles with YAML metadata |
| `data/` | Original DJ-support workbook and machine-readable CSV |
| `src/` | Searchable browser application for all articles and DJ-support entries |
| `mcp-server/` | Read-only MCP access to the canonical articles |
| `progressive-house-kb-full.md` | Generated single-document export |

The archive currently contains 49 articles and 126 DJ-support entries spanning 1994–2021. Both are readable and searchable in the browser application.

## Source-of-truth rules

- Edit historical and biographical content in `articles/*.md`.
- Run `npm run generate:content` after article changes. This updates both the browser seed and the full Markdown export.
- Treat `data/Simon_Latham_DJ_Support_Database_COMPLETE.xlsx` as the preserved original workbook.
- Use `data/Simon_Latham_DJ_Support_Database.csv` for search, scripts, and data interchange.
- Edits made inside the browser are stored locally in IndexedDB. Export them before clearing browser data, then reconcile important changes back into `articles/`.

These rules prevent the browser, MCP server, and Markdown archive from silently becoming three different databases.

## Run the browser archive

```bash
npm install
npm run dev
```

Open <http://localhost:5173>.

For a production build:

```bash
npm run build
npm run preview
```

## Use the MCP server

```bash
cd mcp-server
npm install
npm run build
npm start
```

The MCP server provides article listing, article retrieval, full-text search, and a complete-context export. See [`mcp-server/README.md`](mcp-server/README.md) for configuration.

## DJ-support database

The workbook is preserved unchanged, alongside a UTF-8 CSV export of its main sheet:

- [`Simon_Latham_DJ_Support_Database_COMPLETE.xlsx`](data/Simon_Latham_DJ_Support_Database_COMPLETE.xlsx)
- [`Simon_Latham_DJ_Support_Database.csv`](data/Simon_Latham_DJ_Support_Database.csv)

See [`data/README.md`](data/README.md) for structure, provenance, and integrity checks.

## Publishing

The included GitHub Pages workflow builds and deploys the browser archive whenever `main` is updated. In the repository settings, set **Pages → Build and deployment → Source** to **GitHub Actions**.

## Rights

The repository is a personal research and evidence archive. No reuse licence is granted unless one is added explicitly.
