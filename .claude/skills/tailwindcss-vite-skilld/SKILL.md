---
name: tailwindcss-vite-skilld
description: 'A utility-first CSS framework for rapidly building custom user interfaces. ALWAYS use when writing code importing "@tailwindcss/vite". Consult for debugging, best practices, or modifying @tailwindcss/vite, tailwindcss/vite, tailwindcss vite, tailwindcss.'
metadata:
  version: 4.3.3
  generated_by: cached
  generated_at: 2026-07-18
---

# tailwindlabs/tailwindcss `@tailwindcss/vite@4.3.3`

**Tags:** internal: 0.0.0-internal.b2586d4e, next: 4.0.0, insiders: 0.0.0-insiders.094bf62

**References:** [package.json](./.skilld/pkg/package.json) • [README](./.skilld/pkg/README.md) • [Docs](./.skilld/docs/_INDEX.md) • [Issues](./.skilld/issues/_INDEX.md) • [Discussions](./.skilld/discussions/_INDEX.md) • [Releases](./.skilld/releases/_INDEX.md)

## Search

Use `skilld search "query" -p @tailwindcss/vite` instead of grepping `.skilld/` directories. Run `skilld search --guide -p @tailwindcss/vite` for full syntax, filters, and operators.

<!-- skilld:api-changes -->

## API Changes

This section documents version-specific API changes for @tailwindcss/vite, focusing on recent major/minor releases and breaking changes.

## Breaking & Silent Changes

- BREAKING: Spacing utility output format changed in v4.3.1 — `m-0` and `left-0` now generate `0` instead of `calc(var(--spacing) * 0)`, and `m-1` and `left-1` now generate `var(--spacing)` instead of `calc(var(--spacing) * 1)`. This affects how spacing utilities interact with `calc()` expressions [source](./.skilld/releases/v4.3.1.md:L81:L84)

- DEPRECATED: `start-*` and `end-*` utilities removed in v4.2.0 — use `inset-s-*` and `inset-e-*` utilities instead for logical properties. The old utilities will be canonicalized automatically during upgrades [source](./.skilld/releases/v4.2.0.md:L42)

## New Utilities Added

- NEW: `@container-size` utility added in v4.3.0 for container query sizing [source](./.skilld/releases/v4.3.0.md:L11)

- NEW: `scrollbar-{auto,thin,none}` utilities for `scrollbar-width`, plus `scrollbar-thumb-*` and `scrollbar-track-*` color utilities for `scrollbar-color` — added in v4.3.0 [source](./.skilld/releases/v4.3.0.md:L12:L13)

- NEW: `scrollbar-gutter-*` utilities for `scrollbar-gutter` property added in v4.3.0 [source](./.skilld/releases/v4.3.0.md:L13)

- NEW: `zoom-*` utilities for CSS `zoom` property added in v4.3.0 [source](./.skilld/releases/v4.3.0.md:L14)

- NEW: `tab-*` utilities for CSS `tab-size` property added in v4.3.0 [source](./.skilld/releases/v4.3.0.md:L15)

- NEW: `font-features-*` utility for `font-feature-settings` added in v4.2.0 [source](./.skilld/releases/v4.2.0.md:L22)

- NEW: Inline size utilities `inline-*`, `min-inline-*`, `max-inline-*` for `inline-size`, `min-inline-size`, and `max-inline-size` added in v4.2.0 [source](./.skilld/releases/v4.2.0.md:L18)

- NEW: Block size utilities `block-*`, `min-block-*`, `max-block-*` for `block-size`, `min-block-size`, and `max-block-size` added in v4.2.0 [source](./.skilld/releases/v4.2.0.md:L19)

## New Features & Capabilities

- NEW: `@variant` directive now supports stacked variants (e.g. `@variant hover:focus { … }`) and compound variants (e.g. `@variant hover, focus { … }`) — added in v4.3.0 [source](./.skilld/releases/v4.3.0.md:L16:L17)

- NEW: Functional `@utility` definitions now support `--default(…)` in `--value(…)` and `--modifier(…)` — added in v4.3.0 for more flexible utility theming [source](./.skilld/releases/v4.3.0.md:L18)

- NEW: `@apply` directive now supports CSS mixins — fixed in v4.3.1 [source](./.skilld/releases/v4.3.1.md:L17)

- NEW: `PluginWithConfig` type now exported from `tailwindcss/plugin` — was missing and causing type inference errors in v4.3.0 [source](./.skilld/releases/v4.3.0.md:L32)

## CLI Changes

- NEW: `--silent` option added to `@tailwindcss/cli` in v4.3.1 to suppress build output [source](./.skilld/releases/v4.3.1.md:L11)

**Also changed:** Logical sizing utilities `pbs-*`, `pbe-*`, `mbs-*`, `mbe-*`, `scroll-pbs-*`, `scroll-pbe-*`, `scroll-mbs-*`, `scroll-mbs-*`, `border-bs-*`, `border-be-*` (v4.2.0) · `@variant` support inside `addBase()` (v4.3.1) · New color palettes: mauve, olive, mist, taupe (v4.2.0) · Module hook compatibility for Node 26+ (v4.3.1) · Support bare spacing values in `auto-rows-*` and `auto-cols-*` (v4.3.2)
<!-- /skilld:api-changes -->

<!-- skilld:best-practices -->

## Best Practices for @tailwindcss/vite

## Configuration & Build Optimization

- Control Lightning CSS optimization explicitly via the `optimize` plugin option to disable optimization in development or prevent minification when needed for debugging. Set `optimize: false` to disable entirely, or `optimize: { minify: false }` to optimize structure but skip minification [source](./.skilld/pkg-vite/README.md#enabling-or-disabling-lightning-css)

- Use explicit JavaScript entry points when importing packages via `@plugin` in Vite projects—configure module resolution to prefer `.js` exports over `.css` to avoid build errors when resolving plugin dependencies [source](./.skilld/releases/v4.3.0.md#fixed)

- Prevent unnecessary full-page reloads during development by ensuring scanned CSS files are loaded as modules before triggering HMR; files processed by Vite but not yet loaded as modules will not reload the page [source](./.skilld/releases/v4.3.3.md#fixed)

## CSS Features & Utilities

- Combine `@variant` with stacked (e.g. `@variant hover:focus { … }`) or compound (e.g. `@variant hover, focus { … }`) syntax to define complex pseudo-class combinations without manual selector repetition [source](./.skilld/releases/v4.3.0.md#added)

- Apply CSS mixins directly using `@apply`, not just Tailwind utilities—v4.3.1+ supports composition of custom CSS mixins alongside standard utilities for flexible component design [source](./.skilld/releases/v4.3.1.md#fixed)

## Custom Utilities & Theme Configuration

- Use `--value()` and `--modifier()` only in functional `@utility` definitions (with the `-*` suffix); static utilities without `-*` do not support these functions—use theme namespace lookups like `--value(--color-*)` or `--spacing(…)` instead [source](./.skilld/discussions/discussion-20218.md#accepted-answer)

- Create custom color utilities with opacity support by defining colors in custom theme namespaces and combining `--alpha()` with modifiers—map a color name like `current` to `currentColor` in the theme, then apply opacity via percentage or custom modifiers [source](./.skilld/discussions/discussion-20244.md#accepted-answer)

## File Scanning & Source Detection

- Order `@source` directives carefully—place rules targeting nested files before rules targeting parent folders to ensure all files are correctly included in the scan [source](./.skilld/releases/v4.3.3.md#fixed)

- Initialize a git repository in your project root (`git init`) so Tailwind respects `.gitignore` boundaries during automatic source detection; without a repo boundary, parent-level ignores may prevent file scanning [source](./.skilld/discussions/discussion-20135.md#accepted-answer)

## Class Names & Naming Conventions

- In v4, prefix syntax places variants before the prefix in class names—use `hover:prefix:utility` not `prefix:hover:utility` when applying prefix isolation to ensure variant modifiers are recognized and generated [source](./.skilld/discussions/discussion-20285.md#top-comments)

- Adjacent selectors without whitespace like `[data-foo]div` parse as two separate selectors, not one compound selector—this enables finer control over CSS specificity and selector matching in generated rules [source](./.skilld/releases/v4.3.3.md#fixed)

## Arbitrary Values & Canonicalization

- Canonical class suggestions are intentional for arbitrary values that don't map cleanly to Tailwind's theme scales or when exact pixel values match design specifications—use `w-[123px]` when a design requires that exact value rather than forcing it into the spacing scale [source](./.skilld/discussions/discussion-20142.md#accepted-answer)

## Watch Mode & CLI

- Use `@tailwindcss/cli --watch --poll[=ms]` when filesystem events are unreliable or unavailable (e.g. in Docker, network volumes, or Deno environments)—this mode works without requiring `@parcel/watcher` and automatically falls back when the dependency is unavailable [source](./.skilld/releases/v4.3.3.md#fixed)

<!-- /skilld:best-practices -->

Related: tailwindcss-skilld
