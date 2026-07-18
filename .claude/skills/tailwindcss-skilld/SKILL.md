---
name: tailwindcss-skilld
description: 'A utility-first CSS framework for rapidly building custom user interfaces. ALWAYS use when writing code importing "tailwindcss". Consult for debugging, best practices, or modifying tailwindcss.'
metadata:
  version: 4.3.3
  generated_by: cached
  generated_at: 2026-07-18
---

# tailwindlabs/tailwindcss `tailwindcss@4.3.3`

**Tags:** next: 4.0.0, v3-lts: 3.4.19, insiders: 0.0.0-insiders.094bf62

**References:** [package.json](./.skilld/pkg/package.json) • [README](./.skilld/pkg/README.md) • [Issues](./.skilld/issues/_INDEX.md) • [Discussions](./.skilld/discussions/_INDEX.md) • [Releases](./.skilld/releases/_INDEX.md)

## Search

Use `skilld search "query" -p tailwindcss` instead of grepping `.skilld/` directories. Run `skilld search --guide -p tailwindcss` for full syntax, filters, and operators.

<!-- skilld:api-changes -->

## API Changes

This section documents version-specific API changes — prioritize recent major/minor releases.

- BREAKING: `start-*` and `end-*` utilities — deprecated in v4.2.0 in favour of logical utilities `inset-s-*` and `inset-e-*`; existing code continues to work but canonicalization now migrates these to the new names [source](./.skilld/releases/v4.2.0.md#deprecated)

- NEW: `@container-size` utility — added in v4.3.0, creates container query size utilities for responsive component queries [source](./.skilld/releases/v4.3.0.md#added)

- NEW: `scrollbar-{auto,thin,none}` utilities — added in v4.3.0, controls `scrollbar-width` CSS property for scrollbar visibility and sizing (#20019) [source](./.skilld/releases/v4.3.0.md#added)

- NEW: `scrollbar-thumb-*` and `scrollbar-track-*` color utilities — added in v4.3.0, style scrollbar thumb and track colours via `scrollbar-color` CSS property (#20019) [source](./.skilld/releases/v4.3.0.md#added)

- NEW: `scrollbar-gutter-*` utilities — added in v4.3.0, controls `scrollbar-gutter` property to reserve space for scrollbars (#20018) [source](./.skilld/releases/v4.3.0.md#added)

- NEW: `zoom-*` utilities — added in v4.3.0, provides CSS `zoom` property values for element scaling (#20020) [source](./.skilld/releases/v4.3.0.md#added)

- NEW: `tab-*` utilities — added in v4.3.0, supplies `tab-size` property values for controlling whitespace/tab rendering (#20022) [source](./.skilld/releases/v4.3.0.md#added)

- NEW: `@variant` with stacked variants — added in v4.3.0, allows defining custom variants using stacked syntax like `@variant hover:focus { … }` (#19996) [source](./.skilld/releases/v4.3.0.md#added)

- NEW: `@variant` with compound variants — added in v4.3.0, allows defining custom variants using compound syntax like `@variant hover, focus { … }` (#19996) [source](./.skilld/releases/v4.3.0.md#added)

- NEW: `@tailwindcss/webpack` package — added in v4.2.0, integrates Tailwind CSS as a webpack plugin for bundler-native processing (#19610) [source](./.skilld/releases/v4.2.0.md#added)

- NEW: Logical spacing utilities — added in v4.2.0, provides block-flow and inline-flow directions: `pbs-*`, `pbe-*`, `mbs-*`, `mbe-*`, `scroll-pbs-*`, `scroll-pbe-*`, `scroll-mbs-*`, `scroll-mbe-*`, `border-bs-*`, `border-be-*` (#19601) [source](./.skilld/releases/v4.2.0.md#added)

- NEW: Logical size utilities — added in v4.2.0, provides inline and block sizing: `inline-*`, `min-inline-*`, `max-inline-*`, `block-*`, `min-block-*`, `max-block-*` (#19612) [source](./.skilld/releases/v4.2.0.md#added)

- NEW: Logical inset utilities — added in v4.2.0, provides logical inset positioning: `inset-s-*`, `inset-e-*`, `inset-bs-*`, `inset-be-*` as replacements for `start-*` and `end-*` (#19613) [source](./.skilld/releases/v4.2.0.md#added)

- NEW: `font-features-*` utility — added in v4.2.0, controls `font-feature-settings` CSS property for advanced typography (#19623) [source](./.skilld/releases/v4.2.0.md#added)

- NEW: `PluginWithConfig` type export — added in v4.3.0, exported from `tailwindcss/plugin` to fix TypeScript errors when inferring plugin config types (#19707) [source](./.skilld/releases/v4.3.0.md#fixed)

**Also changed:** `--default(…)` in functional `@utility` · mauve/olive/mist/taupe colour palettes · `@variant` inside `@custom-variant` fixed · arbitrary `:has()` variants canonicalized to `has-[…]` · canonicalization now collapsing multi-directional utilities like `px-[1.2rem] py-[1.2rem]` → `p-[1.2rem]`
<!-- /skilld:api-changes -->

<!-- skilld:best-practices -->

## Tailwind CSS v4.3.3 Best Practices

## Best Practices

- Use `@theme` to define design tokens rather than `:root` CSS variables — `@theme` makes Tailwind generate corresponding utility classes, while `:root` variables don't map to utilities [source](./.skilld/docs/theme.mdx:L54-60)

- Define functional utilities with `@utility name-*` (with `-*`) when you need to accept values via `--value()` and `--modifier()` — static utilities without `-*` don't support dynamic values [source](./.skilld/discussions/discussion-20244.md:L33-63)

- Create static utilities with `@utility name` (without `-*`) for fixed values that don't need parameters — these are useful for binary switches like `content-auto` or `scrollbar-hidden` [source](./.skilld/docs/adding-custom-styles.mdx:L408-415)

- Use `--spacing()` function to access the spacing scale in custom utilities, even when referencing theme values — this ensures bare integers like `p-4` resolve correctly [source](./.skilld/discussions/discussion-20218.md:L25-31)

- Support multiple value types in functional utilities by stacking multiple `--value()` declarations — Tailwind will resolve them left to right and omit declarations that fail [source](./.skilld/docs/adding-custom-styles.mdx:L531-580)

- Add `--default()` to functional utilities to support usage without explicit values — allows utilities like `tab` to use a default while `tab-2` provides a custom value [source](./.skilld/docs/adding-custom-styles.mdx:L583-608)

- Use logical properties for width, margin, padding, and inset (added in v4.2.0) instead of directional properties for better internationalisation support — e.g. `pbs-*` for `padding-block-start` instead of `pt-*` [source](./.skilld/releases/v4.2.0.md:L13-21)

- Define custom theme namespaces to group related values — utilities in `--color-*`, `--spacing-*`, `--text-*` namespaces automatically generate corresponding utility classes [source](./.skilld/docs/theme.mdx:L129-301)

- Use `@layer base`, `@layer components`, and `@layer utilities` to control CSS specificity cascade when adding custom styles — component classes can be overridden by utility classes when placed in the correct layer [source](./.skilld/docs/adding-custom-styles.mdx:L238-297)

- Use `@custom-variant` to create reusable custom variants instead of inline arbitrary variants — custom variants can be applied consistently and combined with other variants [source](./.skilld/docs/adding-custom-styles.mdx:L672-709)

- Use `@variant` directive to apply Tailwind variants within custom CSS and component classes — supports both stacked variants like `@variant hover:focus { … }` and compound variants like `@variant hover, focus { … }` [source](./.skilld/docs/adding-custom-styles.mdx:L299-400)

- Prefer canonical utility classes over arbitrary values when the value exists in your theme — arbitrary values like `w-[123px]` should be reserved for design specifications that don't map cleanly to your scale [source](./.skilld/discussions/discussion-20142.md:L26-34)

- Use type hints with arbitrary values when resolving CSS variables ambiguously — e.g. `text-(length:--my-var)` vs `text-(color:--my-var)` to clarify whether a value is a length or color [source](./.skilld/docs/adding-custom-styles.mdx:L197-207)

<!-- /skilld:best-practices -->
