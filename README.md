# iPRD GitHub Pages Host

This repository hosts generated iPRD HTML files as separate GitHub Pages routes.

## Legal

- License: Proprietary (`LICENSE`)
- Privacy policy: `PRIVACY_POLICY.md`

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

## GPT Action Connector

Use `openapi.yaml` as the GPT Action schema.
Use `MASTER_PROMPT_DEPLOY_BLOCK.md` as the deploy instruction block to append to your GPT master prompt.

- Deployment operation: `deployIprdPage`
- Status operation: `listIprdWorkflowRuns`
- Fixed values:
  - `owner`: `RBX-Labs`
  - `repo`: `iPRD`
  - `workflow_id`: `publish-iprd.yml`
  - `ref`: `main`
- Workflow inputs required:
  - `slug`
  - `title`
  - `html_base64`

## GPT Action Authentication (PAT)

In the GPT Action authentication section:

1. `Authentication` -> select `API Key`
2. `API Key` -> paste your fine-grained PAT
3. `Auth type` -> `Bearer`
4. `Header name` -> `Authorization`

Required PAT setup on GitHub:

1. Token type: `Fine-grained personal access token`
2. Resource owner: organization/account that owns `RBX-Labs/iPRD`
3. Repository access: `Only select repositories` -> `RBX-Labs/iPRD`
4. Repository permissions:
   - `Actions`: `Read and write`
   - `Contents`: `Read and write`
