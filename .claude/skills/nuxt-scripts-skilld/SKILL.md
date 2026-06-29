---
name: nuxt-scripts-skilld
description: 'ALWAYS use when writing code importing "@nuxt/scripts". Consult for debugging, best practices, or modifying @nuxt/scripts, nuxt/scripts, nuxt scripts, scripts.'
metadata:
  version: 1.2.1
  generated_by: Anthropic · Haiku 4.5
  generated_at: 2026-06-29
---

# nuxt/scripts `@nuxt/scripts@1.2.1`

**Tags:** beta: 1.0.0-beta.32, rc: 1.0.0-rc.11, latest: 1.2.1

**References:** [package.json](./.skilld/pkg/package.json) • [Docs](./.skilld/docs/_INDEX.md) • [Issues](./.skilld/issues/_INDEX.md) • [Discussions](./.skilld/discussions/_INDEX.md) • [Releases](./.skilld/releases/_INDEX.md)

## Search

Use `skilld search "query" -p @nuxt/scripts` instead of grepping `.skilld/` directories. Run `skilld search --guide -p @nuxt/scripts` for full syntax, filters, and operators.

<!-- skilld:api-changes -->

## API Changes

This section documents version-specific API changes for @nuxt/scripts v1.2.1 — prioritise recent major/minor releases and breaking changes that LLMs trained on older data will use incorrectly.

### Breaking Changes (v1.0.0 — Major Release)

- BREAKING: Config structure completely reorganised — `scripts.registry` replaces ad-hoc config, `scripts.globals` centralises configuration [source](./.skilld/releases/v1.0.0.md:L213:231)

- BREAKING: First-party proxy mode config changed — `firstParty: { enable: true }` replaces older `firstParty` boolean flag structure [source](./.skilld/releases/v1.0.0.md:L16:26)

- BREAKING: Google Maps `expose` renamed to `mapsApi` — use `const { mapsApi } = await script.load()` instead of `googleMaps` [source](./.skilld/releases/v1.0.0.md:L226:227)

- BREAKING: Google Maps top-level `center` and `zoom` props deprecated — use `initialCenter` and `initialZoom` or declarative `ScriptGoogleMapsMarker` components [source](./.skilld/releases/v1.0.0.md:L225:226)

- BREAKING: PayPal SDK upgraded to v6 — breaking API changes in PayPal instance methods and configuration [source](./.skilld/releases/v1.0.0.md:L229:230)

- BREAKING: `ScriptGoogleMapsStaticMap` now standalone component — no longer a prop on `ScriptGoogleMaps`, use `<ScriptGoogleMapsStaticMap />` directly [source](./.skilld/releases/v1.0.0.md:L192:194)

- BREAKING: `ScriptGoogleMapsPinElement` removed — use `<ScriptGoogleMapsMarker>` with `#content` slot for custom marker visuals [source](./.skilld/releases/v1.0.0.md:L200:201)

- BREAKING: `ScriptGoogleMapsAdvancedMarkerElement` consolidated into `ScriptGoogleMapsMarker` — remove `Advanced` from component name [source](./.skilld/releases/v1.0.0.md:L200:201)

### New APIs (v1.0.0 — v1.2.1)

- NEW: `useScript().reload()` method — re-executes DOM-scanning scripts after SPA navigation for dynamic content updates [source](./.skilld/releases/v1.0.0.md:L118:125)

- NEW: `ScriptXEmbed` and `ScriptInstagramEmbed` components — server-side SSR embeds with slot-based customisation, replaces third-party embed scripts [source](./.skilld/releases/v1.0.0.md:L62:79)

- NEW: `ScriptBlueskyEmbed` component — Bluesky post embeds with SSR support [source](./.skilld/releases/v1.0.0.md:L75:79)

- NEW: `@nuxt/scripts/stats` subpath export with `getScriptStats()` — audit script privacy ratings, performance, CWV estimates, and cookie analysis [source](./.skilld/releases/v1.0.0.md:L143:151)

- NEW: Vendor-native `consent` object on script instances — `useScriptGoogleTagManager().consent.update()`, `useScriptMetaPixel().consent.grant()`, replaces manual consent tracking [source](./.skilld/releases/v1.0.0.md:L82:101)

- NEW: `defaultConsent` option for consent-aware registry scripts — configure initial consent state before first tracking call [source](./.skilld/releases/v1.0.0.md:L86:101)

- NEW: `ScriptGoogleMapsGeoJson` component — declarative GeoJSON layer with full event bindings, wraps `google.maps.Data` [source](./.skilld/releases/v1.0.0.md:L259:260)

- NEW: `ScriptGoogleMapsOverlayView` component with `#content` slot — render Vue components at map coordinates with auto-inheritance of marker position [source](./.skilld/releases/v1.0.0.md:L179:187)

- NEW: Partytown web worker support per-script — set `partytown: true` on registry entries to offload analytics/tracking to a worker thread [source](./.skilld/releases/v1.0.0.md:L34:54)

- NEW: `NUXT_PUBLIC_SCRIPTS_*` environment variables for registry script config — auto-populate `runtimeConfig.public.scripts` from env without boilerplate [source](./.skilld/releases/v1.0.0.md:L203:211)

- NEW: Automatic SRI (Subresource Integrity) hash generation for bundled scripts — set `assets: { integrity: 'sha384' }` in config [source](./.skilld/releases/v1.0.0.md:L127:139)

- NEW: `/types-source` subpath export — machine-readable type definitions for documentation generators [source](./.skilld/releases/v1.0.0.md:L239)

- NEW: `ScriptVimeoPlayer` `ratio` prop — aspect ratio control matching YouTube Player API [source](./.skilld/releases/v1.0.0.md:L159:161)

- NEW: YouTube Player overhaul with isolated instances — multiple players no longer interfere; new `ratio` prop and cleanup on unmount [source](./.skilld/releases/v1.0.0.md:L153:158)

### New Registry Scripts (v1.0.0 — v1.1.0)

- NEW: PostHog Analytics (`useScriptPostHog()`) — product analytics with feature flags [source](./.skilld/releases/v1.0.0.md:L105)

- NEW: Google reCAPTCHA v3 (`useScriptGoogleRecaptcha()`) — invisible bot protection [source](./.skilld/releases/v1.0.0.md:L106)

- NEW: TikTok Pixel (`useScriptTikTokPixel()`) — conversion tracking with consent API [source](./.skilld/releases/v1.0.0.md:L107)

- NEW: Google Sign-In (`useScriptGoogleSignIn()`) — one-tap authentication with helpers [source](./.skilld/releases/v1.0.0.md:L108)

- NEW: Rybbit Analytics (`useScriptRybbit()`) — privacy-focused open source analytics [source](./.skilld/releases/v1.0.0.md:L109)

- NEW: Databuddy Analytics (`useScriptDatabuddy()`) — lightweight analytics [source](./.skilld/releases/v1.0.0.md:L110)

- NEW: Bing UET (`useScriptBingUet()`) — Microsoft Advertising conversion tracking [source](./.skilld/releases/v1.0.0.md:L111)

- NEW: Mixpanel Analytics (`useScriptMixpanel()`) — product analytics and user tracking [source](./.skilld/releases/v1.0.0.md:L112)

- NEW: Vercel Analytics (`useScriptVercelAnalytics()`) — Vercel Web Analytics integration [source](./.skilld/releases/v1.0.0.md:L113)

- NEW: Gravatar (`useScriptGravatar()`) — avatar service with privacy-preserving proxy [source](./.skilld/releases/v1.0.0.md:L114)

- NEW: LinkedIn Insight Tag (`useScriptLinkedInInsight()`) — v1.1.0 [source](./.skilld/releases/v1.1.0.md:L11)

- NEW: Ahrefs Web Analytics (`useScriptAhrefs()`) — v1.1.0 [source](./.skilld/releases/v1.1.0.md:L12)

- NEW: Usercentrics CMP (`useScriptUsercentrics()`) — v1.1.0 [source](./.skilld/releases/v1.1.0.md:L13)

- NEW: Calendly (`useScriptCalendly()`) — v1.1.0 [source](./.skilld/releases/v1.1.0.md:L14)

- NEW: SpeedCurve LUX (`useScriptSpeedCurve()`) — analytics with LUX snippet vendoring — v1.2.0 [source](./.skilld/releases/v1.2.0.md:L11)

### New Features (v1.1.0 — v1.2.0)

- NEW: Build-time debug flag with script-lifecycle tracing — enable via config to see script execution flow at build time [source](./.skilld/releases/v1.1.0.md:L15)

- NEW: Environment-variable overrides for `scripts.globals` — set `NUXT_PUBLIC_SCRIPTS_<SCRIPT_KEY>_*` for single-build, multi-deploy deployments [source](./.skilld/releases/v1.1.0.md:L17)

- NEW: `Consent.default()` with strict GCMv2 validation for `useScriptGoogleTagManager()` and `useScriptGoogleAnalytics()` — v1.1.0 [source](./.skilld/releases/v1.1.0.md:L18)

- NEW: TikTok Pixel production hardening — region selection, CAPI deduplication, advanced matching — v1.1.0 [source](./.skilld/releases/v1.1.0.md:L19)

- NEW: Runtime disable flag and `scripts:globals` hook in v1.2.0 — disable scripts at runtime or customise global config [source](./.skilld/releases/v1.2.0.md:L12)

### Deprecated APIs (v1.0.0 — v1.2.0)

- DEPRECATED: Google Maps heatmap component — removed in v1.2.0, no replacement provided [source](./.skilld/releases/v1.2.0.md:L17)

### Also Changed

Google Maps OverlayView class extraction and reactive rendering · YouTube Player aspect ratio support · Multiple a11y fixes across Instagram embed, Vimeo player, YouTube player · Stripe.js SDK version selection · Proxy mode RFC 7230 hop-by-hop header stripping

<!-- /skilld:api-changes -->

<!-- skilld:best-practices -->

## Best Practices

- Wrap `useScript()` calls in custom composables to ensure singleton behaviour — each script loads only once globally, and all components share the same instance [source](./.skilld/docs/content/docs/1.guides/0.key-concepts.md#script-singleton)

- Use `onNuxtReady` trigger by default (the default behaviour) — it minimises impact on Core Web Vitals by loading scripts after hydration is complete and the main thread is idle [source](./.skilld/docs/content/docs/1.guides/1.script-triggers.md#default-onnutxready)

- Use `useScriptTriggerInteraction()` for user-initiated scripts like chat widgets and conditionally-loaded features — prefer explicit events like `click` over `hover` to avoid UX issues with event loss [source](./.skilld/docs/content/docs/1.guides/1.script-triggers.md#user-interaction)

- Use `useScriptTriggerIdleTimeout()` for non-critical analytics with a 3–5 second delay — balances analytics completeness against main thread blocking during the critical render window [source](./.skilld/docs/content/docs/1.guides/1.script-triggers.md#idle-timeout)

- Call `onLoaded()` instead of relying on `proxy` when you need the script's actual return value or synchronous access to its API — `proxy` queues calls before the script loads but doesn't return values [source](./.skilld/docs/content/docs/1.guides/0.key-concepts.md#understanding-proxied-functions)

- Use explicit `script.warmup('preload')` before manual load when you anticipate the user will need a script — this hints to the browser to download while the app is rendering [source](./.skilld/docs/content/docs/1.guides/1.warmup.md#warmup)

- Prefer global scripts in `nuxt.config` over scattered `useScript()` calls when you don't need type-safe API interaction or want to load a script everywhere without composable boilerplate [source](./.skilld/docs/content/docs/1.guides/4.global.md#usage)

- Use `trigger: false` on registry entries you load via composables rather than globally — this registers proxy routes and types without injecting a `<script>` tag at build time [source](./.skilld/docs/content/docs/4.migration-guide/1.v0-to-v1.md#scripts-no-longer-auto-load-without-a-trigger)

- Gate scripts behind consent with `useScriptTriggerConsent()` to avoid loading them until the user grants permission — the trigger blocks the script until `accept()` is called [source](./.skilld/docs/content/docs/1.guides/3.consent.md#binary-load-gate)

- Wire vendor-native consent APIs explicitly for multiple scripts with a single banner — each vendor (Google, Meta, TikTok, Matomo) exposes its own dialect, so write one handler per script rather than trying to abstract [source](./.skilld/docs/content/docs/1.guides/3.consent.md#fanning-out-to-multiple-scripts)

- Use `defaultConsent` to set the initial policy _before_ the vendor's first tracking call — this prevents opt-out violations when the script initializes before the user interacts with your banner [source](./.skilld/docs/content/docs/1.guides/3.consent.md#per-script-consent-api)

- Provide error fallback and loading slots on Facade Components — minimal default styling is intentional; add your own feedback UI and handle script load failures gracefully [source](./.skilld/docs/content/docs/1.guides/5.facade-components.md#best-practices-in-using-facade-components)

- Use `useScriptEventPage()` to track accurate page titles on SPA navigation — Nuxt's head is async, so route change titles are often stale if you poll directly [source](./.skilld/docs/content/docs/1.guides/3.page-events.md)

- Check each vendor's SPA support before calling `reload()` — many scripts have their own refresh methods (e.g., `_iub.cs.api.activateSnippets()` for iubenda) which are more efficient than full reload [source](./.skilld/docs/content/docs/3.api/1.use-script.md#reload)

<!-- /skilld:best-practices -->
