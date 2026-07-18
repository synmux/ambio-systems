---
name: nuxt-icon-skilld
description: 'ALWAYS use when writing code importing "@nuxt/icon". Consult for debugging, best practices, or modifying @nuxt/icon, nuxt/icon, nuxt icon, icon.'
metadata:
  version: 2.3.1
  generated_by: cached
  generated_at: 2026-07-18
---

# nuxt/icon `@nuxt/icon@2.3.1`

**Tags:** latest: 2.3.1

**References:** [package.json](./.skilld/pkg/package.json) • [README](./.skilld/pkg/README.md) • [Docs](./.skilld/docs/_INDEX.md) • [Issues](./.skilld/issues/_INDEX.md) • [Releases](./.skilld/releases/_INDEX.md)

## Search

Use `skilld search "query" -p @nuxt/icon` instead of grepping `.skilld/` directories. Run `skilld search --guide -p @nuxt/icon` for full syntax, filters, and operators.

<!-- skilld:api-changes -->

## API Changes

This section documents version-specific API changes — prioritise recent major/minor releases.

- BREAKING: Upgrade to Nuxt v4 — v2.0.0 requires Nuxt v4 and drops support for Nuxt 3, all existing code must target Nuxt 4 runtime APIs [source](./.skilld/releases/v2.0.0.md)

- NEW: `NuxtIconBundle` Vite plugin — v2.3.0 added standalone Vite plugin for pre-bundling icons in non-Nuxt projects, accepts `icons`, `scan`, `sizeLimitKb`, and `customCollections` options [source](./.skilld/pkg/README.md:L567:586)

- NEW: `virtual:nuxt-icon-bundle/register` virtual module — v2.3.0 registers bundled icons once in entry file for standalone Vite usage [source](./.skilld/pkg/README.md:L592:593)

- NEW: `@nuxt/icon/utils` utility exports — v2.3.0 exports `IconUsageScanner`, `resolveBundleIcons`, `generateClientBundleCode`, and `init(addIcon)` for integration with custom icon stores [source](./.skilld/pkg/README.md:L607)

- NEW: `recursive` option for custom collections — v2.1.0 added ability to scan nested subfolders in custom icon collections by setting `recursive: true` in `icon.customCollections` config [source](./.skilld/releases/v2.1.0.md)

- NEW: `customCollections` option for Vite plugin — v2.3.0 Vite plugin supports custom collections identical to Nuxt module, enabled by default in plugin context [source](./.skilld/pkg/README.md:L605)

- DEPRECATED: `normalizeIconName` default value to change — currently defaults to `true` for backward compatibility but will flip to `false` in future major version, case-sensitive icon names require opt-in via `normalizeIconName: false` [source](./.skilld/pkg/README.md:L254:277)

**Also changed:** Server bundle query parsing fixed in v2.2.3 · Scoped per-instance customization via unique CSS selectors v2.2.3 · Client bundle collections resolution from rootDir/workspaceDir v2.2.4
<!-- /skilld:api-changes -->

<!-- skilld:best-practices -->

## Best Practices

- Use `fill="currentColor"` in custom SVG icons to enable CSS mask-based colourization — Iconify icons use `mask-image` styling by default, and custom icons need this attribute to generate matching CSS rules that respond to colour utilities [source](./.skilld/issues/issue-402.md)

- Set `serverBundle` to `'remote'` in serverless environments (Cloudflare Workers, Vercel Edge) to avoid bundling icon collections — reduces build time and server bundle size by fetching icons from CDN instead of inlining them [source](./.skilld/README.md:L374:410)

- Pre-bundle frequently-used icons with explicit `clientBundle.icons` list for instant first render without network requests [source](./.skilld/README.md:L462:476)

- Use literal icon names instead of dynamic template strings — static scanning only detects hardcoded icon names like `Icon name="carbon:moon"`, not dynamic constructions like ``Icon :name="`carbon:${variable}`"`` [source](./.skilld/README.md:L554:565)

- Enable `recursive: true` in custom collections to automatically include icons from nested directories — prevents needing multiple `customCollections` entries for different folder levels [source](./.skilld/README.md:L169:178)

- Set `provider: 'server'` when building SPAs (`ssr: false`) with custom collections — the Iconify API lacks custom icons, so explicit server routing is needed to serve them [source](./.skilld/README.md:L218:236)

- Configure `icon.cssLayer` to `'base'` with TailwindCSS v4 in CSS mode — ensures icon CSS rules cascade correctly in Tailwind's new layered architecture [source](./.skilld/README.md:L78:90)

- Set `normalizeIconName: false` in custom collections for case-sensitive icon names — allows `assets/my-icons/FooBar.svg` to be used as `my-icon:FooBar` without kebab-case conversion [source](./.skilld/README.md:L254:277)

- Fine-tune `clientBundle.scan` with `globInclude` and `globExclude` patterns to avoid scanning unnecessary files — reduces build time when scanning large projects [source](./.skilld/README.md:L543:552)

- Explicitly list collection names in `serverBundle.collections` when using all-in-one `@iconify/json` package — constrains the server bundle to only the collections you use instead of loading the entire 100+ MB set [source](./.skilld/README.md:L111:122)

- Define `icon.customize` in `app.config.ts` for global SVG modifications (stroke width, colours, animation) instead of repeating customization logic per component [source](./.skilld/README.md:L350:363)

- Use `provider: 'none'` with `clientBundle: { scan: true }` to disable all runtime icon fetching — forces offline-only rendering, useful for static generation or when all icons are known at build time [source](./.skilld/README.md:L240:252)

- Import Icon from `'#components'` in render functions and setup scripts — enables type-safe component access outside templates [source](./.skilld/README.md:L613:631)

- Configure separate `clientBundle` patterns in `NODE_ENV === 'test'` to enable component testing — in-browser test environments lack the internal Nuxt server routes for on-demand icon fetching [source](./.skilld/README.md:L649:679)

<!-- /skilld:best-practices -->
