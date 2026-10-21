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

## Migration status

This target is being bootstrapped from the inspected [Vyavsetu source repository](https://github.com/manjesh2024/vyavsetu). The source repository is not modified by this copy.

- Prototype code, application surfaces, tests, assets and documentation are carried forward for evaluation.
- The current source UI and SVG assets have not yet completed the VYAVANTA visual rebrand.
- The checked-in source SVGs are documented as legacy approximations, not approved master artwork. They must not be represented as the official VYAVANTA logo or used for final production branding.
- The clean original VYAVANTA master artwork must be installed before producing final logo exports, extracting authoritative color tokens or switching logo usage in UI/receipts.

See [BRAND.md](BRAND.md) and [assets/README.md](assets/README.md) for the artwork guardrails.

## Product/production boundary

The copied project is a functional browser-local demo, not the production Flutter/Spring Boot billing platform. Demo interactions use browser-local storage and simulated payments. Live gateway integration, production authentication/authorization, PostgreSQL persistence, durable offline sync, statutory invoice generation/tax rules and physical printer validation are not implemented in this repository snapshot.

Do not use the demo for live transactions or real customer data. Read [docs/DEVELOPER_HANDOFF.md](docs/DEVELOPER_HANDOFF.md) and [docs/TEST_REPORT.md](docs/TEST_REPORT.md) before implementation.
