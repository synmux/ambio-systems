---
name: nuxt-hints-skilld
description: 'Nuxt module that shows hints for aspects of your application such as Performance, Security, and more!. ALWAYS use when writing code importing "@nuxt/hints". Consult for debugging, best practices, or modifying @nuxt/hints, nuxt/hints, nuxt hints, hints.'
metadata:
  version: 1.1.4
  generated_by: cached
  generated_at: 2026-07-18
---

# nuxt/hints `@nuxt/hints@1.1.4`

**Tags:** latest: 1.1.4

**References:** [package.json](./.skilld/pkg/package.json) • [README](./.skilld/pkg/README.md) • [Issues](./.skilld/issues/_INDEX.md) • [Discussions](./.skilld/discussions/_INDEX.md) • [Releases](./.skilld/releases/_INDEX.md)

## Search

Use `skilld search "query" -p @nuxt/hints` instead of grepping `.skilld/` directories. Run `skilld search --guide -p @nuxt/hints` for full syntax, filters, and operators.

<!-- skilld:api-changes -->

## API Changes

This section documents version-specific API changes in @nuxt/hints v1.x, focusing on configuration and configuration API updates that affect developers using the module.

- NEW: `features` configuration object — v1.0.0-alpha.10 introduced the ability to configure individual hints features (hydration, lazyLoad, webVitals, thirdPartyScripts, htmlValidate) via `hints.features` in nuxt.config.ts [source](./.skilld/releases/v1.0.0-alpha.10.md#enhancements)

- BREAKING: Hints data now stored in `NuxtPayload.__hints` — v1.0.0-alpha.9 moved from NuxtApp augmentation to NuxtPayload, so internal access patterns changed from app-level hints to payload-level hints storage [source](./.skilld/releases/v1.0.0-alpha.9.md#refactors)

- NEW: Partial feature configuration — v1.1.1 made the features config object partial, allowing selective feature overrides instead of requiring all features to be defined [source](./.skilld/releases/v1.1.1.md#fixes)

- NEW: Feature flag options — Each feature now accepts either a boolean or an object with `logs`, `devtools`, and `options` keys for fine-grained control over logging output and devtools visibility per feature [source](./.skilld/pkg/README.md:L142:150)

- NEW: HTML-validate integration — v1.0.0 added built-in HTML validation powered by html-validate, which runs on every server-rendered response and appears in the devtools panel [source](./.skilld/releases/v1.0.0.md#enhancements)

- NEW: `wrapBroadcast` RPC utility — v1.1.2 implemented wrapBroadcast function to enhance RPC error handling in devtools communication [source](./.skilld/releases/v1.1.2.md#enhancements)

**Also changed:** SSE moved to devtools RPC v1.1.0 · Devtools header made sticky v1.1.4 · Preemptive router creation v1.1.4
<!-- /skilld:api-changes -->

<!-- skilld:best-practices -->

## Best Practices

- Disable individual features progressively when overwhelmed by logs — use the `features` object with feature-specific toggles instead of disabling the entire module [source](./.skilld/pkg/README.md:L120:L150)

- Use the object syntax with `logs: false` for specific features to suppress console output while keeping devtools panel updates — helps debug false positives without noise [source](./.skilld/pkg/README.md:L142:L150)

- Convert statically imported components to lazy-loaded using the `Lazy` prefix (e.g., `<LazyHeavyComponent>`) when the module suggests lazy-loading — this reduces client bundle size without refactoring component definitions [source](./.skilld/pkg/README.md:L88:L89)

- Use `defineAsyncComponent()` as an alternative to the `Lazy` prefix for components that the module flags as unused during SSR/hydration — enables explicit control over loading timing and fallback states [source](./.skilld/pkg/README.md:L88:L89)

- On Windows, create a `hints.config.ts` file and configure the `#hints-config` alias explicitly if module resolution fails — avoids build-time aliasing issues specific to Windows file paths [source](./.skilld/issues/issue-290.md:L28:L56)

- Wrap components with `<ClientOnly>` when intentional client-only rendering is needed — the module reports hydration differences for ClientOnly-wrapped content, which is expected behaviour and not a mismatch [source](./.skilld/issues/issue-154.md:L24:L27)

- Set `app.baseURL` in `nuxt.config.ts` before adding the module if your app runs under a non-root path — the devtools panel, telemetry endpoint, and client requests depend on this configuration to resolve correctly [source](./.skilld/issues/issue-361.md:L15:L18)

- Add `@nuxt/hints` to the `transpile` build option if module resolution fails at build time — ensures @nuxt/hints imports are processed before Vite's import analysis [source](./.skilld/issues/issue-151.md:L78:L81)

- Disable the `htmlValidate` feature if it crashes SSR responses (HTTP 500) on SVG content with nested HTML — mark this feature as `{ htmlValidate: false }` until the issue is resolved upstream [source](./.skilld/issues/issue-360.md:L1:L12)

- Prefer `hydration: true` in feature configuration over other hints when starting a new project — hydration mismatches are the highest priority blocker for SSR applications and the most actionable feedback [source](./.skilld/pkg/README.md:L132:L140)

- Test the module with HTTPS dev server (`nuxt dev --host`) if accessing from mobile devices on the same network — `crypto.randomUUID` requires a secure context on non-localhost origins [source](./.skilld/issues/issue-221.md:L12:L40)

- Review the devtools panel periodically rather than relying solely on console warnings — the devtools UI provides interactive inspection, element highlighting on hover, and editor integration that console messages cannot match [source](./.skilld/pkg/README.md:L37:L69)

- Filter out false-positive third-party script detections in Firefox by checking the script URL for extension protocols (e.g., `moz-extension://`) before taking action on audit recommendations [source](./.skilld/issues/issue-135.md:L1:L43)

<!-- /skilld:best-practices -->

Related: nitropack-skilld, prettier-skilld
