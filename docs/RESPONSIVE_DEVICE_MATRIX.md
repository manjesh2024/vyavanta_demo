# VYAVANTA Responsive Device Matrix

The HTML prototype is intended to adapt across desktop, laptop, store POS, tablet/iPad and phone viewports. These starting widths describe layout behavior, not model detection.

| Surface | Starting width | Acceptance expectation |
|---|---:|---|
| Desktop / laptop | ≥ 1200 px | Full navigation, analytics, dense tables and multi-column panels |
| Store POS | 900–1199 px | Large touch targets, visible cart, keyboard/scanner-friendly flow |
| Tablet / iPad | 620–899 px | Compact navigation, responsive panels, portrait and landscape support |
| Android / iPhone | ≤ 619 px | Single-column content, safe-area insets, reachable actions and readable scaling |

## Brand treatment

The current VYAVANTA prototype uses text-only wordmark placeholders until the clean original master artwork is installed. Do not substitute legacy source-brand SVG approximations or crops from brand-board images. Once the master is available, test the approved light and dark variants on every surface and validate contrast without modifying the artwork.

## Test requirements

- Test 200% zoom and OS/browser text scaling.
- Check keyboard navigation, focus visibility and screen-reader semantics.
- Exercise split-screen, landscape, keyboard-visible and narrow-width states.
- Verify empty, loading, error and offline states.
- Touch targets should generally be at least 44 × 44 CSS pixels where practical.
- Validate actual iOS/Android/iPad/Windows hardware separately; browser viewport simulations are not device verification.
