---
name: nuxt-scripts-skilld
description: 'Load third-party scripts with better performance, privacy and DX in Nuxt Apps. ALWAYS use when writing code importing "@nuxt/scripts". Consult for debugging, best practices, or modifying @nuxt/scripts, nuxt/scripts, nuxt scripts, scripts.'
metadata:
  version: 1.3.1
  generated_by: cached
  generated_at: 2026-07-18
---

# nuxt/scripts `@nuxt/scripts@1.3.1`

**Tags:** beta: 1.0.0-beta.32, rc: 1.0.0-rc.11, latest: 1.3.1

**References:** [package.json](./.skilld/pkg/package.json) • [Docs](./.skilld/docs/_INDEX.md) • [Issues](./.skilld/issues/_INDEX.md) • [Discussions](./.skilld/discussions/_INDEX.md) • [Releases](./.skilld/releases/_INDEX.md)

## Search

Use `skilld search "query" -p @nuxt/scripts` instead of grepping `.skilld/` directories. Run `skilld search --guide -p @nuxt/scripts` for full syntax, filters, and operators.

<!-- skilld:api-changes -->

## API Changes

This section documents version-specific API changes — prioritise recent major/minor releases.

### v1.3.0 and later

- NEW: Proxy path aliases feature to hide third-party hostnames in first-party mode [source](./.skilld/releases/v1.3.0.md#features)

- BREAKING: PayPal JavaScript SDK upgraded from v5 to v6 in v1.0 — changed configuration structure and method signatures [source](./.skilld/releases/v1.0.0.md:L229:231)

- BREAKING: Google Maps `mapsApi` expose replaces deprecated `googleMaps` — used to access the Google Maps API instance [source](./.skilld/releases/v1.0.0.md:L227:228)

- NEW: Script `.reload()` method to re-execute DOM-scanning scripts after SPA navigation — allows dynamic re-runs without full page reload [source](./.skilld/releases/v1.0.0.md:L234)

- NEW: `@nuxt/scripts/stats` subpath export for auditing script privacy, performance, and security characteristics [source](./.skilld/releases/v1.0.0.md:L238)

- NEW: Vendor-native `consent` object on registry script instances with `update()`, `grant()`, `revoke()`, and `hold()` methods — works with `defaultConsent` option [source](./.skilld/releases/v1.0.0.md:L252)

- NEW: Partytown web worker support via `partytown: true` per-script option with auto-configured forward arrays [source](./.skilld/releases/v1.0.0.md:L236)

- NEW: SSR social media embeds (`ScriptXEmbed`, `ScriptInstagramEmbed`, `ScriptBlueskyEmbed`) with scoped slots for custom rendering — server-side data fetching with domain proxy [source](./.skilld/releases/v1.0.0.md:L235)

- BREAKING: Google Maps component consolidation — `ScriptGoogleMapsAdvancedMarkerElement` merged into `ScriptGoogleMapsMarker`, custom marker content now via `#content` slot, removed `ScriptGoogleMapsPinElement` [source](./.skilld/releases/v1.0.0.md:L223:224)

- NEW: `ScriptGoogleMapsStaticMap` extracted as standalone component, serves images through server, reduces API billing [source](./.skilld/releases/v1.0.0.md:L224)

- NEW: `ScriptGoogleMapsOverlayView` component with `v-model:open`, `anchor`, and `offset` props for declarative position-based overlays [source](./.skilld/releases/v1.0.0.md:L265)

- NEW: `ScriptGoogleMapsGeoJson` component for declarative GeoJSON loading and styling [source](./.skilld/releases/v1.0.0.md:L249:250)

- BREAKING: Google Maps `:center` and `:zoom` top-level props deprecated — use composition within `ScriptGoogleMaps` instead [source](./.skilld/releases/v1.0.0.md:L226:228)

- NEW: YouTube Player isolated instances with `ratio` prop and proper cleanup on unmount [source](./.skilld/releases/v1.0.0.md:L253:254)

- NEW: Vimeo Player `ratio` prop for aspect ratio control [source](./.skilld/releases/v1.0.0.md:L254)

- NEW: `NUXT_PUBLIC_SCRIPTS_*` environment variables auto-populate `runtimeConfig.public.scripts` without boilerplate config [source](./.skilld/releases/v1.0.0.md:L242)

- DEPRECATED: Google Maps heatmap component in v1.2.0 — no direct replacement yet [source](./.skilld/releases/v1.2.0.md:L17)

- NEW: `scripts:globals` hook and runtime disable option for global script flags in v1.2.0 [source](./.skilld/releases/v1.2.0.md:L12)

- NEW: `Consent.default()` strict GCMv2 validation for `gtm` and `ga` scripts in v1.1.0 [source](./.skilld/releases/v1.1.0.md:L18)

- NEW: Build-time debug flag with script-lifecycle tracing for troubleshooting script loading in v1.1.0 [source](./.skilld/releases/v1.1.0.md:L15)

**Also changed:** First-party mode config structure · `ScriptGoogleMapsMarker` position prop and content slot · SpeedCurve LUX (new v1.2) · Unhead v3 peer dependency support (v1.2) · Env-var overrides for scripts.globals (v1.1) · TikTok Pixel production hardening (v1.1) · Multiple new registry scripts in v1.0 and v1.1 · Google Maps interactive map DX overhaul with 11 declarative components
<!-- /skilld:api-changes -->

<!-- skilld:best-practices -->

## Best Practices

- Wrap `useScript()` calls in composables to enable easier instantiation and reuse across your application — a script with the same `src` will only load once and subsequent calls return the same instance [source](./.skilld/docs/content/docs/1.guides/0.key-concepts.md#script-singleton)

- Use the `onLoaded()` hook to access the script's API directly instead of proxied functions when you need return values or direct control — proxied functions queue calls before the script loads but cannot return values until awaited, blocking rendering [source](./.skilld/docs/content/docs/1.guides/0.key-concepts.md#understanding-proxied-functions)

- Check the third-party script's native SPA support before using `reload()` — most modern analytics scripts provide their own methods (e.g., `_iub.cs.api.activateSnippets()` for iubenda) which are more efficient than reloading the entire script [source](./.skilld/docs/content/docs/3.api/1.use-script.md:L115-L128)

- Prefer specialized triggers (`useScriptTriggerIdleTimeout()`, `useScriptTriggerInteraction()`, `useScriptTriggerElement()`) over the default `onNuxtReady` when a script is only needed in specific user flows — reduces initial bundle impact and improves Core Web Vitals [source](./.skilld/docs/content/docs/1.guides/1.script-triggers.md:L67-L138)

- Use `warmupStrategy: 'preload'` for scripts you load immediately and `'preconnect'` or `'dns-prefetch'` for scripts you expect to load within 10 seconds — optimises the network connection before the script actually loads [source](./.skilld/docs/content/docs/1.guides/1.warmup.md#warmupstrategy)

- Call `script.warmup()` explicitly when you know the user may soon need a manually-loaded script (e.g., when the video container becomes visible) — enables preloading without triggering a load [source](./.skilld/docs/content/docs/1.guides/1.warmup.md#warmup)

- Store script configuration in `runtimeConfig` or `.env` files rather than hardcoding IDs and tokens in your codebase — registry scripts automatically validate options during development, catching misconfigurations early [source](./.skilld/docs/content/docs/1.guides/1.registry-scripts.md#runtime-config-integration)

- Provide a `mock` value in development config to load a mocked version of registry scripts instead of the real third-party service — prevents side effects during local development while still testing the API surface [source](./.skilld/docs/content/docs/1.guides/1.registry-scripts.md#disabling-in-development)

- Use a unique `key` when loading the same registry script multiple times with different configuration — without a key, subsequent calls return the first instance instead of loading a new one [source](./.skilld/docs/content/docs/1.guides/1.registry-scripts.md#loading-multiple-of-the-same-script)

- Override `scriptInput.src` when loading self-hosted versions of registry scripts — Nuxt Scripts merges query parameters from the original URL onto your custom source while preserving registry features like first-party mode and consent handling [source](./.skilld/discussions/discussion-387.md#top-comments)

- Set `bundle: false` when using Google Tag Manager's Tag Assistant Preview Mode — bundling prevents the Tag Assistant debugger from functioning correctly [source](./.skilld/discussions/discussion-745.md#accepted-answer)

- Use `useScriptTriggerConsent()` to gate script loading on user consent — returns a reactive trigger and methods to manage the consent state, working alongside per-script `consent` objects for vendor-native consent APIs [source](./.skilld/docs/content/docs/1.guides/3.consent.md#binary-load-gate)

- Guard access to global scripts that may be disabled per deployment with optional chaining (e.g., `$scripts.awin?.`) — runtime overrides via env vars can disable specific scripts, making them undefined [source](./.skilld/docs/content/docs/1.guides/4.global.md#disabling-a-global-per-deployment)

- Provide error fallback and accessible loading states for Facade Components using slots — trigger script loading on click (not hover) to avoid losing subsequent user interaction events [source](./.skilld/docs/content/docs/1.guides/5.facade-components.md#best-practices-in-using-facade-components)

<!-- /skilld:best-practices -->
