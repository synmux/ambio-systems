---
name: nuxt-skilld
description: 'Nuxt is a free and open-source framework with an intuitive and extendable way to create type-safe, performant and production-grade full-stack web applications and websites with Vue.js. ALWAYS use when writing code importing "nuxt". Consult for debugging, best practices, or modifying nuxt.'
metadata:
  version: 4.5.0
  generated_by: cached
  generated_at: 2026-07-18
---

# nuxt/nuxt `nuxt@4.5.0`

**Tags:** 1x: 1.4.5, 2x: 2.18.1, alpha: 4.0.0-alpha.4

**References:** [package.json](./.skilld/pkg/package.json) • [README](./.skilld/pkg/README.md) • [Docs](./.skilld/docs/_INDEX.md) • [Issues](./.skilld/issues/_INDEX.md) • [Discussions](./.skilld/discussions/_INDEX.md) • [Releases](./.skilld/releases/_INDEX.md)

## Search

Use `skilld search "query" -p nuxt` instead of grepping `.skilld/` directories. Run `skilld search --guide -p nuxt` for full syntax, filters, and operators.

<!-- skilld:api-changes -->

## API Changes

This section documents version-specific API changes from Nuxt v4 — prioritizing recent major/minor releases and silent breakages.

### Breaking Changes

- BREAKING: `useHead()` type-narrowing — `unhead` v3 introduces stricter types that may surface existing type mismatches; runtime behaviour is compatible for most apps but promise input (deprecated in v2) is no longer supported [source](./.skilld/releases/v4.5.0.md:L271)

- BREAKING: `statusCode` and `statusMessage` renamed to `status` and `statusText` — old properties still work but deprecated in v4.3 in preparation for v5; Web API naming convention aligns with h3 v2 and Nitro v3 [source](./.skilld/releases/v4.3.0.md:L197:204)

- BREAKING: `unctx` v3 resolves async context bugs — improves reliability of composables in async contexts, part of long-standing async context issue fixes [source](./.skilld/releases/v4.5.0.md:L273:275)

- BREAKING: Vite 8 major upgrade — faster cold starts, Rolldown-powered internals, custom Vite plugins/config may need review against Vite migration guide [source](./.skilld/releases/v4.5.0.md:L36:43)

### New APIs

- NEW: `useLayout()` composable — read the layout resolved for the current route; returns read-only computed ref, reactive to navigation and layout changes via `definePageMeta` or `setPageLayout` [source](./.skilld/releases/v4.5.0.md:L112:129)

- NEW: Named views via filename convention — use `name@view.vue` pattern for sibling page files to populate named `<NuxtPage name="view">` outlets; `definePageMeta` read from default route file only [source](./.skilld/releases/v4.5.0.md:L131:161)

- NEW: `enabled` option for `useFetch` and `useAsyncData` — gate data fetching with reactive boolean; blocks initial fetch, `execute`/`refresh`, and watch triggers; cancels in-flight requests when toggled false [source](./.skilld/releases/v4.5.0.md:L163:181)

- NEW: `NuxtLink` prefetch slot props — custom slot now exposes `prefetch`, `prefetched`, and `shouldPrefetch` for manual prefetch control without auto-attach [source](./.skilld/releases/v4.5.0.md:L183:209)

- NEW: `import.meta.envName` — resolved Nuxt environment name available at runtime; works on both Vite and webpack/Rspack builds [source](./.skilld/releases/v4.5.0.md:L226:236)

- NEW: Experimental SSR streaming mode — enable with `experimental.ssrStreaming: true` to flush HTML shell early and stream body; auto-disables for bots/crawlers; routes with `redirect`, `cache`, `isr`, `swr`, `noScripts`, or `ssr: false` rules auto-disable streaming [source](./.skilld/releases/v4.5.0.md:L66:98)

- NEW: Stable error code system — all build/runtime errors/warnings carry stable codes (e.g. `NUXT_E1001`, `NUXT_B5001`) with inline why/fix; verbose text stripped from production builds [source](./.skilld/releases/v4.5.0.md:L102:110)

- NEW: `createUseFetch()` and `createUseAsyncData()` — create custom instances with default options; compose interceptors, headers, and defaults; auto-registered for key injection with SSR support [source](./.skilld/releases/v4.4.0.md:L14:51)

- NEW: `useAnnouncer()` composable — announce dynamic in-page changes (form submissions, loading states, results) to screen readers; use with `<NuxtAnnouncer>` component [source](./.skilld/releases/v4.4.0.md:L94:128)

- NEW: Typed layout props in `definePageMeta` — pass typed props to layouts directly from page metadata; layout props now fully typed with autocomplete and type-checking [source](./.skilld/releases/v4.4.0.md:L63:92)

- NEW: `refresh` option for `useCookie` — set `refresh: true` to extend cookie expiration on each assignment without changing value [source](./.skilld/releases/v4.4.0.md:L158:171)

- NEW: `useState` reset to default — `clearNuxtState()` now resets to initial value instead of undefined, aligning with `useAsyncData` behaviour [source](./.skilld/releases/v4.4.0.md:L174:186)

- NEW: Route rule layouts with `appLayout` — set layouts via `routeRules` centrally; useful for admin panels and shared layout patterns [source](./.skilld/releases/v4.3.0.md:L34:55)

- NEW: ISR/SWR payload extraction — `_payload.json` generation now works with ISR, SWR, and cache `routeRules`; enables cached payloads for client-side navigation [source](./.skilld/releases/v4.3.0.md:L57:74)

- NEW: Async plugin constructors for modules — `addVitePlugin()` and `addWebpackPlugin()` now accept async factory functions for lazy-loading build plugins [source](./.skilld/releases/v4.3.0.md:L164:180)

**Also changed:** `experimental.payloadExtraction: 'client'` mode (inline payload in HTML for cached routes) · `setPageLayout()` with props support · `#server` alias for clean server imports · Route groups in page meta via `route.meta.groups` · AbortController support in `useAsyncData` · `onInstall`/`onUpgrade` module lifecycle hooks · `moduleDependencies` for declaring module dependencies with version constraints · `getLayerDirectories()` utility · Enhanced chunk stability with import maps · Experimental Rolldown support · Experimental Vite Environment API · Experimental async data handler extraction · TypeScript plugin support for component renaming and go-to-definition
<!-- /skilld:api-changes -->

<!-- skilld:best-practices -->

## Nuxt Best Practices

## Best Practices

- Fix hydration mismatches immediately — hydration errors force Vue to re-render entire component trees, increasing time to interactive, causing broken interactivity and state inconsistencies. Don't ignore warnings in development console [source](./.skilld/docs/3.guide/2.best-practices/hydration.md#why-is-it-important-to-fix-them)

- Use `useFetch` or `useAsyncData` with explicit keys instead of direct `$fetch` in component setup — prevents double-fetching on server and client, forwards data through payload to avoid refetching during hydration [source](./.skilld/docs/1.getting-started/10.data-fetching.md#the-need-for-usefetch-and-useasyncdata)

- Use `useState` composable for shared state, never define `ref()` outside of setup function — global state outside setup causes memory leaks on server by sharing state across requests [source](./.skilld/docs/1.getting-started/11.state-management.md#best-practices)

- Implement lazy hydration with `hydrate-on-visible` attribute for deferred component hydration — delays loading and making interactive non-critical components until they're visible, improving time-to-interactive [source](./.skilld/docs/3.guide/2.best-practices/performance.md#lazy-hydration)

- Configure route rules for hybrid rendering to optimize per-route caching — use `prerender`, `swr` (stale-while-revalidate), `isr` (incremental static regeneration), or `ssr: false` per route based on content freshness requirements [source](./.skilld/docs/3.guide/2.best-practices/performance.md#hybrid-rendering)

- Minimize payload size with `pick` and `transform` options in data fetching composables — prevents unnecessary data from being serialized and transferred to the browser, reducing initial HTML document size [source](./.skilld/docs/1.getting-started/10.data-fetching.md#minimize-payload-size)

- Cache and share data across components by providing explicit keys to `useAsyncData` — identical keys create shared reactive state, but requires consistent handler, deep, transform, pick, getCachedData, and default options [source](./.skilld/docs/1.getting-started/10.data-fetching.md#keys)

- Enable `parallel: true` for asynchronous plugins to improve hydration performance — multiple async plugins load concurrently instead of sequentially, preventing blocking operations during the critical hydration phase [source](./.skilld/docs/3.guide/2.best-practices/plugins.md#if-async-enable-parallel)

- Defer expensive module setup logic to lifecycle hooks like `onInstall` and `onUpgrade` — prevents unnecessary work on every build and provides better developer experience, only runs when module is first installed or upgraded [source](./.skilld/docs/3.guide/4.modules/7.best-practices.md#use-lifecycle-hooks)

- Prefix all module exports with module name to avoid conflicts — all components, composables, server routes, and configuration should be prefixed (e.g., `FooButton`, `useFooData`, `/api/_foo/...`) to prevent collision with user code or other modules [source](./.skilld/docs/3.guide/4.modules/7.best-practices.md#prefix-your-exports)

- Wrap browser-only content with `ClientOnly` component to prevent hydration mismatches — allows different content to render on server (fallback slot) versus client, avoiding mismatches when using browser APIs or window object conditionals [source](./.skilld/docs/3.guide/2.best-practices/hydration.md#dynamic-content-based-on-time)

- Use `vue:error` hook in plugins for global error handling — provides a centralized handler for all Vue rendering errors, allowing error reporting framework integration that catches errors even if handled locally [source](./.skilld/docs/1.getting-started/12.error-handling.md#vue-errors)

- Use `callOnce` utility for side effects like Pinia store actions, not `useAsyncData` — `useAsyncData` is for data fetching and caching only; using it for side effects causes unintended repeated executions with nullish values [source](./.skilld/docs/1.getting-started/10.data-fetching.md#L230:240)

- Use reactive values and computed URLs with `useFetch` to automatically refetch when dependencies change — computed getter URLs and reactive query parameters trigger refetching automatically without manual watch setup, enabling dynamic data fetching patterns [source](./.skilld/docs/1.getting-started/10.data-fetching.md#computed-url)

<!-- /skilld:best-practices -->

Related: unhead-vue-skilld, vue-skilld, vue-router-skilld
