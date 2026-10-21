# VYAVANTA Standalone App Prototypes

This folder introduces isolated web prototypes alongside the existing VYAVANTA root experience. The existing `index.html` and root demo are not replaced.

## App entry points

- `index.html` — prototype launcher
- `customer/index.html` — premium customer shopping experience
- `driver/index.html` — delivery partner workflow
- `store/index.html` — merchant/store workflow

## Current prototype scope

**Customer:** category browsing, product search/filtering, quantity-based persistent cart, checkout form, dummy payment-method selection, browser-local order history, profile, order confirmation.

**Driver:** go online/offline, accept/decline a demo assignment, confirm pickup, start delivery, OTP verification (demo OTP: `2468`), earnings and partner profile.

**Store:** demo order queue, accept/reject, preparing → ready → handover, browser-local stock management, add product, sales overview, store profile.

## Deliberate integration boundary

All three prototypes use independent browser-local demo state. They are **not connected to one another yet** and do not dispatch real orders, charge payments, track live routes, send push notifications, or authenticate users. This is intentional: review each product surface and workflow first, then implement an explicit shared order adapter for existing VYAVANTA marketplace demo data.

## Branding and reference

Customer, driver and merchant surfaces use the VYAVANTA logo assets committed under `assets/vyavanta-*.webp`. Their shared theme direction is teal `#008B8A`, secondary teal `#14B8A6`, aqua `#22D4BF`, orange `#FF8A3D` and navy `#0E2A5B`. The horizontal dark logo is for deep navy/teal headers; the light logo is for light surfaces. Keep the artwork unchanged and apply contrast adjustments to the UI around it.

## Run locally

From the repository root:

```sh
python3 -m http.server 8000
```

Then open `http://localhost:8000/apps/` and select an app. No build step is required.
