---
name: vue-skilld
description: 'The progressive JavaScript framework for building modern web UI. ALWAYS use when editing or working with *.vue files or code importing "vue". Consult for debugging, best practices, or modifying vue, core.'
metadata:
  version: 3.5.40
  generated_by: cached
  generated_at: 2026-07-18
---

# vuejs/core `vue@3.5.40`

**Tags:** csp: 1.0.28-csp, v2-latest: 2.7.16, legacy: 2.7.16

**References:** [package.json](./.skilld/pkg/package.json) • [README](./.skilld/pkg/README.md) • [Docs](./.skilld/docs/_INDEX.md) • [Issues](./.skilld/issues/_INDEX.md) • [Discussions](./.skilld/discussions/_INDEX.md) • [Releases](./.skilld/releases/_INDEX.md)

## Search

Use `skilld search "query" -p vue` instead of grepping `.skilld/` directories. Run `skilld search --guide -p vue` for full syntax, filters, and operators.

<!-- skilld:api-changes -->

## API Changes

This section documents version-specific API changes in Vue 3.x — focus on recent minor/major releases where breaking changes and new APIs supersede older training data.

### Breaking Changes — v3.4

- BREAKING: Global JSX namespace removed in v3.4 — no longer registers `JSX` global. Use `jsxImportSource: 'vue'` in `tsconfig.json` or `/* @jsxImportSource vue */` per-file. Reference `vue/jsx` to restore pre-3.4 behaviour [source](./.skilld/releases/blog-3.4.md#global-jsx-namespace)

- BREAKING: `@vnodeXXX` event listeners now a compiler error — use `@vue:XXX` format instead. Previously a deprecation warning [source](./.skilld/releases/blog-3.4.md#other-removed-features)

- BREAKING: `v-is` directive removed — use `is` attribute with `vue:` prefix (e.g. `is="vue:ComponentName"`). Deprecated in 3.3, removed in 3.4 [source](./.skilld/releases/blog-3.4.md#other-removed-features)

- BREAKING: `app.config.unwrapInjectedRef` removed in v3.4 — was deprecated and enabled by default in 3.3, now removed entirely. Ref unwrapping in injections is always on [source](./.skilld/releases/blog-3.4.md#other-removed-features)

- DEPRECATED: Reactivity Transform removed — marked deprecated in 3.3, removed in 3.4. Users can use Vue Macros plugin as replacement [source](./.skilld/releases/blog-3.4.md#other-removed-features)

### New APIs — v3.5

- NEW: `useTemplateRef()` — new composable for obtaining template refs via runtime string ID (replaces static ref name binding). Supports dynamic ref IDs, unlike the previous `ref` attribute approach [source](./.skilld/releases/blog-3.5.md#usetemplateref)

- NEW: `useId()` — generates unique stable IDs across server and client renders, eliminates hydration mismatches for form labels and accessibility attributes [source](./.skilld/releases/blog-3.5.md#useid)

- NEW: `onWatcherCleanup()` — registers cleanup callbacks within watcher scope, replaces manual return function pattern for aborting stale requests or cancelling side effects [source](./.skilld/releases/blog-3.5.md#onwatchercleanup)

- NEW: `hydrateOnVisible()` — async component hydration strategy that defers hydration until component becomes visible (via Intersection Observer), reduces initial hydration work [source](./.skilld/releases/blog-3.5.md#lazy-hydration)

- NEW: `useHost()`, `useShadowRoot()` — composables for accessing host element and shadow root within custom elements (via `defineCustomElement`), replaces `this.$host` for composition API [source](./.skilld/releases/blog-3.5.md#custom-elements-improvements)

- NEW: `data-allow-mismatch` attribute — suppresses hydration mismatch warnings on elements where client/server values differ intentionally (e.g. dates). Optionally scoped to types: `text`, `children`, `class`, `style`, `attribute` [source](./.skilld/releases/blog-3.5.md#data-allow-mismatch)

- NEW: `Teleport defer` prop — mounts Teleport component after current render cycle, allows teleporting to targets rendered later in the same frame [source](./.skilld/releases/blog-3.5.md#deferred-teleport)

### Stabilized APIs — v3.4

- STABLE: `defineModel` stabilized from experimental in v3.3 to stable in v3.4 — simplifies `v-model` implementation by combining prop declaration and event emission. Also improved support for modifiers [source](./.skilld/releases/blog-3.4.md#definemodel-is-now-stable)

- STABLE: Reactive Props Destructure stabilized in v3.5 — destructured props from `defineProps` now reactive by default. Wrap in getter for use in `watch()` or composables [source](./.skilld/releases/blog-3.5.md#reactive-props-destructure)

### New APIs — v3.3 (Still Current)

- NEW: `defineSlots` macro — declares expected slots and their prop types. Type-only, no runtime effect. Provides IDE hints and type checking for slot props [source](./.skilld/releases/blog-3.3.md#typed-slots-with-defineslots)

- NEW: `defineOptions` macro — sets component options directly in `<script setup>` without separate `<script>` block (e.g. `defineOptions({ inheritAttrs: false })`) [source](./.skilld/releases/blog-3.3.md#defineoptions)

- NEW: `toValue()` utility — normalizes values, refs, and getters into raw values. Opposite of `toRef()`. Use in composables to accept getter functions as reactive sources [source](./.skilld/releases/blog-3.3.md#better-getter-support-with-toref-and-tovalue)

- ENHANCED: `toRef()` — now accepts values, getters, or existing refs and normalizes them into refs. Getter refs are more efficient than `computed` when performing simple property access [source](./.skilld/releases/blog-3.3.md#better-getter-support-with-toref-and-tovalue)

- NEW: `jsxImportSource` support — use `jsxImportSource: 'vue'` in `tsconfig.json` to opt-in to per-file JSX namespace instead of global (for React coexistence). Becomes required in 3.4 [source](./.skilld/releases/blog-3.3.md#jsx-import-source-support)

**Also changed:** Generic `<script setup>` type parameters via `generic="T"` attribute (v3.3) · Imported types in `defineProps` / `defineEmits` (v3.3) · More ergonomic `defineEmits` with object syntax (v3.3) · `v-bind` same-name shorthand `:id :src :alt` (v3.4) · Template parser rewritten for 2x speed (v3.4)
<!-- /skilld:api-changes -->

<!-- skilld:best-practices -->

## Best Practices

- Prefer `<script setup>` for component composition — Vue automatically exposes top-level variables to templates, reducing boilerplate and improving readability [source](./.skilld/docs/guide/essentials/reactivity-fundamentals.md#script-setup)

- Stabilise props passed to child components to minimise unnecessary re-renders — only children whose props actually change will update, dramatically reducing update performance in large lists [source](./.skilld/docs/guide/best-practices/performance.md#props-stability)

- Return plain objects containing refs from composables, not reactive objects — enables destructuring whilst retaining reactivity, which is the idiomatic pattern [source](./.skilld/docs/guide/reusability/composables.md#return-values)

- Start composable function names with "use" by convention — communicates that a function encapsulates stateful logic and Composition API lifecycle rules apply [source](./.skilld/docs/guide/reusability/composables.md#naming)

- Use `computed()` properties instead of methods for derived values that depend on reactive state — computed properties cache their results, avoiding unnecessary recalculation if dependencies haven't changed [source](./.skilld/docs/guide/essentials/computed.md#computed-caching-vs-methods)

- Apply `v-memo` to expensive sub-trees or large v-for lists to skip updates conditionally — gives fine-grained control over re-rendering without restructuring components [source](./.skilld/docs/guide/best-practices/performance.md#v-memo)

- Accept refs or getter functions in composable arguments and normalise them with `toValue()` — allows composables to work seamlessly with static values, refs, and computed properties [source](./.skilld/docs/guide/reusability/composables.md#input-arguments)

- Clean up side effects in `onUnmounted()` lifecycle hooks — prevents memory leaks from accumulated event listeners, timers, or subscriptions as component instances are destroyed [source](./.skilld/docs/guide/reusability/composables.md#side-effects)

- Never use non-trusted content as a component template — Vue templates compile to JavaScript; user-provided templates enable arbitrary code execution and cannot be safely sandboxed [source](./.skilld/docs/guide/best-practices/security.md#rule-no-1-never-use-non-trusted-templates)

- Wrap dynamic components with `<KeepAlive :max="limit">` to preserve component state and cache size — sets an LRU cache limit preventing unbounded memory growth in systems that frequently switch between many component instances [source](./.skilld/docs/guide/built-ins/keep-alive.md#max-cached-instances)

- Only perform DOM-specific side effects in `onMounted()` when building SSR-enabled applications — server environments have no DOM; mounting hooks run exclusively in the browser, safely isolating side effects [source](./.skilld/docs/guide/reusability/composables.md#side-effects)

- Beware of deep watchers on large data structures — deep traversal can be expensive; only enable when genuinely necessary and document the performance trade-off [source](./.skilld/docs/guide/essentials/watchers.md#deep-watchers)

- Link form labels explicitly with `for` and `id` attributes rather than nesting inputs inside labels — provides better support for assistive technology and clearer semantic HTML [source](./.skilld/docs/guide/best-practices/accessibility.md#labels)

- Virtualise rendering for large lists to display only visible items and nearby rows — renders hundreds of DOM nodes instead of thousands, preserving performance even with 100,000+ list items [source](./.skilld/docs/guide/best-practices/performance.md#virtualize-large-lists)

<!-- /skilld:best-practices -->
