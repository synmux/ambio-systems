---
name: nuxt-hints-skilld
description: 'ALWAYS use when writing code importing "@nuxt/hints". Consult for debugging, best practices, or modifying @nuxt/hints, nuxt/hints, nuxt hints, hints.'
metadata:
  version: 1.1.2
  generated_by: Anthropic · Haiku 4.5
  generated_at: 2026-05-31
---

# nuxt/hints `@nuxt/hints@1.1.2`

**Tags:** latest: 1.1.2

**References:** [package.json](./.skilld/pkg/package.json) • [README](./.skilld/pkg/README.md) • [Issues](./.skilld/issues/_INDEX.md) • [Discussions](./.skilld/discussions/_INDEX.md) • [Releases](./.skilld/releases/_INDEX.md)

## Search

Use `skilld search "query" -p @nuxt/hints` instead of grepping `.skilld/` directories. Run `skilld search --guide -p @nuxt/hints` for full syntax, filters, and operators.

<!-- skilld:api-changes -->

## Version Clarification Needed

I've reviewed the @nuxt/hints release history, and I found a **version mismatch**:

- **Latest stable release**: v1.0.3 (2026-04-02)
- **Requested version**: v1.1.2 (does not exist)
- **Release timeline**: v1.0.0-alpha.1 → v1.0.0 → v1.0.3

**Before I proceed, please clarify which version you'd like me to document:**

1. **v1.0.3** (current stable) — generate API Changes for the latest available release
2. **v1.1.2** (future) — if you're planning ahead and have specifications for this version, provide them
3. **Different version** — if I've misunderstood, let me know which v1.x version to target

Once you confirm, I'll generate the API Changes section with:

- Breaking changes between versions
- New APIs introduced
- Deprecated or renamed APIs
- Proper source citations from release notes

Which would you prefer?

<!-- /skilld:api-changes -->

<!-- skilld:best-practices -->

## Best Practices

## Configuration & Setup

- Use feature object syntax with nested `logs` and `devtools` flags to independently control console output and DevTools UI visibility for each feature, rather than relying solely on the top-level `devtools` boolean — this prevents console spam when fixing issues step by step without losing DevTools visibility [source](./.skilld/pkg/README.md:L120-150)

- Disable features selectively when facing false positives or overwhelming logs rather than disabling the entire module — the feature toggle design specifically supports fixing issues incrementally (e.g. disabling hydration while fixing web vitals) [source](./.skilld/issues/issue-196.md)

- Enable HTML validation via the `htmlValidate` feature to catch HTML5 compliance issues at build time, leveraging the built-in `html-validate` integration rather than configuring it separately [source](./.skilld/pkg/README.md:L92-95)

## Component Optimization

- Prefix statically imported components with `Lazy` (e.g. `<LazyHeavyComponent>`) to defer component loading until they appear in the viewport — this is detected and recommended by the unused component detection feature [source](./.skilld/pkg/README.md:L65-89)

- Prefer the `Lazy` prefix over `defineAsyncComponent` for component-level code splitting as it has better integration with the hints module's lazy-loading detector [source](./.skilld/pkg/README.md:L85-89)

- Use the DevTools lazy-load panel to identify statically imported components that were never rendered on a given route and convert them to lazy-loaded components, which directly reduces initial bundle size [source](./.skilld/pkg/README.md:L65-69)

## Web Vitals & Performance

- Monitor all three Core Web Vitals (LCP, INP, CLS) with the module's real-time attribution data — the detailed element-specific information pinpoints which DOM nodes cause metrics degradation rather than just reporting aggregate numbers [source](./.skilld/pkg/README.md:L47-51)

- Check the Web Vitals DevTools panel for element-specific optimization advice tied to each metric rather than relying on generic performance guidance [source](./.skilld/releases/v1.0.0.md:L32-45)

- Prioritize the LCP element when optimizing web vitals — the module flags images with `loading="lazy"` that shouldn't have it, preventing a common performance regression [source](./.skilld/pkg/README.md:L99-104)

## Hydration Debugging

- Use the Hydration Inspector's side-by-side diff viewer to compare server-rendered vs client-hydrated HTML rather than manually diffing SSR and client output — the visual diff catches whitespace-sensitive mismatches that are easy to miss [source](./.skilld/pkg/README.md:L53-57)

- Disable hydration feature detection if using `ssr: false` globally on your routes to prevent false-positive mismatch warnings that occur when hydration is intentionally skipped [source](./.skilld/issues/issue-197.md)

## Third-Party Scripts

- Review third-party scripts in the DevTools Scripts panel for render-blocking status and missing security attributes (e.g. missing `crossorigin="anonymous"`) rather than relying on manual script audits [source](./.skilld/pkg/README.md:L59-63)

- Ensure external scripts have the `crossorigin="anonymous"` attribute when they are accessed cross-origin — the module detects this absence and flags it as a security and error-reporting gap [source](./.skilld/pkg/README.md:L99-108)
<!-- /skilld:best-practices -->
