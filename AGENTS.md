# AGENTS.md

## Cursor Cloud specific instructions

### Repository overview

This is a **documentation-only repository** containing Korean-language tutorial/workshop guides for building a pizza ordering chatbot using the [danbee.Ai](https://danbee.ai) platform. There is **no application source code**, no `package.json`, no test framework, and no linting configuration.

The repository contains:
- `README.md` — Tutorial index page
- `실습/` — 13 step-by-step markdown lab guides (Labs 01–13)
- `강의파일/` — Lecture PDF
- `실습공유.md` — Shared API endpoint info

### Services referenced in the tutorial

| Service | Purpose | Notes |
|---|---|---|
| **danbee.Ai** | SaaS chatbot builder | External platform; requires account |
| **Strapi v3** | REST API for pizza menu/pricing data | Original Docker image (`strapi/strapi:3.2.5`) is deprecated and no longer available on Docker Hub |
| **MongoDB 4.4.1** | Database for Strapi | Docker image still available |
| **Naver Mail SMTP** | Order confirmation emails (Lab 12) | Optional |
| **LINE Messaging API** | Chat channel integration (Lab 13) | Optional |

### Running a mock API server

Since the original Strapi v3 Docker image is no longer available, use a mock Express.js server to replicate the tutorial's API endpoints (`/pizzasizes`, `/pizasizes`, `/chickens`). See `/tmp/mock-strapi/server.js` for reference.

### Viewing documentation locally

Use `grip` (Python package) to render the markdown files with GitHub-flavored styling:

```bash
pip install grip
grip README.md 0.0.0.0:6419
```

Then visit `http://localhost:6419/`.

### Important caveats

- There are **no lint checks, automated tests, or build steps** in this repo — it is purely documentation.
- The shared Strapi instance at `http://gbible.iptime.org:1337` (referenced in `실습공유.md`) is likely offline since the tutorial is from ~2019–2020.
- Docker is required for running the MongoDB container (used by Strapi or mock API).
- When setting up Docker in a Cloud Agent VM, use `fuse-overlayfs` storage driver and `iptables-legacy` as described in the standard Docker-in-Docker setup.
