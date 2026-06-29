---
name: nuxt-hints-skilld
description: 'ALWAYS use when writing code importing "@nuxt/hints". Consult for debugging, best practices, or modifying @nuxt/hints, nuxt/hints, nuxt hints, hints.'
metadata:
  version: 1.1.3
  generated_by: Anthropic · Haiku 4.5
  generated_at: 2026-06-29
---

# nuxt/hints `@nuxt/hints@1.1.3`

**Tags:** latest: 1.1.3

**References:** [package.json](./.skilld/pkg/package.json) • [README](./.skilld/pkg/README.md) • [Issues](./.skilld/issues/_INDEX.md) • [Discussions](./.skilld/discussions/_INDEX.md) • [Releases](./.skilld/releases/_INDEX.md)

## Search

Use `skilld search "query" -p @nuxt/hints` instead of grepping `.skilld/` directories. Run `skilld search --guide -p @nuxt/hints` for full syntax, filters, and operators.

<!-- skilld:api-changes -->

## API Changes

This section documents version-specific API changes for @nuxt/hints v1.1.3.

- NEW: `features` configuration object — introduced in v1.0.0-alpha.10, allows per-feature configuration in `nuxt.config.ts` under the `hints.features` key with toggles for `hydration`, `lazyLoad`, `webVitals`, `thirdPartyScripts`, and `htmlValidate` [source](./.skilld/releases/v1.0.0-alpha.10.md)

- NEW: Feature-level options structure — each feature accepts either `boolean` (enable/disable) or `object` with `{ logs: boolean, devtools: boolean, options: {...} }` for fine-grained control, introduced in v1.0.0 [source](./.skilld/pkg/README.md:L142:L150)

**Also changed:** Features config made partial in v1.1.1 (allows selective overrides) · Html-validate integration added v1.0.0 · RPC wrapBroadcast enhancement v1.1.2

<!-- /skilld:api-changes -->

<!-- skilld:best-practices -->

## Best Practices

- Use partial feature configuration to selectively debug specific areas — configure only the feature you're fixing and disable others to reduce console noise [source](./.skilld/releases/v1.1.1.md)

- Configure features as objects with `{ logs, devtools, options }` flags rather than just booleans for granular control over whether warnings appear in console vs DevTools only [source](./.skilld/pkg/README.md:L142:L150)

- Expect hydration detection to produce false positives when components mount — the module relies on Vue's onMounted hook rather than a dedicated hydration mismatch hook, so timing differences can trigger spurious warnings [source](./.skilld/issues/issue-257.md)

- Keep the DevTools panel connected during development when using lazy-load detection — if the client disconnects, lazy-load reporting via birpc times out and crashes the dev server (fixed in v1.1.2 but still worth avoiding) [source](./.skilld/releases/v1.1.2.md)

- Disable htmlValidate or carefully manage SVG structures in your markup — the feature uses Prettier's HTML parser which cannot handle SVG-to-HTML namespace transitions (e.g., SVG with nested `<picture>` elements inside `<foreignObject>`) [source](./.skilld/issues/issue-360.md:L12:L23)

- Apply the Windows path alias workaround if #hints-config fails to resolve on Windows — use a manual alias in nuxt.config.ts to point to a local hints.config.ts file [source](./.skilld/issues/issue-290.md:L30:L57)

- Use Lazy prefix (e.g., `<LazyHeavyComponent>`) or defineAsyncComponent for component suggestions — lazy-load detection identifies statically imported components but relies on your components using Nuxt's built-in lazy-loading patterns to fix issues [source](./.skilld/pkg/README.md:L87:L89)

- Focus on Web Vitals attribution data to pinpoint exact elements causing performance issues — LCP, INP, and CLS metrics come with detailed attribution so you can identify and optimize specific DOM elements rather than guessing [source](./.skilld/pkg/README.md:L29)

- Add crossorigin="anonymous" to external scripts in your audit recommendations — the module flags missing crossorigin attributes because they improve security and enable error reporting for third-party scripts [source](./.skilld/pkg/README.md:L107:L108)

- Ignore style-only hydration diffs as these are false positives — v1.1.3 filters style serialization differences to reduce noise [source](./.skilld/releases/v1.1.3.md:L11)

- Disable the hydration feature if your app uses ssr: false — the module will still try to detect mismatches and generate warnings even though hydration never runs [source](./.skilld/issues/issue-197.md)

- Include @nuxt/hints in the build transpile array if you encounter "#imports" resolution errors — some build configurations with custom Vite optimizeDeps or rollup settings require the module to be explicitly transpiled [source](./.skilld/issues/issue-151.md:L75:L83)

- Use the hover-to-highlight and click-to-inspect DevTools features during debugging — these interactive diagnostics let you navigate directly to problematic elements and source files without manual searching [source](./.skilld/pkg/README.md:L32:L35)
<!-- /skilld:best-practices -->

Related: nitropack-skilld, prettier-skilld
