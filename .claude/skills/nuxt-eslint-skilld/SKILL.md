---
name: nuxt-eslint-skilld
description: 'ALWAYS use when writing code importing "@nuxt/eslint". Consult for debugging, best practices, or modifying @nuxt/eslint, nuxt/eslint, nuxt eslint, eslint.'
metadata:
  version: 1.15.2
  generated_by: Anthropic · Haiku 4.5
  generated_at: 2026-05-31
---

# nuxt/eslint `@nuxt/eslint@1.15.2`

**Tags:** next: 0.3.0-beta.10, latest: 1.15.2

**References:** [package.json](./.skilld/pkg/package.json) • [README](./.skilld/pkg/README.md) • [Issues](./.skilld/issues/_INDEX.md) • [Discussions](./.skilld/discussions/_INDEX.md)

## Search

Use `skilld search "query" -p @nuxt/eslint` instead of grepping `.skilld/` directories. Run `skilld search --guide -p @nuxt/eslint` for full syntax, filters, and operators.

<!-- skilld:api-changes -->

## API Changes

This section documents version-specific API changes for @nuxt/eslint v1.15.2 — prioritizing APIs that changed behavior, were removed, or are commonly misused.

## Primary APIs

- NEW: `withNuxt()` — the main composable for importing generated Nuxt ESLint config in `eslint.config.mjs`. Returns a `FlatConfigComposer` instance with chainable methods for manipulating flat config. This is the recommended way to set up ESLint in Nuxt 4+ projects, replacing manual config imports [source](./.skilld/pkg/README.md:L8-L108)

- NEW: `createConfigForNuxt()` — low-level config factory function from `@nuxt/eslint-config` package for projects that don't use the module. Returns a `FlatConfigComposer` instance with support for options like `features.tooling`, `features.typescript`, and `features.stylistic` for fine-grained control over rule inclusion [source](./.skilld/references/@nuxt/eslint@1.15.2/docs/content/1.packages/1.config.md:L42-L120)

## Configuration Changes

- BREAKING: `config.standalone` option added — set to `false` when combining `@nuxt/eslint` with external presets like `@antfu/eslint-config` to avoid "Different instances of plugin" errors. Default `true` bundles all base plugins (JS, TS, Vue) which causes conflicts with other preset instances [source](./.skilld/references/@nuxt/eslint@1.15.2/docs/content/1.packages/0.module.md:L262-L292)

- BREAKING: `nuxt/typescript/rules` — correct override key for TypeScript rule customization via `.override()`. Old documentation showed `nuxt/typescript`, but that refers only to the plugin setup, not the rules config. Must use `nuxt/typescript/rules` to mutate actual rules [source](./.skilld/issues/issue-574.md)

- NEW: `features.tooling` option (experimental) — enables additional rule sets (`unicorn`, `regexp`, `jsdoc`) for module/library authors when set to `true` in `createConfigForNuxt()`. Can be configured per-rule with an object: `tooling: { regexp: false }` [source](./.skilld/references/@nuxt/eslint@1.15.2/docs/content/1.packages/1.config.md:L89-L119)

- NEW: Type-aware linting via `typescript: { tsconfigPath: './tsconfig.json' }` option — automatically activates `projectService` and includes `recommended-type-checked` / `strict-type-checked` rulesets. Replaces manual `languageOptions.parserOptions.project` configuration [source](./.skilld/references/@nuxt/eslint@1.15.2/docs/content/1.packages/1.config.md:L137-L150)

## Rule Changes

- DEPRECATED: `@nuxtjs/eslint-module` — merged into `@nuxt/eslint` as opt-in `checker` feature. Replace module import with `@nuxt/eslint` and move checker options under `eslint.checker` in `nuxt.config.ts` [source](./.skilld/references/@nuxt/eslint@1.15.2/docs/content/2.guide/1.migration.md)

- BREAKING: `import/order` rule — NOT included in built-in import config. Only `import/first`, `import/no-duplicates`, `import/no-mutable-exports`, and `import/no-named-default` are provided. Import sorting requires adding a separate plugin or explicit rule configuration [source](./.skilld/references/@nuxt/eslint@1.15.2/sections/_BEST_PRACTICES.md:L28)

- BREAKING: `vue/component-tags-order` rule — removed from bundled `eslint-plugin-vue`. Use `vue/block-order` instead (renamed) to control tag ordering in `.vue` files [source](./.skilld/references/@nuxt/eslint@1.15.2/sections/_BEST_PRACTICES.md:L34)

## FlatConfigComposer Methods

- NEW: `.prepend()` — prepend configs before Nuxt configs in the chain. Complements `.append()` for flexible config composition [source](./.skilld/references/@nuxt/eslint@1.15.2/docs/content/1.packages/0.module.md:L190-L204)

- NEW: `.remove()` — remove built-in config layers (e.g., remove auto-generated gitignore config to lint submodules). More precise than `.override()` for bulk removal [source](./.skilld/references/@nuxt/eslint@1.15.2/sections/_BEST_PRACTICES.md:L36)

- NEW: `.onResolved()` — bulk rule mutations across all configs in one pass. Useful for downgrading all `@typescript-eslint` errors to warnings or other global rule changes [source](./.skilld/references/@nuxt/eslint@1.15.2/sections/_BEST_PRACTICES.md:L38)

## Plugin Rules

- NEW: `nuxt/prefer-import-meta` — enforces `import.meta.client` / `import.meta.server` instead of `process.client` / `process.server` in Nuxt 3+ projects [source](./.skilld/references/@nuxt/eslint@1.15.2/docs/content/1.packages/2.plugin.md:L22-L32)

## Configuration Deprecations

- DEPRECATED: Legacy `.eslintrc` config format — not supported. Module and config packages generate and require ESLint flat config format (ESLint 9+, supported since ESLint 8.45.0) [source](./.skilld/references/@nuxt/eslint@1.15.2/docs/content/1.packages/0.module.md:L7-L11)

- DEPRECATED: `nuxt.config.ts` ESLint option in old `@nuxt/eslint` v0.x — replaced with `eslint` module option in Nuxt 4 projects. Check module documentation for current syntax [source](./.skilld/references/@nuxt/eslint@1.15.2/docs/content/2.guide/0.faq.md:L29-L35)

**Also changed:** `config.stylistic` boolean or object support (opt-in formatting rules) · `config.autoInit` toggle for auto-generating `eslint.config.mjs` on first server start · `checker: true` option to enable ESLint along dev server (replaces `@nuxtjs/eslint-module`) · `formatters` config (with `markdown` field) for linting non-JS files · `sortConfigKeys` automatic on stylistic mode for `nuxt.config.ts` ordering

<!-- /skilld:api-changes -->

<!-- skilld:best-practices -->

## Best Practices

- Run `nuxt prepare` (or `nuxi prepare`) before linting -- `withNuxt()` imports from `.nuxt/eslint.config.mjs` which is only generated during the Nuxt build/prepare phase, not from the npm package directly [source](./.skilld/issues/issue-609.md)

- Set `config.standalone` to `false` in `nuxt.config.ts` when combining with external config presets like `@antfu/eslint-config` -- standalone mode (the default) bundles its own base configs (JS, TS, Vue, import plugins), which causes "Different instances of plugin" errors when another preset provides the same plugins [source](./.skilld/issues/issue-568.md)

- Use `nuxt/typescript/rules` as the override key for TypeScript rule customisation, not `nuxt/typescript` -- the actual named config containing the rules is `nuxt/typescript/rules`, while `nuxt/typescript` refers only to the plugin setup block [source](./.skilld/issues/issue-574.md)

- Enable type-aware linting by setting `typescript: { tsconfigPath: './tsconfig.json' }` in the module config rather than manually adding `parserOptions.project` -- this activates `projectService` and automatically includes `recommended-type-checked` and `strict-type-checked` rulesets [source](./.skilld/discussions/discussion-544.md)

```ts
// nuxt.config.ts
export default defineNuxtConfig({
  modules: ["@nuxt/eslint"],
  eslint: {
    config: {
      typescript: {
        strict: true,
        tsconfigPath: "./tsconfig.json",
      },
    },
  },
});
```

- Wrap third-party flat config objects in an array when passing to `withNuxt()` -- single config objects are not iterable, so spreading them with `...config` throws a `[Symbol.iterator]` error [source](./.skilld/discussions/discussion-409.md#accepted-answer)

- The built-in import config does not include `import/order` -- it only provides `import/first`, `import/no-duplicates`, `import/no-mutable-exports`, and `import/no-named-default`. Import sorting requires adding a separate plugin or rule configuration [source](./.skilld/discussions/discussion-593.md)

- When `formatters: true` is set, markdown formatting is disabled by default because many Nuxt projects use MDC syntax with `@nuxt/content`, which Prettier does not fully understand -- enable it explicitly with `formatters: { markdown: true }` only if not using MDC [source](./.skilld/pkg-eslint/dist/chunks/formatters.mjs:L30)

- Enabling `stylistic` automatically activates `nuxt/nuxt-config-keys-order` to enforce consistent key ordering in `nuxt.config.ts` -- this is controlled by `sortConfigKeys` which defaults to `true` when stylistic is on [source](./.skilld/pkg-eslint/dist/shared/eslint-config.Bw-e4MbC.mjs:L127)

- Use `vue/block-order` instead of `vue/component-tags-order` for SFC tag ordering -- the latter is removed from the bundled eslint-plugin-vue and will throw "Could not find" errors at runtime [source](./.skilld/discussions/discussion-618.md)

- Use `.remove()` instead of `.override()` to replace built-in config layers like gitignore -- for example, to lint git submodules, remove the auto-generated gitignore config and add a custom `eslint-config-flat-gitignore` instance with `filesGitModules: []` [source](./.skilld/discussions/discussion-600.md#accepted-answer)

- Use `.onResolved()` for bulk rule mutations across all configs -- for example, downgrading all `@typescript-eslint` and `@stylistic` errors to warnings in one pass rather than overriding each rule individually [source](./.skilld/discussions/discussion-588.md)

- When `stylistic` is not enabled, the module explicitly disables 10+ Vue template formatting rules (`html-indent`, `html-quotes`, `max-attributes-per-line`, `multiline-html-element-content-newline`, etc.) by setting them to `undefined` -- this prevents Vue's recommended config from enforcing formatting that conflicts with external formatters like Prettier [source](./.skilld/pkg-eslint/dist/chunks/vue.mjs:L136)

- Pass ignores as a standalone config object inside an array to `withNuxt()`, not as a property mixed into a rules config -- global ignores in flat config only work when the config object contains only `ignores` and no other keys like `rules` or `files` [source](./.skilld/discussions/discussion-413.md#accepted-answer)

- Use `// @ts-expect-error` or type casting when spreading `typescript-eslint` configs into `withNuxt()` -- the types from `typescript-eslint` are incompatible with ESLint's core `FlatConfig` types, which is an upstream issue acknowledged by the maintainer with no planned fix in `@nuxt/eslint` [source](./.skilld/issues/issue-497.md)
<!-- /skilld:best-practices -->
