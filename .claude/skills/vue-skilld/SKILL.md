---
name: vue-skilld
description: 'ALWAYS use when editing or working with *.vue files or code importing "vue". Consult for debugging, best practices, or modifying vue, core.'
metadata:
  version: 3.5.39
  generated_by: Anthropic · Haiku 4.5
  generated_at: 2026-06-29
---

# vuejs/core `vue@3.5.39`

**Tags:** csp: 1.0.28-csp, legacy: 2.7.16, v2-latest: 2.7.16

**References:** [package.json](./.skilld/pkg/package.json) • [README](./.skilld/pkg/README.md) • [Docs](./.skilld/docs/_INDEX.md) • [Issues](./.skilld/issues/_INDEX.md) • [Discussions](./.skilld/discussions/_INDEX.md) • [Releases](./.skilld/releases/_INDEX.md)

## Search

Use `skilld search "query" -p vue` instead of grepping `.skilld/` directories. Run `skilld search --guide -p vue` for full syntax, filters, and operators.

<!-- skilld:api-changes -->

## API Changes — Vue 3.5.39

This section documents version-specific API changes — prioritize recent major/minor releases.

## API Changes

NEW: `useTemplateRef()` — new in v3.5, provides a simpler way to access template refs compared to plain variable refs; matches refs by runtime string IDs rather than compile-time analysis, supporting dynamic ref bindings [source](./.skilld/docs/api/composition-api-helpers.md#usetemplateref)

NEW: `useId()` — new in v3.5, generates unique-per-application IDs stable across SSR; used for form elements and accessibility attributes without hydration mismatches [source](./.skilld/docs/api/composition-api-helpers.md#useid)

NEW: `onWatcherCleanup()` — new in v3.5, globally imported API for registering cleanup callbacks in watchers; call inside watch callbacks before potential side effects [source](./.skilld/docs/api/reactivity-core.md#onwatchercleanup)

NEW: `Teleport defer` prop — new in v3.5, allows teleporting to target elements rendered after the teleport in the template; passes `defer` to enable deferred target resolution [source](./.skilld/docs/api/built-in-components.md#teleport)

NEW: Lazy hydration strategies — new in v3.5, async components can control hydration timing via `hydrate` option; `hydrateOnIdle()`, `hydrateOnVisible()`, `hydrateOnMediaQuery()`, `hydrateOnInteraction()` available from vue [source](./.skilld/docs/guide/components/async.md)

STABLE: `defineModel()` — experimental in v3.3, stabilized in v3.4; simplifies two-way binding by automatically registering prop and emitting updates, returns a ref that can be directly mutated [source](./.skilld/releases/blog-3.4.md#definemodel-is-now-stable)

STABLE: Reactive Props Destructure — experimental in v3.3, stabilized in v3.5; destructured props from `defineProps` are now reactive by default; accessing destructured variables is compiled to access on `props` object [source](./.skilld/releases/blog-3.5.md#reactive-props-destructure)

NEW: `v-bind` same-name shorthand — new in v3.4, allows `:id :src :alt` instead of `:id="id" :src="src" :alt="alt"`; matches JavaScript more than native HTML attributes [source](./.skilld/releases/blog-3.4.md#v-bind-same-name-shorthand)

BREAKING: Global `JSX` namespace removed — v3.4 no longer registers global JSX namespace by default to avoid collision with React; use `jsxImportSource: 'vue'` in tsconfig.json or `/* @jsxImportSource vue */` per-file, or reference `vue/jsx` to restore [source](./.skilld/releases/blog-3.4.md#global-jsx-namespace)

BREAKING: Reactivity Transform removed — v3.4 removed the experimental Reactivity Transform feature; users can migrate via Vue Macros plugin instead [source](./.skilld/releases/blog-3.4.md#other-removed-features)

BREAKING: `app.config.unwrapInjectedRef` removed — v3.4 removed this config option; unwrapping injected refs is now always enabled (was deprecated in v3.3) [source](./.skilld/releases/blog-3.4.md#other-removed-features)

BREAKING: `@vnodeXXX` event listeners removed — v3.4 changed from deprecation warning to compiler error; use `@vue:XXX` listeners instead [source](./.skilld/releases/blog-3.4.md#other-removed-features)

BREAKING: `v-is` directive removed — v3.4 removed v-is; use the `is` attribute with `vue:` prefix (`is="vue:ComponentName"`) instead [source](./.skilld/releases/blog-3.4.md#other-removed-features)

NEW: `defineOptions()` — new in v3.3, allows declaring component options directly in `<script setup>` without requiring a separate `<script>` block [source](./.skilld/releases/blog-3.3.md#defineoptions)

ENHANCED: `toRef()` — enhanced in v3.3, now supports normalizing values/getters/existing refs into refs; calling `toRef` with a getter is similar to computed but more efficient [source](./.skilld/releases/blog-3.3.md#better-getter-support-with-toref-and-tovalue)

NEW: `toValue()` — new in v3.3, normalizes values/getters/refs into values; replaces `unref()` for composables that accept getters as reactive data sources [source](./.skilld/releases/blog-3.3.md#better-getter-support-with-toref-and-tovalue)

NEW: `defineSlots()` — new in v3.3, macro for declaring expected slots and their respective slot props in `<script setup>` with TypeScript; provides type hints only, no runtime implications [source](./.skilld/releases/blog-3.3.md#typed-slots-with-defineslots)

NEW: Imported and complex types support in macros — new in v3.3, `defineProps` and `defineEmits` can now use imported types and limited complex types (intersections, unions); conditional types not supported [source](./.skilld/releases/blog-3.3.md#imported-and-complex-types-support-in-macros)

NEW: Generic components — new in v3.3, `<script setup>` now accepts `generic` attribute for generic type parameters; supports multiple parameters, constraints, and defaults [source](./.skilld/releases/blog-3.3.md#generic-components)

NEW: Ergonomic `defineEmits` type syntax — new in v3.3, can declare emits as object literal with event names as keys and argument tuples as values; call signature syntax still supported [source](./.skilld/releases/blog-3.3.md#more-ergonomic-defineemits)

PERFORMANCE: Reactivity system improvements — v3.5 refactored reactivity with -56% memory usage and no behavior changes; computed props and sync effects more efficient [source](./.skilld/releases/blog-3.5.md#reactivity-system-optimizations)

**Also changed:** `useHost()` and `useShadowRoot()` for custom elements · `configureApp` option for custom elements · `shadowRoot: false` option to mount custom elements without Shadow DOM · Custom element `nonce` option · `data-allow-mismatch` attribute for hydration mismatches · Improved hydration mismatch error messages in v3.4 with error reference page

<!-- /skilld:api-changes -->

<!-- skilld:best-practices -->

## Best Practices

- Use lazy loading for route components via Vue Router's built-in support — this automatically splits components into separate chunks, improving initial page load by deferring non-critical routes. Combine with async components for optimal code splitting [source](./.skilld/docs/guide/best-practices/performance.md#code-splitting)

- Prefer type-based prop declaration with generic arguments in TypeScript `<script setup>` over runtime declaration — this provides better type inference and enables IDE autocompletion while the compiler translates it to equivalent runtime options [source](./.skilld/docs/guide/typescript/composition-api.md#typing-component-props)

- Use `toValue()` when writing composables that accept ref or getter arguments instead of raw values — it normalises both ref and getter inputs and ensures proper dependency tracking when called inside `watchEffect()` [source](./.skilld/docs/guide/reusability/composables.md#input-arguments)

- Return a plain object of refs from composables instead of a reactive object — this preserves reactivity through destructuring, whereas reactive objects lose the connection when destructured [source](./.skilld/docs/guide/reusability/composables.md#return-values)

- Keep computed properties simple and single-focused rather than combining multiple calculations into one — simpler properties are easier to test, read, and adapt to changing requirements as each value can be independently named and reused [source](./.skilld/docs/style-guide/rules-strongly-recommended.md#simple-computed-properties)

- Use `shallowRef()` and `shallowReactive()` for large immutable data structures (100k+ properties accessed per render) to avoid the overhead of deep reactivity proxies — mutations must replace the root value entirely rather than modifying nested properties [source](./.skilld/docs/guide/best-practices/performance.md#reduce-reactivity-overhead-for-large-immutable-structures)

- Keep computed property values stable when possible — in Vue 3.4+, computed properties only trigger effects when their value actually changes, reducing unnecessary effect triggers; avoid creating new objects on each compute or manually compare old values before returning [source](./.skilld/docs/guide/best-practices/performance.md#computed-stability)

- Keep template expressions simple and move complex logic to computed properties or methods — this improves readability and allows expressions to be reused and tested independently [source](./.skilld/docs/style-guide/rules-strongly-recommended.md#simple-expressions-in-templates)

- Use `v-once` for sub-trees that are bound to runtime data but never need to update — the entire sub-tree skips all future updates, improving performance for static content [source](./.skilld/docs/guide/best-practices/performance.md#v-once)

- Composables should only be called at the top level of `<script setup>` or inside the `setup()` hook (synchronously) — this is required for Vue to properly register lifecycle hooks and link watchers to the component instance to prevent memory leaks [source](./.skilld/docs/guide/reusability/composables.md#usage-restrictions)

- Use watch with getter functions instead of trying to directly watch nested properties of reactive objects — you cannot pass a property directly to `watch()`, only refs, reactive objects, getter functions, or arrays of these [source](./.skilld/docs/guide/essentials/watchers.md#watch-source-types)

- Use shallow watchers (default behaviour) and only enable deep watching when necessary — deep watchers have performance cost; prefer restructuring your data to avoid deep nesting when possible [source](./.skilld/docs/guide/essentials/watchers.md#deep-watchers)

- Never dynamically compile templates from user input or server-rendered untrusted content — Vue templates compile to JavaScript and malicious content can execute arbitrary code; always control template content directly in your code [source](./.skilld/docs/guide/best-practices/security.md#rule-no-1-never-use-non-trusted-templates)

- Use `v-memo` to conditionally skip updates for expensive sub-trees or lists when dependencies haven't changed — this is particularly useful for large `v-for` lists or complex render trees to prevent unnecessary recalculations [source](./.skilld/docs/guide/best-practices/performance.md#v-memo)
<!-- /skilld:best-practices -->
