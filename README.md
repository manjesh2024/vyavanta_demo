# VYAVANTA

**Every Business. One Ecosystem.**

VYAVANTA is the target brand for this commerce prototype: restaurant and retail POS, inventory, marketplace, delivery, and SaaS administration.

## Run the current prototype

Open `index.html` or `app.html` in a modern browser. No build step is required. For a local server:

```bash
python3 -m http.server 8000
```

Then visit `http://localhost:8000`.

## Developer documentation

- [Developer Documentation Portal](docs/index.html)
- [Visual architecture and flowcharts](docs/architecture-flowcharts.html)
- [API architecture and backend blueprint](docs/api-architecture.html)
- [Configuration Studio](studio/index.html)
- [Developer handoff](docs/developer-handoff.html)
- [Brand guidelines](docs/brand-guidelines.html)
- [Responsive/device matrix](docs/responsive-device-matrix.html)
- [Demo verification report](docs/test-report.html)
- [Hinglish quick start](docs/quick-start-hinglish.html)

## Repository snapshot and migration status

The 45 file paths in the source snapshot at commit `43b26a96f465188b5dc8ae555856b0ea93ff1b9c` were copied into this target and verified against the target tree on 2026-10-21. The source repository at [manjesh2024/vyavsetu](https://github.com/manjesh2024/vyavsetu) was not modified.

- The target uses its own commit history; the source commit ancestry was not transferred by the API-based snapshot copy.
- The interactive HTML prototype, customer/driver/store surfaces, Configuration Studio, docs, workflows, assets and tests are present.
- Visible product branding was updated to VYAVANTA. Text-only wordmark placeholders replace legacy logo usage until the clean master artwork is available.
- Purple/violet/magenta/orange theme styling is provisional. Final logo exports and authoritative color tokens are blocked until the original master artwork is supplied.
- The source SVGs remain in the repository for traceability only; they are not official VYAVANTA assets.

See [BRAND.md](BRAND.md) and [assets/README.md](assets/README.md) for the artwork guardrails.

## Product/production boundary

The copied project is a functional browser-local demo, not the production Flutter/Spring Boot billing platform. Demo interactions use browser-local storage and simulated payments. Live gateway integration, production authentication/authorization, PostgreSQL persistence, durable offline sync, statutory invoice generation/tax rules and physical printer validation are not implemented in this repository snapshot.

Do not use the demo for live transactions or real customer data. Read [docs/DEVELOPER_HANDOFF.md](docs/DEVELOPER_HANDOFF.md) and [docs/TEST_REPORT.md](docs/TEST_REPORT.md) before implementation.
