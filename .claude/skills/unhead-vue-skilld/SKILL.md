---
name: unhead-vue-skilld
description: 'ALWAYS use when writing code importing "@unhead/vue". Consult for debugging, best practices, or modifying @unhead/vue, unhead/vue, unhead vue, unhead.'
metadata:
  version: 3.1.1
  generated_by: Anthropic · Haiku 4.5
  generated_at: 2026-05-31
---

# unjs/unhead `@unhead/vue@3.1.1`

**Tags:** next: 3.0.0-beta.9, beta: 3.0.0-beta.12, rc: 3.0.0-rc.4

**References:** [package.json](./.skilld/pkg/package.json) • [README](./.skilld/pkg/README.md) • [Docs](./.skilld/docs/_INDEX.md) • [Issues](./.skilld/issues/_INDEX.md) • [Discussions](./.skilld/discussions/_INDEX.md) • [Releases](./.skilld/releases/_INDEX.md)

## Search

Use `skilld search "query" -p @unhead/vue` instead of grepping `.skilld/` directories. Run `skilld search --guide -p @unhead/vue` for full syntax, filters, and operators.

<!-- skilld:api-changes -->

## API Changes

This section documents version-specific API changes — prioritize recent major/minor releases.

## Breaking Changes in v3 (v2 → v3 Migration)

- BREAKING: `renderDOMHead()` and `renderSSRHead()` — now synchronous, remove `await` calls. These functions no longer return promises [source](./.skilld/releases/v3.0.0.md:L200:L201)

- BREAKING: Vite plugin import path — `@unhead/addons/vite` renamed to framework-specific subpath with named `Unhead` export. Change from `import unhead from '@unhead/addons/vite'` to `import { Unhead } from '@unhead/vue/vite'` [source](./.skilld/releases/v3.0.0.md:L202:L215)

- BREAKING: Strict `Link` / `Script` / `Meta` type narrowing — unions no longer fall back to `GenericLink` / `GenericScript`, so custom `rel` / `type` values require `satisfies GenericLink` / `satisfies GenericScript`. Meta `content` is now required; use `content: null` explicitly to remove a meta tag [source](./.skilld/releases/v3.0.0.md:L217:L220)

- BREAKING: Dropped deprecated property names — `children` → `innerHTML`, `hid`/`vmid` → `key`, `body: true` → `tagPosition: 'bodyClose'`, `useServerHead`/`useServerSeoMeta` → `useHead`/`useSeoMeta`, `createHeadCore` → `createUnhead` [source](./.skilld/releases/v3.0.0.md:L221:L232)

- BREAKING: Plugins now opt-in — `TemplateParamsPlugin` and `AliasSortingPlugin` no longer included by default; import and register explicitly if needed [source](./.skilld/releases/v3.0.0.md:L237:L240)

- BREAKING: Hooks removed/changed — `init` hook removed, `dom:renderTag`/`dom:rendered` hooks deprecated (will be removed in v4), `dom:beforeRender` is now synchronous (no async handlers) [source](./.skilld/releases/v3.0.0.md:L241:L246)

- BREAKING: Type renames — `Head` → `HeadTag`, `MetaFlatInput` → `MetaFlat`, `RuntimeMode` removed, `@unhead/schema` → `unhead/types`, `@unhead/shared` → `unhead` [source](./.skilld/releases/v3.0.0.md:L247:L256)

- BREAKING: CJS removed — all packages are ESM-only [source](./.skilld/releases/v3.0.0.md:L233:L235)

- BREAKING: Path imports changed — `@unhead/vue/legacy` → `@unhead/vue/client` or `@unhead/vue/server` (legacy path still works with deprecation warning), `mode` option on entries removed [source](./.skilld/releases/v3.0.0.md:L226:L232)

## New APIs in v3.0.0

- NEW: `ValidatePlugin` — validates resolved head output and warns about common mistakes (missing titles, duplicate meta tags, contradictory preload priorities, render-blocking scripts, late charset, too many fetchpriority hints). Includes v2 migration rules that detect deprecated property names. Tree-shakeable with ESLint-style flat config [source](./.skilld/releases/v3.0.0.md:L83:L101)

- NEW: `CanonicalPlugin` — auto-generates `<link rel="canonical">` tags and resolves relative URLs in `og:image`, `twitter:image`, and `og:url`. Includes query parameter filtering (strips tracking params like `utm_source`, `fbclid`, `gclid` by default), trailing slash normalization, and automatic hash fragment stripping [source](./.skilld/releases/v3.0.0.md:L103:L121)

- NEW: `MinifyPlugin` — minifies inline `<script>` and `<style>` tag content during SSR using lightweight pure-JS minifiers with zero native dependencies. Companion utilities `minifyJS`, `minifyCSS`, `minifyJSON` available via `unhead/minify` [source](./.skilld/releases/v3.0.0.md:L123:L135)

- NEW: `createStreamableHead()` — enables streaming SSR support. Import from `@unhead/vue/stream/server` on server and `@unhead/vue/stream/client` on client. Head tags update dynamically as suspense boundaries resolve. Server-side returns `{ head, wrapStream }` to wrap Vue stream [source](./.skilld/releases/v3.0.0.md:L17:L36)

- NEW: `onRendered` callback option — callback on `useHead()` that fires when DOM head is updated, enabling synchronization with DOM patches [source](./.skilld/releases/v3.0.0.md:L178)

- NEW: `tagWeight` option on `createHead()` — override default CAPO tag weight function for custom tag sorting [source](./.skilld/releases/v3.0.0.md:L179)

- NEW: Unified Vite plugin `Unhead` — replaces manual composition of addons + streaming plugin + framework glue. Single import `@unhead/vue/vite` provides tree-shaking, `useSeoMeta` → `useHead` transform, inline minification, streaming SSR, dev-mode ValidatePlugin auto-injection, and Vite DevTools integration [source](./.skilld/releases/v3.0.0.md:L40:L58)

- NEW: `@unhead/vue/stream/iife` export — low-level streaming API for direct IIFE injection with correct TypeScript types [source](./.skilld/releases/v3.0.0.md#vue)

- NEW: HookableCore — lighter hook system replacing `hookable` with sync-only hooks, reducing bundle size [source](./.skilld/releases/v3.0.0.md:L173)

- NEW: `useHeadSafe()` style whitelist — now whitelists CSS styles for safe usage [source](./.skilld/releases/v3.0.0.md:L169)

## New APIs in v3.1.0

- NEW: Streaming mode default changed from `async` to `inline` — reduces TTFB; async mode now fixed for production Vite builds via `this.emitFile()` so script src references real hashed assets [source](./.skilld/releases/v3.1.0.md:L49:L64)

- NEW: Streaming `nonce` option — forwarded on every injected `<script>` tag for CSP support [source](./.skilld/releases/v3.1.0.md:L63)

- NEW: `StreamingGlobal` type — shared type ensuring server bootstrap, client, and injected IIFE agree on `window.__unhead__` shape [source](./.skilld/releases/v3.1.0.md:L63)

- NEW: Bundler-agnostic streaming plugin — unplugin factory at `@unhead/vue/bundler` with first-class webpack entry alongside Vite. Framework packages now expose `Unhead({ streaming: true })` for bundler selection [source](./.skilld/releases/v3.1.0.md:L49:L61)

- NEW: `@unhead/cli` package — migration and validation CLI with `audit`, `migrate`, `validate-html`, `validate-url` commands [source](./.skilld/releases/v3.1.0.md:L9:L26)

- NEW: `@unhead/eslint-plugin` — flat-config ESLint plugin with v2→v3 migration autofixes based on ValidatePlugin rules [source](./.skilld/releases/v3.1.0.md:L28:L47)

**Also changed:** `blocking` attribute support on scripts/stylesheets · `@unhead/react/helmet` compat export · `fediverse:creator` meta tag · `useScript()` consolidated into core · Schema.org: 12 new nodes added · `resolveTags()` composable pipeline · Support union rel/type in defineLink and defineScript

<!-- /skilld:api-changes -->

<!-- skilld:best-practices -->

## @unhead/vue v3.1.1 Best Practices

## Best Practices

- Use reactive state with computed properties instead of calling `useHead()` in watchers — each watcher trigger creates a new entry, whereas reactive refs update the existing one automatically [source](./.skilld/docs/0.vue/head/guides/1.core-concepts/0.reactivity-and-context.md#solution-4-using-reactive-state-recommended)

- Call `injectHead()` at the top level of setup before async operations to grab the head instance reference — enables passing the head instance to `useHead()` inside async functions and lifecycle hooks where context would be lost [source](./.skilld/docs/0.vue/head/guides/1.core-concepts/0.reactivity-and-context.md#solution-3-using-injectheadlangts)

- Use `useHeadSafe()` instead of `useHead()` when handling untrusted user-generated content or third-party data — implements an XSS protection whitelist that silently strips dangerous tags and attributes [source](./.skilld/docs/head/7.api/composables/1.use-head-safe.md#how-it-works)

- Prefer `useSeoMeta()` for defining SEO and social sharing meta tags — provides type-safe API with 100+ pre-configured tags, auto-handles `name` vs `property` attributes, and prevents typos and common mistakes [source](./.skilld/docs/head/7.api/composables/3.use-seo-meta.md#basic-usage)

- Define `titleTemplate` once in your app entry or layout, not on individual pages — allows page components to set just the page title, and the template applies automatically across your site for consistent branding [source](./.skilld/docs/head/1.guides/1.core-concepts/1.titles.md#how-do-i-add-a-site-name-to-all-titles)

- Use `templateParams` with placeholders like `%siteName` and `%separator` in your head tags — enables dynamic values and consistent branding across multiple tags without hardcoding strings [source](./.skilld/docs/head/1.guides/plugins/6.template-params.md#what-are-template-params)

- Wrap third-party script loading in a composable that uses `useScript()` — leverages automatic singleton deduplication so scripts with the same `src` or `key` load only once globally, preventing duplicate loads across components [source](./.skilld/docs/head/1.guides/1.core-concepts/9.loading-scripts.md#creating-reusable-script-composables)

- Use the `proxy` feature of `useScript()` to call script functions before the script finishes loading — function calls are queued and executed once the script loads, working safely during server-side rendering and resilient to script blocking [source](./.skilld/docs/head/1.guides/1.core-concepts/9.loading-scripts.md#how-do-i-call-script-functions-before-loading-completes)

- Place analytics and non-critical scripts at `tagPosition: 'bodyClose'` instead of the head — prevents non-essential scripts from blocking initial page render and improves perceived performance metrics [source](./.skilld/docs/head/1.guides/1.core-concepts/2.positions.md#common-use-cases)

- The Unhead Vite plugin automatically removes server-only composables from client bundles via tree-shaking — calls to `useSchemaOrg()` and deprecated `useServerHead` variants are stripped from client builds, reducing bundle size [source](./.skilld/docs/head/1.guides/build-plugins/1.tree-shaking.md#what-does-it-do)

- Enable streaming SSR for applications with async components and Suspense boundaries — injects DOM update patches into the response stream as each boundary resolves, allowing head tags from async components to reach the client [source](./.skilld/docs/0.vue/head/guides/1.core-concepts/5.streaming.md#how-it-works)

- Use custom `key` attributes on tags for explicit deduplication control — any tag can be overridden or removed later by referencing the same key, enabling fine-grained management of verification tags and third-party integrations [source](./.skilld/docs/head/1.guides/1.core-concepts/6.handling-duplicates.md#how-do-i-use-custom-keys-for-deduplication)

- Unhead automatically integrates with Vue's component lifecycle — head entries are removed when components unmount, deactivated during keep-alive transitions, and reactivated on re-entry, preventing memory leaks and keeping tags in sync [source](./.skilld/docs/0.vue/head/guides/1.core-concepts/0.reactivity-and-context.md#how-does-component-lifecycle-affect-head-tags)

- Avoid calling `useHead()` inside watchers or effect functions — this creates duplicate entries on each trigger; instead use reactive state (refs, computed) directly in the `useHead()` input, and they will update automatically [source](./.skilld/docs/0.vue/head/guides/1.core-concepts/0.reactivity-and-context.md#can-i-use-usehead-inside-a-watcher)
<!-- /skilld:best-practices -->
