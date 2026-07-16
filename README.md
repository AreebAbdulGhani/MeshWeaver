# MeshWeaver

**The Enterprise Content CI/CD Pipeline for Adobe Express.**

Link a master deck to your CRM. MeshWeaver maps the document semantically, rewrites the value proposition for each prospect, and reflows the layout so the new copy fits — then hands you a batch to approve. Build and test are automated; the release is still yours.

Built as a four-layer pipeline:

| Layer | What it does |
| --- | --- |
| **Zero-Trust Ingestion Plane** | Scoped OAuth 2.0 + PKCE connections to Salesforce, Marketo, HubSpot, and Workfront. Ephemeral per-job workers, no CRM data at rest, mutual TLS, full audit log. |
| **Semantic Document Map** | Walks the node tree via `allDescendants` / `allTextContent` and infers each text frame's role from hierarchy — headline, subhead, body, caption — not from guesswork. |
| **Generative Agent** | Rewrites the value proposition against the prospect's firmographics, with brand guidelines as hard constraints and per-slot length budgets. |
| **Layout Reflow Engine** | Uses Node resize methods and threaded text controls so generated copy fits the design instead of breaking it. |

A **human approval gate** sits before deployment. MeshWeaver never auto-sends.

## Contents

- `index.html` — single-page site (dark, dependency-free, self-contained)
- `MeshWeaver_Technical_Architecture_v1.pdf` — technical whitepaper
- `whitepaper/whitepaper.html` — whitepaper source (renders to the PDF via headless Chrome)

## Status

Pre-seed, prototyping. Backend built against the Adobe Express Developer MCP Server; UI architected in Spectrum Web Components for native dark mode support. Public beta targeted for **September 2026**.

## Local preview

```sh
python3 -m http.server 8000
# → http://localhost:8000
```

## Rebuilding the whitepaper PDF

```sh
"/Applications/Google Chrome.app/Contents/MacOS/Google Chrome" \
  --headless --disable-gpu --no-pdf-header-footer \
  --print-to-pdf="MeshWeaver_Technical_Architecture_v1.pdf" \
  "file://$PWD/whitepaper/whitepaper.html"
```

## Contact

Areeb Abdul Ghani — areebghani359@gmail.com — Bengaluru, India
