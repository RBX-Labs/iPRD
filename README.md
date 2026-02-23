# iPRD GitHub Pages Host

This repository hosts generated iPRD HTML files as separate GitHub Pages routes.

## Current hosted pages

- `/AI-index` -> `AI-index/index.html`

## Add a new page automatically

1. Open the main page: `https://rbx-labs.github.io/iPRD/`
2. Upload or paste generated `index.html`.
3. Set slug (example: `my-product-prd`).
4. Click `Deploy as GitHub Page`.
5. The workflow `.github/workflows/publish-iprd.yml` commits:
   - `/<slug>/index.html`
   - `iprds/index.json` (registry used by homepage)

## Token requirements for deploy button

Use a fine-grained PAT with access to repo `RBX-Labs/iPRD` and permissions:
- Contents: Read and write
- Actions: Read and write

The token is stored in browser localStorage only.
