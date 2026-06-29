---
name: unhead-vue-skilld
description: 'ALWAYS use when writing code importing "@unhead/vue". Consult for debugging, best practices, or modifying @unhead/vue, unhead/vue, unhead vue, unhead.'
metadata:
  version: 3.1.6
  generated_by: Anthropic · Haiku 4.5
  generated_at: 2026-06-29
---

# unjs/unhead `@unhead/vue@3.1.6`

**Tags:** next: 3.0.0-beta.9, beta: 3.0.0-beta.12, rc: 3.0.0-rc.4

**References:** [package.json](./.skilld/pkg/package.json) • [README](./.skilld/pkg/README.md) • [Docs](./.skilld/docs/_INDEX.md) • [Issues](./.skilld/issues/_INDEX.md) • [Discussions](./.skilld/discussions/_INDEX.md) • [Releases](./.skilld/releases/_INDEX.md)

## Search

Use `skilld search "query" -p @unhead/vue` instead of grepping `.skilld/` directories. Run `skilld search --guide -p @unhead/vue` for full syntax, filters, and operators.

<!-- skilld:api-changes -->

## API Changes

This section documents version-specific API changes — prioritize recent major/minor releases.

### Breaking Changes (v3.0.0)

- BREAKING: `renderDOMHead()` and `renderSSRHead()` now synchronous — remove `await` keyword, these functions no longer return promises [source](./.skilld/releases/v3.0.0.md#breaking-changes:L198:L201)

- BREAKING: `children` property deprecated — replace with `innerHTML` in script/style tags to set inline content [source](./.skilld/docs/0.vue/head/guides/0.get-started/1.migration.md#legacy-property-names:L22:L31)

- BREAKING: `hid` / `vmid` property deprecated — replace with `key` property to uniquely identify meta tags [source](./.skilld/docs/0.vue/head/guides/0.get-started/1.migration.md#legacy-property-names:L33:L44)

- BREAKING: `body: true` property deprecated — replace with `tagPosition: 'bodyClose'` to inject scripts at end of body [source](./.skilld/docs/0.vue/head/guides/0.get-started/1.migration.md#legacy-property-names:L46:L56)

- BREAKING: `useServerHead()`, `useServerHeadSafe()`, `useServerSeoMeta()` removed — use `useHead()`, `useHeadSafe()`, `useSeoMeta()` instead, or wrap in `if (import.meta.server)` for server-only logic [source](./.skilld/releases/v3.0.0.md#dropped-deprecations:L228)

- BREAKING: `createHeadCore()` removed — import `createHead` from `@unhead/vue/server` or `@unhead/vue/client` depending on context [source](./.skilld/docs/0.vue/head/guides/0.get-started/1.migration.md#vue-legacy-exports-removed:L114:L121)

- BREAKING: `@unhead/vue/legacy` export path removed — use `/client` or `/server` subpath imports explicitly [source](./.skilld/releases/v3.0.0.md#vue-legacy-exports-removed:L230)

- BREAKING: Type `Head` renamed to `HeadTag` — update imports and type annotations to use new name [source](./.skilld/docs/0.vue/head/guides/0.get-started/1.migration.md#type-changes:L180:L182)

- BREAKING: CommonJS removed, ESM-only — all packages must be imported via ESM (`import` syntax), no more `require()` [source](./.skilld/releases/v3.0.0.md:L233)

- BREAKING: `TemplateParamsPlugin` and `AliasSortingPlugin` now opt-in — import and register explicitly if needed for template variable substitution and tag alias sorting [source](./.skilld/releases/v3.0.0.md:L237:L239)

- BREAKING: `init` hook removed — no longer available in hook lifecycle [source](./.skilld/docs/0.vue/head/guides/0.get-started/1.migration.md:L151)

- BREAKING: Vite plugin import changed — use named `Unhead` export from `@unhead/vue/vite` instead of default export from `@unhead/addons/vite` [source](./.skilld/releases/v3.0.0.md#build-plugins:L206:L214)

- BREAKING: `headEntries()` method deprecated — access entries via `head.entries` Map instead: `[...head.entries.values()]` [source](./.skilld/docs/0.vue/head/guides/0.get-started/1.migration.md#core-api-changes:L127:L132)

- BREAKING: `resolveUnrefHeadInput()` removed — reactive resolution now happens automatically during `useHead()` calls [source](./.skilld/docs/0.vue/head/guides/0.get-started/1.migration.md:L171)

- BREAKING: Link/Script/Meta types now strict — union types no longer fall back to generic `GenericLink`/`GenericScript`, enforce per-tag constraints (e.g. preload requires `as` attribute), custom `rel`/`type` need `satisfies` assertion [source](./.skilld/releases/v3.0.0.md#strict-types:L217:L219)

- BREAKING: `dom:renderTag`, `dom:rendered` hooks deprecated — use `onRendered` option on `useHead()` instead for accessing resolved head after DOM update [source](./.skilld/docs/0.vue/head/guides/0.get-started/1.migration.md:L152:L153)

- BREAKING: `mode` option on head entries removed — use client/server `createHead` imports to control entry scope [source](./.skilld/docs/0.vue/head/guides/0.get-started/1.migration.md:L134:L143)

### New APIs (v3.0.0)

- NEW: `onRendered` callback option — pass callback to `useHead()` to access resolved head entry after DOM updates: `useHead({...}, { onRendered: () => {...} })` [source](./.skilld/releases/v3.0.0.md:L178)

- NEW: `tagWeight` option on `createHead()` — override default CAPO tag weight function for custom tag sorting during rendering [source](./.skilld/releases/v3.0.0.md:L179)

- NEW: `ValidatePlugin` — inspects resolved head output and warns about common mistakes (missing titles, duplicate meta tags, preload priority conflicts, late charset, render-blocking scripts, excessive fetchpriority, preconnect without crossorigin) and v2 migration issues, auto-injected in dev via Vite plugin [source](./.skilld/releases/v3.0.0.md#validateplugin:L83:L101)

- NEW: `CanonicalPlugin` — auto-generates `<link rel="canonical">` tags, resolves relative URLs to absolute in og:image/twitter:image/og:url, filters query parameters (strips utm_source, fbclid, gclid by default), normalizes trailing slashes, strips hash fragments [source](./.skilld/releases/v3.0.0.md#canonical-plugin:L103:L121)

- NEW: `MinifyPlugin` — minifies inline `<script>` and `<style>` tag content during SSR using lightweight pure-JS minifiers, safe for edge/serverless [source](./.skilld/releases/v3.0.0.md#minifyplugin:L123:L135)

- NEW: `createStreamableHead()` — enables streaming SSR support, head tags update dynamically as suspense boundaries resolve during streaming, server-side collects entries in queue stub at `window.__unhead__` [source](./.skilld/releases/v3.0.0.md#streaming-ssr:L13:L36)

- NEW: `useHead()` type narrowing — types now narrow based on input, link/script/meta tags resolve to specific subtypes (e.g. `StylesheetLink`, `PreloadLink`, `ModuleScript`, `JsonLdScript`) instead of generic union for precise autocomplete and type errors [source](./.skilld/releases/v3.0.0.md#usehead-type-narrowing:L60:L78)

- NEW: Vite DevTools integration — unified `Unhead()` plugin from `@unhead/vue/vite` exposes DevTools panel with live head state, source file/line tracing, SEO overview, useScript() load status, active plugins, template params, and validation warnings [source](./.skilld/releases/v3.0.0.md#unified-vite-plugin-devtools:L40:L56)

### New Features (v3.1.0)

- NEW: `@unhead/cli` package — CLI tool for codebase auditing (lint for misuse and SEO/perf foot-guns), v2-to-v3 migration autofixes (rewrite deprecated props, wrap tag literals), HTML validation, URL validation with ValidatePlugin rules [source](./.skilld/releases/v3.1.0.md:L9:L26)

- NEW: `@unhead/eslint-plugin` — flat-config ESLint plugin with v2→v3 migration autofixes, shares validation rules from runtime `ValidatePlugin` for compile-time checking [source](./.skilld/releases/v3.1.0.md#unhead-eslint:L28:L47)

**Also changed:** `Unhead({ streaming: true })` bundler-agnostic config for Vite/webpack · `/vite` and `/bundler` subpath exports unified · `nonce` option for streaming CSP support · `InferSeoMetaPlugin` respects user-provided `twitter:card` · default streaming mode changed from `async` to `inline` · schema.org graph resolution rewrite · 12 new schema.org nodes (Dataset, MusicAlbum, PodcastSeries, TVSeries, etc.)

<!-- /skilld:api-changes -->

<!-- skilld:best-practices -->

## Best Practices

- Use reactive state (refs/computed) directly in useHead() rather than calling useHead() in watchers — changes update automatically without creating multiple entries [source](./.skilld/docs/0.vue/head/guides/1.core-concepts/0.reactivity-and-context.md#L309:L325)

- Call injectHead() at component setup time before async operations to maintain Vue's provide/inject context for later head updates [source](./.skilld/docs/0.vue/head/guides/1.core-concepts/0.reactivity-and-context.md#L156:L203)

- Use top-level await in script setup or effectScope() to preserve async context — Vue's compile-time transforms handle context automatically at the top level [source](./.skilld/docs/0.vue/head/guides/1.core-concepts/0.reactivity-and-context.md#L104:L154)

- Use useScript() with warmupStrategy for third-party scripts — preconnect for CDN connections, preload for immediately needed scripts, prefetch for scripts needed soon [source](./.skilld/docs/head/1.guides/1.core-concepts/9.loading-scripts.md#L143:L183)

- Wrap script initialization in reusable composables and rely on the singleton pattern — scripts with the same source are loaded once globally regardless of component calls [source](./.skilld/docs/head/1.guides/1.core-concepts/9.loading-scripts.md#L26:L41)

- Set tagPosition: 'bodyClose' for non-critical scripts like analytics to avoid blocking initial render [source](./.skilld/docs/head/1.guides/1.core-concepts/2.positions.md#L30:L55)

- Use tagPriority aliases ('critical', 'high', 'low') instead of numeric weights to maintain performance-optimized Capo.js ordering [source](./.skilld/docs/head/1.guides/1.core-concepts/2.positions.md#L85:L150)

- Use useSeoMeta() for SEO tags instead of useHead() — provides full TypeScript support and automatically handles name vs property attributes [source](./.skilld/docs/head/7.api/composables/3.use-seo-meta.md#L154:L217)

- Enable CanonicalPlugin({ canonicalHost: 'https://mysite.com' }) to auto-convert relative URLs to absolute in og:image, twitter:image, and canonical links — required for proper social sharing and SEO [source](./.skilld/docs/head/1.guides/plugins/canonical.md#L50:L100)

- Use InferSeoMetaPlugin() to automatically generate og:title, og:description, and twitter:card from existing title and description — reduces duplicate meta tag definitions [source](./.skilld/docs/head/1.guides/plugins/infer-seo-meta-tags.md#L7:L40)

- Enable ValidatePlugin({ root: process.cwd() }) in development to catch head tag mistakes like non-absolute URLs, missing OG companions, and typos in meta properties [source](./.skilld/docs/head/1.guides/plugins/validate.md#L19:L52)

- Use useHeadSafe() when working with user-generated content or third-party input — provides XSS protection via a strict whitelist of allowed tags and attributes [source](./.skilld/docs/head/7.api/composables/1.use-head-safe.md#L6:L22)

- Pause DOM updates during route transitions by hooking dom:beforeRender and calling renderDOMHead(head) after navigation completes — prevents jarring tag updates with Suspense components [source](./.skilld/docs/0.vue/head/guides/1.core-concepts/4.pausing-dom-rendering.md#L30:L55)
<!-- /skilld:best-practices -->
