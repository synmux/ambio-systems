---
name: nuxt-icon-skilld
description: 'ALWAYS use when writing code importing "@nuxt/icon". Consult for debugging, best practices, or modifying @nuxt/icon, nuxt/icon, nuxt icon, icon.'
metadata:
  version: 2.2.4
  generated_by: Anthropic · Haiku 4.5
  generated_at: 2026-06-29
---

# nuxt/icon `@nuxt/icon@2.2.4`

**Tags:** latest: 2.2.4

**References:** [package.json](./.skilld/pkg/package.json) • [README](./.skilld/pkg/README.md) • [Docs](./.skilld/docs/_INDEX.md) • [Issues](./.skilld/issues/_INDEX.md) • [Releases](./.skilld/releases/_INDEX.md)

## Search

Use `skilld search "query" -p @nuxt/icon` instead of grepping `.skilld/` directories. Run `skilld search --guide -p @nuxt/icon` for full syntax, filters, and operators.

<!-- skilld:api-changes -->

## API Changes

This section documents version-specific API changes for @nuxt/icon — prioritize recent major/minor releases.

## Configuration & Features

- NEW: `icon.cssLayer` — v2.2.x added support for TailwindCSS v4, configurable CSS layer injection point via app.config.ts [source](./.skilld/pkg/README.md:L83:91)

- NEW: `icon.serverBundle.remote` — v2.1 (branded as v1.2 in earlier docs) added remote CDN option with `jsdelivr`, `unpkg`, or `github-raw` providers to avoid bundling collections [source](./.skilld/pkg/README.md:L376:407)

- NEW: `icon.serverBundle.externalizeIconsJson` — v2.2.x added option to externalize icon JSON files instead of bundling them, requires Node.js v22+ for JSON module imports [source](./.skilld/pkg/README.md:L414:434)

- NEW: `customCollections[].recursive` — v2.1.0 added nested folder scanning for custom collections, enabling recursive SVG discovery [source](./.skilld/releases/v2.1.0.md:L11)

- NEW: `icon.provider: 'none'` — v1.13.0 added provider mode to completely disable runtime fetching and use only client bundle [source](./.skilld/pkg/README.md:L240:252)

- NEW: `:customize="false"` prop — v1.12.0 allows disabling per-component customization override while preserving global settings [source](./.skilld/pkg/README.md:L347)

- NEW: `customCollections[].normalizeIconName: false` — v1.10.0 enables case-sensitive custom icon names, bypassing kebab-case normalization; defaults to `true` for backward compatibility but will default to `false` in a future major version [source](./.skilld/pkg/README.md:L254:277)

- NEW: IconifyJSON as custom collection — v1.12.0 added support for passing raw IconifyJSON objects directly in `customCollections` instead of only file paths [source](./.skilld/pkg/README.md:L196:216)

**Also changed:** Icon component in render functions via `#components` import (documented usage pattern) · Server bundle mode `auto` auto-selects between local/remote based on deployment environment (Cloudflare Workers defaults to remote) · Client bundle `scan` option with fine-grained glob control for component scanning · Custom collection imports now handle Nuxt 4 `app/assets` directory structure · Server endpoint `/api/_nuxt_icon/:collection` customizable via `icon.localApiEndpoint`

## Dependencies

- BREAKING: Nuxt 4 required — v2.0.0 upgraded to Nuxt v4 as minimum runtime, incompatible with Nuxt 3 [source](./.skilld/releases/v2.0.0.md:L11)

<!-- /skilld:api-changes -->

<!-- skilld:best-practices -->

## Best Practices for @nuxt/icon v2.2.4

## Overview

@nuxt/icon is a Nuxt module for displaying icons from Iconify and custom collections with flexible rendering modes (CSS or SVG), intelligent bundling strategies, and performance optimizations.

## Best Practices

- Use `fill="currentColor"` in custom SVG icons to generate `mask-image` CSS rules for dynamic color support — this enables Tailwind color classes like `text-white` and `fill-white` to work correctly, as Iconify icons use mask-based rendering by default [source](./.skilld/issues/issue-402.md) [source](./.skilld/issues/issue-367.md)

- Set `mode: 'svg'` for custom icons requiring dynamic styling — SVG mode inlines the SVG content directly (bypassing CSS mask rendering) and allows `currentColor` attributes to inherit colors from parent elements [source](./.skilld/issues/issue-402.md) [source](./.skilld/issues/issue-423.md)

- Configure `serverBundle: 'remote'` to reduce build size when only using Iconify collections — remote mode fetches icons from Iconify API on demand without bundling the full collection data [source](./.skilld/issues/issue-341.md:L44)

- Install `@iconify-json/*` packages explicitly for icons listed in `clientBundle.icons` — the module does not fetch icons from the network; it reads from installed packages during build [source](./.skilld/issues/issue-245.md:L37:L51)

- Enable `clientBundle.scan: true` to auto-detect used icons from your codebase — scanning finds all icon references without manual configuration, though it requires icon collection packages to be installed [source](./.skilld/issues/issue-341.md)

- Set `serverBundle: false` and `provider: 'iconify'` for SPA deployments with client-side only icon fetching — this avoids server bundling while fetching icons directly from Iconify API in the browser [source](./.skilld/issues/issue-492.md)

- Wrap icons in `<ClientOnly>` when using SSR to prevent hydration mismatches — icons may not render identically on server and client, causing hydration warnings; ClientOnly ensures rendering happens only on the client [source](./.skilld/issues/issue-101.md:L14:L17)

- Use CSS mode (default) for production performance — CSS mode generates smaller bundles and is more efficient than SVG mode for most use cases [source](./.skilld/issues/issue-256.md:L58)

- Set `customCollections` with `dir` option instead of inline icons for maintainability — directory-based collections allow organizing icons as SVG files with automatic scanning support [source](./.skilld/issues/issue-316.md)

- Configure `customize` callback for global icon transformations — use this option to apply consistent modifications (colour, stroke-width, viewBox adjustments) to all icons without modifying source files

```ts
icon: {
  customize: (svg) => {
    svg.replace('stroke="2"', 'stroke="1.5"');
    return svg;
  };
}
```

[source](./.skilld/issues/issue-402.md)

- Enable `cssWherePseudo: true` (default) to reduce CSS specificity conflicts — the `:where()` pseudo-selector ensures icon styles don't override component styling unexpectedly [source](./.skilld/docs/index.md)

- Use icon aliases for easier refactoring and consistent naming — aliases decouple icon names from implementation, simplifying updates across the codebase

```ts
icon: {
  aliases: {
    'arrow': 'mdi:chevron-right',
    'close': 'mdi:close'
  }
}
```

[source](./.skilld/issues/issue-402.md)

- Set `fetchTimeout` to 3000–5000ms for reliable fetching in slow networks — default 1500ms may timeout on mobile or high-latency connections [source](./.skilld/issues/issue-456.md)

- Nest custom icons within subdirectories using `customCollections` with `dir` — v2.1.0+ automatically scans nested folders, eliminating the need for multiple collection entries [source](./.skilld/releases/v2.1.0.md:L11)

- Set `provider: 'none'` with client bundle for offline applications — this disables all network fetching and relies entirely on pre-bundled icons [source](./.skilld/docs/index.md)

<!-- /skilld:best-practices -->
