# VYAVANTA — Developer Handoff

**Tagline:** EVERY BUSINESS. ONE ECOSYSTEM.  
**Status:** Interactive demo prototype; not a production billing system.

## 1. Product scope

VYAVANTA is a connected commerce platform for restaurant and retail businesses. The intended product family includes:

- Business Admin: stores/locations, catalog, staff, reports and settings.
- POS Terminal: offline-capable counter billing, provisional bill, payment and final invoice.
- Restaurant / KDS: order routing, kitchen ticket lifecycle and service status.
- Inventory & Purchasing: stock ledger, receiving, transfers, reorder alerts and purchase approvals.
- Customer Marketplace: discovery, catalog, cart, checkout, customer order timeline.
- Driver App: assigned deliveries, pickup, proof of delivery and delivery completion.
- SaaS Super Admin: tenants, plans, subscriptions, entitlements, support, platform audit and feature flags.
- Developer Access: brand assets, design tokens, responsive rules, diagrams, business invariants and developer checklist.

The current HTML demo presents sample data and illustrative interactions. It does not implement real identity, payment, tax, statutory invoices, database persistence, hardware, or server synchronization.

## 2. Brand guidelines

### Official identity

- Brand: **VYAVANTA**
- Tagline: **Every Business. One Ecosystem.**
- Selected visual direction: circular/orbit-like emblem with purple, violet, magenta/pink and orange gradients; navy wordmark.
- Logo artwork must come from the clean original master supplied by the product owner. Do not redraw, regenerate, approximate, recolour, simplify or reconstruct it.

### Current asset status

The source repository's checked-in `vyavsetu-*.svg` files are legacy source-brand approximations/traces and are not official VYAVANTA artwork. The located `vyavanta_logo_assets.zip` documents itself as raster crops from a brand-board image, not original editable/vector master artwork. Neither should be passed off as the official logo or used as production assets.

Until the clean original master or approved original export pack is provided, use text-only VYAVANTA placeholders. Do not use legacy logo images on login, navigation, invoices, receipts, customer/driver apps or app icons.

### Colors and design tokens

Purple/violet, magenta/pink, orange/light orange and navy are the provisional visual direction. HEX values shown on reference boards are not authoritative. Extract the actual logo colors from the clean master and record sampled HEX, method and semantic token assignments before finalizing the design system.

Production themes must share semantic tokens (primary, secondary, accent, surface, on-surface, border, success, warning, danger) rather than hardcoding component-specific colors. Validate contrast in light, dark and high-contrast modes.

## 3. Responsive design contract

The HTML preview includes viewport presets; final behaviour must be content-driven and adapt to the available width. These widths are starting breakpoints, not device-model detection rules.

| Layout | Starting width | Key expectations |
|---|---:|---|
| Desktop / laptop | ≥ 1200 px | Full navigation, multi-column analytics, dense tables |
| Business-store POS | 900–1199 px | Large touch targets, keyboard/scanner support, visible cart |
| Tablet / iPad | 620–899 px | Compact navigation, responsive panels, portrait/landscape |
| Android / iPhone | ≤ 619 px | Single column, safe-area insets, reachable actions, readable scaling |

Production acceptance must additionally test: split screen, landscape, keyboard visible, 200% zoom/text scaling, slow network, offline, long translations, empty/loading/error states and accessibility semantics. Touch targets should generally be at least 44 × 44 CSS px where practical.

## 4. Proposed production architecture

- Clients: Flutter apps/adaptive UI for Android, iOS, Web, Windows/macOS/Linux as agreed.
- Backend: Java Spring Boot modular monolith with explicit module boundaries and versioned APIs.
- Database: PostgreSQL.
- Local POS: Drift/SQLite with schema migrations and a transactional outbox.
- Auth: session/token validation, membership, tenant/location context and server-side RBAC.
- Modules: identity/session, organizations/tenants, roles/permissions, catalog, pricing/tax, orders, payments, invoices, inventory, purchasing, restaurant/KDS, marketplace, delivery, notifications, subscriptions/entitlements, audit and feature flags.
- Sync: local outbox → authenticated idempotent push → server validation/commit → acknowledgement → delta pull/reconciliation.
- Observability: structured logs, correlation IDs, redacted diagnostics, metrics and auditable operator actions.

## 5. Non-negotiable business rules

- All protected data reads/writes must be scoped by tenant and location on the server. Client-selected tenant IDs cannot be trusted by themselves.
- Server revalidates product, price, discounts, tax and stock at checkout.
- Use idempotency keys for order creation, payment submission, sync events and retryable mutations.
- Do not mark an order paid from a client-only callback. Verify gateway webhooks and reconcile uncertain payment results.
- Final invoices are immutable. Use explicit credit notes, refunds, void/reversal records according to jurisdictional rules.
- Separate provisional bills from legally final invoice identifiers.
- Store stock changes as auditable ledger movements with source references and defined conflict policy.
- Every significant status transition records actor, timestamp, source and outcome.
- Offline writes remain locally durable until acknowledgement; expose pending, syncing, synced, failed and conflict states.
- Failed requests must not erase drafts or silently indicate success.
- Cash-drawer opening is restricted to the configured payment/role policy; don't trigger it for online payment.
- Printer delivery is not the same as order/payment success; track print jobs separately.
- Server and database time remain authoritative for audit timestamps.

## 6. Decisions to close before implementation

1. Tax/legal jurisdiction, rounding, invoice fields and retention policy.
2. Offline invoice-number strategy: provisional references or server-reserved ranges.
3. Payment provider, webhooks, refunds, split and partial payments.
4. Exact receipt printer, drawer model, paper widths and supported connections.
5. Stock reservation and offline oversell policy across multiple terminals.
6. Marketplace checkout policy (recommended MVP: one merchant/store per order).
7. Authentication provider, account recovery and user/tenant onboarding.
8. Retention, backup, export and deletion policies for customer and audit data.

## 7. Test matrix

- Domain tests: pricing, taxes, rounding, discounts, permissions, order state machine, invoice immutability.
- API tests: tenant isolation, forbidden cross-tenant reads, request validation, idempotency and concurrency.
- Database tests: migrations from prior versions, transaction rollback, stock ledger consistency.
- Offline tests: kill/restart while pending, duplicate request, interrupted upload, auth expiry, conflict resolution and delta reconciliation.
- UI tests: responsive breakpoints, keyboard, scanner, touch, accessibility, loading/empty/error states and theme switching.
- Payments: success, failure, timeout/unknown result, webhook duplication, refund and reconciliation.
- Hardware: print success/failure/retry, 58/80 mm layouts, Windows printer setup, cash drawer open only under allowed conditions.
- Release: secrets review, dev/staging/prod config, migration plan, observability, backups and rollback.

## 8. Configuration Studio — new product capability

The proposed Configuration Studio lets authorised admins configure supported page layouts, semantic design tokens, dynamic form schemas, category visibility, and module/navigation visibility by surface, tenant and store. Configuration uses a registered component/action allowlist; it must not execute arbitrary user-authored HTML, JavaScript, Dart, SQL or scripts. Backend permissions and plan entitlements remain authoritative.

**Safety boundary:** the isolated browser prototype at `studio/index.html` stores only under `vyavsetu_studio_sandbox_v1`. Its local “publish” creates a sandbox snapshot only. Existing app screens, business logic and browser storage do not consume its data. Do not connect the Studio to live app surfaces until the versioned Spring Boot API, PostgreSQL schema, tenant/RBAC enforcement, audit/outbox, Flutter configuration adapter, compatibility checks and rollback process have been implemented and tested.

Read the [full Configuration Studio product/engineering blueprint](CONFIGURATION_STUDIO_BLUEPRINT.md) and its [visual walkthrough](configuration-studio.html) before assigning work to a developer or coding agent. The blueprint includes target scopes, role matrix, component registry, form JSON contract, proposed API endpoints, data model, security constraints, offline POS behavior, acceptance criteria and phased implementation.

## 9. Repository entry points

- `index.html`: device/theme preview launcher.
- `app.html`: interactive demo surfaces and Developer Access hub.
- `studio/index.html`: isolated Configuration Studio sandbox; local-only and not integrated with current apps.
- `docs/CONFIGURATION_STUDIO_BLUEPRINT.md` and `docs/configuration-studio.html`: full product/engineering spec and visual guide for the future configurable product layer.
- `assets/`: logo assets.
- `docs/ARCHITECTURE_FLOWCHARTS.md`: Mermaid source for the target workflows.
- `docs/API_ARCHITECTURE.md` and `docs/api-architecture.html`: proposed REST endpoints, JSON contracts, current localStorage inventory, Drift/SQLite tables, PostgreSQL model and Spring Boot package design.
- `docs/RESPONSIVE_DEVICE_MATRIX.md`: viewport and QA matrix.
- `docs/QUICK_START_HINGLISH.md`: local demo startup.
