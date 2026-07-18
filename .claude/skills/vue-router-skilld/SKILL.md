---
name: vue-router-skilld
description: 'ALWAYS use when writing code importing "vue-router". Consult for debugging, best practices, or modifying vue-router, vue router, router.'
metadata:
  version: 5.2.0
  generated_by: cached
  generated_at: 2026-07-18
---

# vuejs/router `vue-router@5.2.0`

**Tags:** next: 4.0.13, legacy: 3.6.5, edge: 4.4.0-alpha.3

**References:** [package.json](./.skilld/pkg/package.json) • [README](./.skilld/pkg/README.md) • [Docs](./.skilld/docs/_INDEX.md) • [Issues](./.skilld/issues/_INDEX.md) • [Discussions](./.skilld/discussions/_INDEX.md) • [Releases](./.skilld/releases/_INDEX.md)

## Search

Use `skilld search "query" -p vue-router` instead of grepping `.skilld/` directories. Run `skilld search --guide -p vue-router` for full syntax, filters, and operators.

<!-- skilld:api-changes -->

## API Changes

This section documents version-specific API changes for vue-router — prioritize recent major/minor releases.

### Breaking Changes (Score 5: Silent Breakage)

- BREAKING: Empty optional params silently omitted from resolved params since v5.0.7 — routes with optional parameters now exclude empty values from `route.params`, potentially breaking code checking for param existence [source](./.skilld/releases/v5.0.7.md:L24)

- BREAKING: Query params optional by default (experimental) since v5.0.0 — query parameters are now optional in type definitions by default, changing validation strictness [source](./.skilld/releases/v5.0.0.md:L14)

- BREAKING: `miss()` throws internally and returns `never` (experimental) since v5.0.3 — function behaviour changed fundamentally for data loaders error handling [source](./.skilld/releases/v5.0.3.md:L12)

### New APIs (Score 4)

- NEW: Raw param parsers support in v5.1.0 — allows defining param parsers with `ParamParser<T>` interface for custom route parameter parsing and validation [source](./.skilld/releases/v5.1.0.md:L13)

- NEW: Allow overriding global Router type in v5.1.0 — use `TypesConfig` to customise the Router type returned by `useRouter()` for type narrowing [source](./.skilld/releases/v5.1.0.md:L15)

- NEW: `reroute()` function (experimental) in v5.0.3 — replaces deprecated `new NavigationResult()` for triggering route navigation within data loaders [source](./.skilld/releases/v5.0.3.md:L13)

- NEW: Data loaders (experimental) in v5.0.0 — async data loading feature added as experimental API for route-level data fetching [source](./.skilld/releases/v5.0.0.md:L16)

### Deprecated / Renamed APIs (Score 3)

- DEPRECATED: `NavigationResult()` constructor in v5.0.3 — use `reroute()` instead for navigation within data loaders [source](./.skilld/releases/v5.0.3.md:L26)

- DEPRECATED: `selectNavigationResult()` removed (experimental) in v5.0.3 — data loader helper removed, use alternative patterns [source](./.skilld/releases/v5.0.3.md:L14)

- DEPRECATED: `next()` callback in navigation guards in v5.0.3 — guards now use return values instead of callback invocation [source](./.skilld/releases/v5.0.3.md:L23)

### Enhanced/New Features (Score 3–4)

- NEW: String param parsers for convenience in v5.1.0 — pass string names to `defineParamParser()` for built-in parsers instead of inline functions [source](./.skilld/releases/v5.1.0.md:L18)

- ENHANCED: `defineParamParser()` more intuitive in v5.0.7 — improved API signature for defining custom URL parameter serialisation [source](./.skilld/releases/v5.0.7.md:L12)

- NEW: Param parser include/exclude options in v5.0.7 — add `include` and `exclude` options to `defineParamParser()` for granular parser scope control [source](./.skilld/releases/v5.0.7.md:L15)

- ENHANCED: Typed `definePage` params.path in v5.1.0 — params.path property now has strict typing to match route definitions [source](./.skilld/releases/v5.1.0.md:L11)

- ENHANCED: Strict type for `definePage` param default in v5.1.0 — param default values are now type-checked against route parameter types [source](./.skilld/releases/v5.1.0.md:L12)

- NEW: Runtime warning for invalid query param formats in v5.1.0 — warns at runtime when query parameters don't match declared formats [source](./.skilld/releases/v5.1.0.md:L16)

- NEW: Override `useRouter()` return type with experimental types config in v5.1.0 — (experimental) use `TypesConfig` to replace Router type at IDE level [source](./.skilld/releases/v5.1.0.md:L17)

**Also changed:** Support `_parent` in nested folders · Volar plugins · Route JSON schema · Runtime error on missing param parsers · Force array type raw param parsers · Deterministic param parser type order · Helpful diagnostics (v5.2.0) · Ignore stale async scrollBehavior results (v5.2.0) · Allow Pinia 4 (v5.2.0)
<!-- /skilld:api-changes -->

<!-- skilld:best-practices -->

## Vue Router 5.2.0 Best Practices

## Best Practices

- Always use dynamic imports for lazy-loaded route components — enables code splitting and only fetches the component when the route is visited, significantly reducing initial bundle size [source](./.skilld/docs/guide/advanced/lazy-loading.md#L1:L35)

- Watch specific route parameter changes with computed watchers instead of watching the entire `route` object — prevents unnecessary watchers firing and improves reactivity precision [source](./.skilld/docs/guide/advanced/composition-api.md#L35:L52)

- Use `router.beforeResolve` instead of `beforeEach` for data fetching and permission checks — executes after all async components are resolved, ensuring data is ready before rendering [source](./.skilld/docs/guide/advanced/navigation-guards.md#L89:L112)

- Avoid the third `next()` argument in navigation guards — favour returning values (`false` to cancel, route location to redirect) instead, which is clearer and reduces nesting errors [source](./.skilld/docs/guide/advanced/navigation-guards.md#L66:L87)

- Register the `DataLoaderPlugin` before adding the router to the app — ensures data loaders are properly initialized and can intercept navigation before rendering [source](./.skilld/docs/data-loaders/index.md#L18:L39)

- Export all data loaders from page components, even if defined separately — allows the router to discover and await loaders during navigation, enabling proper data fetching orchestration [source](./.skilld/docs/data-loaders/organization.md#L48)

- Inject global dependencies into loader functions before any `await` statements — after awaiting, the injection context is lost and subsequent inject calls will fail [source](./.skilld/docs/data-loaders/defining-loaders.md#L59:L84)

- Extract shared data loaders to separate files and re-export from page components — reduces bundle size by preventing page component chunks from being loaded just to access a loader [source](./.skilld/docs/data-loaders/organization.md#L1:L46)

- Use `RouterView` v-slot to wrap route components with `KeepAlive` and `Transition` — enables component caching and animated transitions between routes without repeating the slot logic [source](./.skilld/docs/guide/advanced/router-view-slot.md#L15:L47)

- Calculate dynamic scroll offset margins using `getComputedStyle()` instead of hardcoded values — adapts to elements with dynamic heights like sticky headers without breaking responsive layouts [source](./.skilld/docs/guide/advanced/scroll-behavior.md#L119:L143)

- Await `router.push()` and check the resolved value to detect navigation failures — differentiates between successful navigation, prevention, cancellation, and redirection [source](./.skilld/docs/guide/advanced/navigation-failures.md#L38:L47)

- Use `isNavigationFailure()` with `NavigationFailureType` to classify why navigation failed — allows handling aborted, cancelled, and duplicated navigation attempts differently [source](./.skilld/docs/guide/advanced/navigation-failures.md#L49:L61)

- Spread `RouterLink.props` when creating custom link components and use `useLink` for advanced implementations — ensures all RouterLink features and props are available in your custom component [source](./.skilld/docs/guide/advanced/extending-router-link.md#L14:L127)

- Call `router.replace()` after `router.addRoute()` to navigate to the newly added route immediately — the router adds the route but doesn't navigate; manual navigation is required to display the new route [source](./.skilld/docs/guide/advanced/dynamic-routing.md#L12:L37)

<!-- /skilld:best-practices -->
