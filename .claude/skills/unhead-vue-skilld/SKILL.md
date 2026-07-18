---
name: unhead-vue-skilld
description: 'Full-stack head manager built for Vue. ALWAYS use when writing code importing "@unhead/vue". Consult for debugging, best practices, or modifying @unhead/vue, unhead/vue, unhead vue, unhead.'
metadata:
  version: 3.1.8
  generated_by: cached
  generated_at: 2026-07-18
---

# unjs/unhead `@unhead/vue@3.1.8`

**Tags:** next: 3.0.0-beta.9, beta: 3.0.0-beta.12, rc: 3.0.0-rc.4

**References:** [package.json](./.skilld/pkg/package.json) • [README](./.skilld/pkg/README.md) • [Issues](./.skilld/issues/_INDEX.md) • [Discussions](./.skilld/discussions/_INDEX.md) • [Releases](./.skilld/releases/_INDEX.md)

## Search

Use `skilld search "query" -p @unhead/vue` instead of grepping `.skilld/` directories. Run `skilld search --guide -p @unhead/vue` for full syntax, filters, and operators.

<!-- skilld:api-changes -->

## API Changes

This section documents version-specific API changes — prioritise recent major/minor releases.

### Breaking Changes & Critical Migrations

- BREAKING: `renderDOMHead()` and `renderSSRHead()` — v3.0.0 changed from async (returning promises) to fully synchronous single-pass execution. Remove all `await` calls. [source](./.skilld/releases/v3.0.0.md#breaking-changes:L200:201)

- BREAKING: `@unhead/addons` → `@unhead/bundler` — package renamed in v3.0.0. Old name deprecated with runtime warning. Update import statements and default `unhead()` export to named `Unhead()` export. [source](./.skilld/docs/6.migration-guide/1.v3.md#@unhead/addons-%E2%86%92-@unhead/bundler:L46:97)

- BREAKING: Framework Vite plugins — v3.0.0 changed from default export to named `Unhead` export. Update `import unhead from '@unhead/vue/vite'` to `import { Unhead } from '@unhead/vue/vite'` and call as `Unhead()` not `unhead()`. [source](./.skilld/docs/6.migration-guide/1.v3.md#framework-vite-plugins:-named-`unhead`-export:L102:129)

- BREAKING: Strict type narrowing for `Link` and `Script` — v3.0.0 removed fallback to generic union types. `Link` and `Script` now enforce per-tag constraints (e.g. preload links require `as` attribute and `crossorigin`). Meta `content` is now required; use `content: null` to remove. [source](./.skilld/releases/v3.0.0.md#breaking-changes:L217:219)

- BREAKING: Legacy property names removed — v3.0.0 dropped automatic conversion. Replace `children` → `innerHTML`, `hid`/`vmid` → `key`, `body: true` → `tagPosition: 'bodyClose'`, `useServerHead` → `useHead`, `useServerHeadSafe` → `useHeadSafe`, `useServerSeoMeta` → `useSeoMeta`. [source](./.skilld/docs/6.migration-guide/1.v3.md#legacy-property-names:L135:196)

- BREAKING: `createHeadCore()` → `createUnhead()` — v3.0.0 renamed core factory function. [source](./.skilld/docs/6.migration-guide/1.v3.md#core-api-changes:L278:285)

- BREAKING: Plugins now opt-in — v3.0.0 made `TemplateParamsPlugin` and `AliasSortingPlugin` opt-in; import and register explicitly if needed. Template params like `%siteName` appear literally without the plugin. [source](./.skilld/releases/v3.0.0.md#breaking-changes:L237:239)

- BREAKING: Schema.org plugin exports — v3.0.0 removed `PluginSchemaOrg` and `SchemaOrgUnheadPlugin`. Use `UnheadSchemaOrg()` instead. [source](./.skilld/docs/6.migration-guide/1.v3.md#schema.org-plugin:L199:222)

- BREAKING: Schema.org config options — v3.0.0 changed `canonicalHost` → `host`, `canonicalUrl` → `host` + `path`. Removed `position`, `defaultLanguage`, `defaultCurrency`. [source](./.skilld/docs/6.migration-guide/1.v3.md#schema.org-config-options:L224:243)

- BREAKING: Hooks removed — v3.0.0 dropped `init` hook entirely. `dom:renderTag` and `dom:rendered` hooks deprecated (removed in v4). `dom:beforeRender` now synchronous. [source](./.skilld/releases/v3.0.0.md#breaking-changes:L241:245)

- BREAKING: CJS removed — v3.0.0 ESM-only; all `.cjs` exports gone. [source](./.skilld/releases/v3.0.0.md#breaking-changes:L233:235)

- BREAKING: Type name changes — v3.0.0 renamed `Head` → `HeadTag`, `MetaFlatInput` → `MetaFlat`, removed `RuntimeMode`. Package aliases removed: `@unhead/schema` → `unhead/types`, `@unhead/shared` → `unhead`. [source](./.skilld/releases/v3.0.0.md#breaking-changes:L247:255)

### New Features Added in v3.x

- NEW: `createStreamableHead()` — v3.0.0 added streaming SSR support. Import from `@unhead/vue/stream/server` (server) or `@unhead/vue/stream/client` (client). Head tags update dynamically as suspense boundaries resolve. [source](./.skilld/releases/v3.0.0.md#streaming-ssr:L13:36)

- NEW: Unified Vite Plugin with DevTools — v3.0.0 single `Unhead()` import replaces old manual composition. Provides tree-shaking, `useSeoMeta` transform, inline minification, streaming, auto-injected `ValidatePlugin`, and Vite DevTools integration. [source](./.skilld/releases/v3.0.0.md#unified-vite-plugin-+-devtools:L40:58)

- NEW: `ValidatePlugin()` — v3.0.0 added optional validation that warns about missing titles, duplicate meta tags, contradictory preload priorities, missing plugins, deprecated properties, and render-blocking scripts. Auto-injected in dev by unified Vite plugin. [source](./.skilld/releases/v3.0.0.md#validateplugin:L83:101)

- NEW: `CanonicalPlugin()` — v3.0.0 added auto-generation of `<link rel="canonical">` tags with query parameter filtering, trailing slash normalization, and automatic hash stripping. [source](./.skilld/releases/v3.0.0.md#canonical-plugin:L103:121)

- NEW: `MinifyPlugin()` — v3.0.0 added minification of inline `<script>` and `<style>` content during SSR using pure-JS minifiers safe for edge/serverless. Companion `MinifyTransform` available in `@unhead/bundler`. [source](./.skilld/releases/v3.0.0.md#minifyplugin:L123:135)

- NEW: `onRendered()` callback — v3.0.0 added callback option on `useHead()` to synchronise with DOM head updates and access resolved head output. [source](./.skilld/releases/v3.0.0.md#other-changes:L178)

- NEW: `tagWeight` option — v3.0.0 added customisable `tagWeight` option on `createHead()` to override default CAPO tag weight function. [source](./.skilld/releases/v3.0.0.md#other-changes:L179)

- NEW: `@unhead/cli` — v3.1.0 added command-line interface with `audit`, `migrate`, `validate-html`, and `validate-url` commands. Run via `npx -y @unhead/cli`. [source](./.skilld/releases/v3.1.0.md#unhead-cli:L9:26)

- NEW: `@unhead/eslint-plugin` — v3.1.0 added ESLint flat-config plugin for validating `useHead()` and `useSeoMeta()` code with rules from runtime `ValidatePlugin`. Install via `npm i -D @unhead/eslint-plugin`. [source](./.skilld/releases/v3.1.0.md#unhead-eslint:L28:47)

- NEW: Streaming bundler-agnostic factory — v3.1.0 moved streaming plugin from `unhead/stream/vite` to bundler-agnostic `unplugin` factory. Framework packages compose it via `Unhead({ streaming: true })` with first-class Webpack and Vite entries. Streaming gains `nonce` option for CSP, fixed `async` mode for production Vite builds, dev warning on empty server queue, and `StreamingGlobal` type. Default mode changed from `async` to `inline` for smaller TTFB. [source](./.skilld/releases/v3.1.0.md#streaming-ssr-non-vite-support:L49:63)

- NEW: `@unhead/react/helmet` — v3.0.0 added drop-in compatibility export for users migrating from `react-helmet`. [source](./.skilld/releases/v3.0.0.md#other-changes:L168)

### Enhanced Type Safety & Validation

- ENHANCED: `useHead()` type narrowing — v3.0.0 narrows types based on input. Link, script, and meta tags resolve to specific subtypes (e.g. `StylesheetLink`, `PreloadLink`, `ModuleScript`, `JsonLdScript`) instead of generic union, so autocomplete and type errors are precise. [source](<./.skilld/releases/v3.0.0.md#`usehead()`-type-narrowing:L60:80>)

- ENHANCED: `useHeadSafe()` CSS styles — v3.0.0 now whitelists CSS styles in addition to other safe properties. [source](./.skilld/releases/v3.0.0.md#other-changes:L169)

- ENHANCED: `blocking` attribute support — v3.0.0 added support for `blocking` attribute on scripts and stylesheets. [source](./.skilld/releases/v3.0.0.md#other-changes:L170)

- ENHANCED: Union rel/type in helpers — v3.1.1 added support for union `rel`/`type` in `defineLink` and `defineScript` helpers. [source](./.skilld/releases/v3.1.1.md#bug-fixes:L12)

### Minor Updates & Fixes

- ENHANCED: `fediverse:creator` meta tag — v3.0.0 added built-in support for `fediverse:creator` meta tag. [source](./.skilld/releases/v3.0.0.md#other-changes:L172)

- ENHANCED: Schema.org nodes — v3.0.0 added 12 new schema.org nodes (`Dataset`, `MusicAlbum`, `MusicGroup`, `MusicPlaylist`, `MusicRecording`, `PodcastEpisode`, `PodcastSeason`, `PodcastSeries`, `Service`, `TVEpisode`, `TVSeason`, `TVSeries`) and rewrote graph resolution for correctness. [source](./.skilld/releases/v3.0.0.md:L159:164)

- ENHANCED: `HookableCore` — v3.0.0 switched from `hookable` to lighter `HookableCore` with sync-only hooks. [source](./.skilld/releases/v3.0.0.md#other-changes:L173)

- ENHANCED: `templateParams` extensible — v3.0.0 made `templateParams` extensible via TypeScript module augmentation. [source](./.skilld/releases/v3.0.0.md#other-changes:L175)

- FIX: `useScript()` consolidation — v3.0.0 consolidated `useScript()` back into core; legacy support removed and full integration with Vue lifecycle. [source](./.skilld/releases/v3.0.0.md#other-changes:L171)

- DEPRECATED: DOM hooks — v3.0.0 deprecated `dom:renderTag` and `dom:rendered` hooks (will be removed in v4). Use plugin system or `onRendered` callback instead. [source](./.skilld/releases/v3.0.0.md#breaking-changes:L241:245)

Also changed: `resolveTags()` composable pipeline · Synchronous `transformHtmlTemplate` · Pure tree-shakeable core · Removed `ohash` and `defu` dependencies · Removed `unhead:payload` mechanism · Streaming `nonce` option for CSP · `@unhead/vue/stream/iife` exports · Schema.org `null` opt-out · Performance improvements (32% faster @unhead/vue, 17% faster core)
<!-- /skilld:api-changes -->

<!-- skilld:best-practices -->

## Best Practices

- Use `useHead()` over direct `document.title` manipulation for SSR compatibility — framework-agnostic head tag management works in both server and client contexts, whereas direct DOM manipulation fails during server-side rendering [source](./.skilld/references/@unhead/vue@3.1.8/docs/head/1.guides/1.core-concepts/1.titles.md#what-is-the-title-tag)

- Leverage `titleTemplate` with `templateParams` for consistent branding across pages — centralises branding logic and improves SEO through brand recognition [source](./.skilld/references/@unhead/vue@3.1.8/docs/head/1.guides/1.core-concepts/1.titles.md#how-do-i-add-a-site-name-to-all-titles)

- Use reactive state (refs, computed, or store selections) with `useHead()` for async updates instead of calling `useHead()` inside watchers — avoids creating duplicate head entries on each watcher trigger [source](./.skilld/references/@unhead/vue@3.1.8/docs/0.vue/head/guides/1.core-concepts/0.reactivity-and-context.md#should-i-use-refs-or-computed-getters)

- Apply `useHeadSafe()` for untrusted user input (user profiles, third-party data) instead of `useHead()` — implements a strict whitelist of allowed tags and attributes, preventing XSS attacks [source](./.skilld/references/@unhead/vue@3.1.8/docs/head/7.api/composables/1.use-head-safe.md#how-it-works)

- Call `injectHead()` at component setup time before any async operations for reliable async context handling — captures the head instance early, allowing safe updates in lifecycle hooks and event handlers [source](./.skilld/references/@unhead/vue@3.1.8/docs/0.vue/head/guides/1.core-concepts/0.reactivity-and-context.md#solution-3-using-injecthead)

- Position analytics and non-critical scripts at `'bodyClose'` using `tagPosition` to avoid blocking initial page render — improves Core Web Vitals and perceived performance [source](./.skilld/references/@unhead/vue@3.1.8/docs/head/1.guides/1.core-concepts/2.positions.md#common-use-cases)

- Register the Canonical plugin with `canonicalHost` to automatically convert relative URLs to absolute for meta tags — required for proper Open Graph, Twitter Card, and SEO canonical link handling [source](./.skilld/references/@unhead/vue@3.1.8/docs/head/1.guides/plugins/canonical.md#why-do-i-need-absolute-urls-in-meta-tags)

- Leverage the singleton pattern in `useScript()` by matching `src` or `key` to prevent duplicate script loads globally — scripts with identical identifiers load only once, reducing network overhead [source](./.skilld/references/@unhead/vue@3.1.8/docs/head/7.api/composables/4.use-script.md#smart-defaults)

- Register the ValidatePlugin in development to catch SEO and head tag mistakes early — detects non-absolute URLs, missing OG tags, typos in meta properties, and conflicting robots directives before production [source](./.skilld/references/@unhead/vue@3.1.8/docs/head/1.guides/plugins/validate.md#what-does-this-plugin-do)

- Use content arrays in meta tags for multiple verification tags with the same name instead of separate entries — prevents deduplication when you legitimately need multiple values [source](./.skilld/references/@unhead/vue@3.1.8/docs/head/1.guides/1.core-concepts/6.handling-duplicates.md#using-content-arrays)

- Enable `transformSeoMeta: true` in the Vite build plugin (default) to save ~3kb of bundle size — the transform rewrites `useSeoMeta()` calls to `useHead()` at build time, removing runtime meta-key resolution code [source](./.skilld/references/@unhead/vue@3.1.8/docs/head/1.guides/build-plugins/2.seo-meta-transform.md#what-does-it-do)

- Use `effectScope()` or `injectHead()` when `useHead()` must be called inside `onMounted`, `onUpdated`, or other lifecycle hooks — preserves component context for proper entry cleanup on unmount [source](./.skilld/references/@unhead/vue@3.1.8/docs/0.vue/head/guides/1.core-concepts/0.reactivity-and-context.md#solution-2-using-effectscope)

- Choose `<Head>` component over `useHead()` composable for template-based head management when your project prefers declarative template syntax — both APIs work equally well; choose based on code style preference [source](./.skilld/references/@unhead/vue@3.1.8/docs/0.vue/head/guides/1.core-concepts/1.components.md#what-is-the-head-component)

- Set up streaming SSR with `createStreamableHead()` in server/client entries to support async components in the `<head>` — enables head tags from suspended components to stream as Suspense boundaries resolve, matching modern SSR patterns [source](./.skilld/references/@unhead/vue@3.1.8/docs/0.vue/head/guides/1.core-concepts/5.streaming.md#setup)

<!-- /skilld:best-practices -->
