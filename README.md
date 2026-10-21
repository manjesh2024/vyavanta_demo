# VYAVANTA

**EVERY BUSINESS. ONE ECOSYSTEM.**

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

The 45-file source snapshot at commit `43b26a96f465188b5dc8ae555856b0ea93ff1b9c` was copied to this target and path-verified. The source repository at [manjesh2024/vyavsetu](https://github.com/manjesh2024/vyavsetu) remains untouched. The target has its own Git history; source commit ancestry was not transferred by the API-based copy.

- The browser prototype, customer/driver/store surfaces, Configuration Studio, docs, workflows, assets and tests are present.
- VYAVANTA logo variants from the supplied identity artwork are stored under `assets/vyavanta-*.webp`.
- Main/app themes and visual documentation use the supplied teal/aqua/navy/orange palette with contrast-safe interaction tokens.
- The legacy `vyavsetu-*.svg` source files remain for migration traceability only and are not referenced by the current UI.
- Production Flutter/Spring Boot services and device/hardware integrations remain outside this HTML demo.

See [BRAND.md](BRAND.md) and [assets/README.md](assets/README.md) for exact asset names, color values and usage rules.

## Product/production boundary

The copied project is a functional browser-local demo, not the production Flutter/Spring Boot billing platform. Demo interactions use browser-local storage and simulated payments. Live gateway integration, production authentication/authorization, PostgreSQL persistence, durable offline sync, statutory invoice generation/tax rules and physical printer validation are not implemented in this repository snapshot.

Do not use the demo for live transactions or real customer data. Read [docs/DEVELOPER_HANDOFF.md](docs/DEVELOPER_HANDOFF.md) and [docs/TEST_REPORT.md](docs/TEST_REPORT.md) before implementation.
