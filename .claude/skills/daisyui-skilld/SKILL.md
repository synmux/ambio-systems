---
name: daisyui-skilld
description: 'daisyUI 5 - The Tailwind CSS Component Library. ALWAYS use when writing code importing "daisyui". Consult for debugging, best practices, or modifying daisyui.'
metadata:
  version: 5.6.18
  generated_by: cached
  generated_at: 2026-07-18
---

# saadeghi/daisyui `daisyui@5.6.18`

**Tags:** alpha: 5.6.0-alpha.4, beta: 5.6.0-beta.0, latest: 5.6.18

**References:** [package.json](./.skilld/pkg/package.json) • [README](./.skilld/pkg/README.md) • [Docs](./.skilld/docs/_INDEX.md) • [Issues](./.skilld/issues/_INDEX.md) • [Discussions](./.skilld/discussions/_INDEX.md) • [Releases](./.skilld/releases/_INDEX.md)

## Search

Use `skilld search "query" -p daisyui` instead of grepping `.skilld/` directories. Run `skilld search --guide -p daisyui` for full syntax, filters, and operators.

<!-- skilld:api-changes -->

## API Changes

This section documents version-specific API changes in daisyUI v5.6.x — the most recent minor release.

### New Components (v5.6.0)

- NEW: `.aura` — new Aura component added for enhanced UI flexibility [source](./.skilld/releases/CHANGELOG.md:L139)

- NEW: `.otp` — new OTP (one-time password) input component for authentication flows [source](./.skilld/releases/CHANGELOG.md:L140)

- NEW: `.megamenu` — new Megamenu component for complex multi-level navigation [source](./.skilld/releases/CHANGELOG.md:L141)

### New Utilities and Features (v5.6.0)

- NEW: `.range-vertical` — vertical range slider class, complements existing `.range` for vertical orientation [source](./.skilld/releases/CHANGELOG.md:L142)

- NEW: `tooltip-start`, `tooltip-center`, `tooltip-end` — tooltip alignment utilities for precise positioning, closing #4229 [source](./.skilld/releases/CHANGELOG.md:L144)

- NEW: HTML popover support for `.modal` — modals now support native HTML popover API for improved dialog handling [source](./.skilld/releases/CHANGELOG.md:L143)

- NEW: `.btn-active` — exposed as a standalone utility class in v5.6.1, previously only available as a state [source](./.skilld/releases/CHANGELOG.md:L132)

- NEW: `.menu` element support — `<menu>` HTML elements are now supported as `.menu` containers, not just `<div>` [source](./.skilld/releases/CHANGELOG.md:L153)

- NEW: `.card` checked/selected focus states — cards now support `.selected` and `.selectable` classes with proper focus and checked styling [source](./.skilld/releases/CHANGELOG.md:L154)

### Breaking Changes and Behavioral Changes (v5.6.0)

- BREAKING: Button styles completely rewritten — `.btn` styling changed significantly including checked, disabled, soft, ghost, link, and focus states; old button markup may render differently [source](./.skilld/releases/CHANGELOG.md:L151)

- BREAKING: Join styles simplified and nested join leakage prevented — `.join-item` nesting behavior changed; styles for nested joins no longer propagate in v5.6.14 onwards [source](./.skilld/releases/CHANGELOG.md:L150) and [source](./.skilld/releases/CHANGELOG.md:L40)

- BREAKING: Rating size modifiers now responsive — `.rating-lg`, `.rating-md`, `.rating-sm`, `.rating-xs` now use Tailwind responsive breakpoints; fixed-size ratings require explicit breakpoint prefixes [source](./.skilld/releases/CHANGELOG.md:L146)

- BREAKING: Input, textarea, select, and floating label sizing changed — sizing is improved but may affect layouts expecting v5.5 dimensions [source](./.skilld/releases/CHANGELOG.md:L147)

- BREAKING: `.select-xs` and `.select-sm` sizing broken in v5.6.0-5.6.4 — these sizes rendered same as `.select-md` due to CSS generation order; fixed in v5.6.5, use v5.6.5+ [source](./.skilld/discussions/discussion-4620.md)

- BREAKING: `.tab` class conflict with Tailwind 4.3.0 — Tailwind added its own `tab` bare utility; daisyUI `.tab` component class was de-prioritized; fixed in v5.6.5 with proper layering [source](./.skilld/releases/CHANGELOG.md:L104)

- BREAKING: `.collapse` overflow behavior when closed changed — improved overflow handling may affect collapsed state rendering [source](./.skilld/releases/CHANGELOG.md:L148)

- BREAKING: `.select` customization changed — new `.selectedcontent` default styling for customizable select elements; custom select content now has base styles [source](./.skilld/releases/CHANGELOG.md:L152)

**Also changed:** `.tabs-border` line sizing · `.modal-start` and `.modal-end` RTL · `.indicator` alignment with child items · `.fab-flower` action fan-out · `.swap-active` rotate/flip compatibility · `.select-ghost` background opacity · `.diff` card integration · file input styling cleanup
<!-- /skilld:api-changes -->

<!-- skilld:best-practices -->

## Best Practices

- Use `@plugin "daisyui"` with Tailwind CSS 4.x plugin syntax for module resolution reliability — older versions like 4.2.3 had file extension issues with .css imports that caused build failures [source](./.skilld/issues/issue-4505.md:L47:60)

- Define theme variants with `@plugin "daisyui" { themes: light --default, dark --prefersdark; }` in your CSS entry point — this syntax correctly applies the `default` flag without requiring per-theme configuration [source](./.skilld/issues/issue-4488.md:L50:62)

- Use `@plugin "daisyui/theme"` only for customizing colour values and font tokens within existing themes — avoid setting `default: true` inside individual theme definitions as it can cause colour overrides in production builds [source](./.skilld/issues/issue-4488.md)

- Set an appropriate `.browserslistrc` or `browserslist` in `package.json` targeting modern browsers — legacy browser support generates unnecessary CSS rules like `-moz-placeholder` that cause floating labels to misbehave [source](./.skilld/discussions/discussion-4462.md:L30:32)

- Use `<ul>` elements for `.menu` components instead of `<ol>` — the maintainer notes that semantic list numbering is removed by Tailwind's preflight reset and serves no purpose without visible markers [source](./.skilld/discussions/discussion-4473.md:L27:32)

- Use new utility classes `tooltip-start`, `tooltip-center`, and `tooltip-end` for precise tooltip positioning — these were added in v5.6.0 to replace manual positioning workarounds [source](./.skilld/releases/CHANGELOG.md:L144)

- Apply `.btn-active` utility class for button active states — this was exposed as a reusable class in v5.6.1 after button style refactoring and provides reliable visual feedback [source](./.skilld/releases/CHANGELOG.md:L132)

- Use `range-vertical` class for vertical range sliders instead of custom transforms — this component was added in v5.6.0 and handles orientation natively [source](./.skilld/releases/CHANGELOG.md:L142)

- Use HTML `popover` attribute for modal implementations instead of role-based dialogs when targeting modern browsers — daisyUI v5.6.0 added native popover support for HTML popovers [source](./.skilld/releases/CHANGELOG.md:L141)

- Exclude the `properties` file when building with tools that warn about nested `@property` rules — use `@plugin "daisyui" { exclude: properties; }` to suppress PostCSS warnings if custom properties aren't needed [source](./.skilld/issues/issue-3882.md:L58:62)

- Prefer the new Aura, OTP, and Megamenu components introduced in v5.6.0 for their respective use cases — these replace many custom implementations and include built-in accessibility features [source](./.skilld/releases/CHANGELOG.md:L139:141)

- Use font customization via CSS variables in theme definitions — change `--font-sans`, `--font-serif`, etc. in `@plugin "daisyui/theme"` blocks to override default typefaces across all themes [source](./.skilld/discussions/discussion-4401.md:L24:37)

- Check for Tailwind CSS version compatibility before upgrading — Tailwind 4.2.3+ has better plugin resolution, but verify that daisyUI v5.6+ is paired with compatible Tailwind versions (4.2.2 or 4.2.5+) [source](./.skilld/issues/issue-4505.md:L40:45)

- Use custom colour tokens by defining new CSS variables in theme blocks instead of extending Tailwind — this follows daisyUI's documented pattern for colour systems and maintains theme consistency [source](./.skilld/discussions/discussion-4438.md:L34:36)

<!-- /skilld:best-practices -->
