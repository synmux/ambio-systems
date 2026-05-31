---
name: eslint-skilld
description: 'ALWAYS use when writing code importing "eslint". Consult for debugging, best practices, or modifying eslint.'
metadata:
  version: 10.4.1
  generated_by: Anthropic · Haiku 4.5
  generated_at: 2026-05-31
---

# eslint/eslint `eslint@10.4.1`

**Tags:** es6jsx: 0.11.0-alpha.0, next: 10.0.0-rc.2, maintenance: 9.39.4

**References:** [package.json](./.skilld/pkg/package.json) • [README](./.skilld/pkg/README.md) • [Docs](./.skilld/docs/_INDEX.md) • [Issues](./.skilld/issues/_INDEX.md) • [Discussions](./.skilld/discussions/_INDEX.md) • [Releases](./.skilld/releases/_INDEX.md)

## Search

Use `skilld search "query" -p eslint` instead of grepping `.skilld/` directories. Run `skilld search --guide -p eslint` for full syntax, filters, and operators.

<!-- skilld:api-changes -->

## API Changes

This section documents version-specific API changes for ESLint v10.x, prioritizing recent major/minor releases and APIs that LLMs trained on older data may use incorrectly.

## Breaking Changes (v10.0.0 → v10.2.0)

- BREAKING: Removed deprecated `SourceCode` methods — `getTokenOrCommentBefore()`, `getTokenOrCommentAfter()`, `isSpaceBetweenTokens()`, `getJSDocComment()` all removed; use `getTokenBefore(node, { includeComments: true })`, `getTokenAfter(node, { includeComments: true })`, `isSpaceBetween()` instead [source](./.skilld/docs/src/use/migrate-to-10.0.0.md:L367:389)

- BREAKING: Removed deprecated rule `context` methods — `context.getCwd()`, `context.getFilename()`, `context.getPhysicalFilename()`, `context.getSourceCode()` all removed; use `context.cwd`, `context.filename`, `context.physicalFilename`, `context.sourceCode` instead [source](./.skilld/docs/src/use/migrate-to-10.0.0.md:L326:349)

- BREAKING: Removed `context.parserOptions` and `context.parserPath` — use `context.languageOptions.parserOptions` instead, no replacement for `parserPath` [source](./.skilld/docs/src/use/migrate-to-10.0.0.md:L326:349)

- BREAKING: `Program` AST node `range` now spans entire source text including leading/trailing comments/whitespace, previously excluded them [source](./.skilld/docs/src/use/migrate-to-10.0.0.md:L274:295)

- BREAKING: Fixer methods require string `text` arguments — `insertTextBefore()`, `insertTextAfter()`, `replaceText()`, `replaceTextRange()`, and related methods now throw `TypeError` if text is not a string [source](./.skilld/docs/src/use/migrate-to-10.0.0.md:L297:312)

- BREAKING: RuleTester no longer allows `errors` or `output` properties in valid test cases; must be removed [source](./.skilld/docs/src/use/migrate-to-10.0.0.md:L391:417)

- BREAKING: Removed `nodeType` property from `LintMessage` objects — custom formatters and integrations must no longer access `message.nodeType` [source](./.skilld/docs/src/use/migrate-to-10.0.0.md:L419:425)

- BREAKING: Removed `type` property in errors of invalid `RuleTester` test cases — using this property now throws an error [source](./.skilld/docs/src/use/migrate-to-10.0.0.md:L266:272)

- BREAKING: Old `.eslintrc` configuration format no longer supported — must use `eslint.config.js`; `FlatESLint` and `LegacyESLint` exports removed; `Linter` class `configType` option can no longer be `"eslintrc"` [source](./.skilld/docs/src/use/migrate-to-10.0.0.md:L95:107)

- BREAKING: Configuration file lookup algorithm changed — `v10_config_lookup_from_file` feature flag removed; new behavior (search from file directory upward) is now default; must remove flag from CLI, environment, or API calls [source](./.skilld/docs/src/use/migrate-to-10.0.0.md:L81:93)

- BREAKING: JSX references now tracked — `<Component>` is now a reference to the imported component; may produce new false positives/negatives; rules like `@eslint-react/jsx-uses-vars` no longer needed [source](./.skilld/docs/src/use/migrate-to-10.0.0.md:L109:132)

- BREAKING: `eslint-env` comments now reported as errors — comments like `/* eslint-env node */` must be removed; no longer supported by new config system [source](./.skilld/docs/src/use/migrate-to-10.0.0.md:L134:146)

- BREAKING: Custom `ScopeManager` implementations must provide `addGlobals(names: string[])` method for global variable resolution [source](./.skilld/docs/src/use/migrate-to-10.0.0.md:L314:324)

- BREAKING: Node.js < v20.19, v21, v23 no longer supported — ESLint v10 requires Node.js v20.19+, v22.13+, or v24+ [source](./.skilld/docs/src/use/migrate-to-10.0.0.md:L57:67)

- BREAKING: `stylish` formatter uses native `styleText` instead of `chalk` — respects `NO_COLOR`, `NODE_DISABLE_COLORS` environment variables; `--color`/`--no-color` CLI flags now take precedence over environment variables [source](./.skilld/docs/src/use/migrate-to-10.0.0.md:L172:189)

- BREAKING: `func-names` rule schema stricter — extra array items beyond allowed options no longer accepted; must contain only base string option and optionally object option [source](./.skilld/docs/src/use/migrate-to-10.0.0.md:L224:240)

- BREAKING: `no-invalid-regexp` `allowConstructorFlags` option requires unique items — duplicate flags in array now result in configuration error [source](./.skilld/docs/src/use/migrate-to-10.0.0.md:L242:254)

- DEPRECATED: `radix` rule options `"always"` and `"as-needed"` deprecated in v10.0.0 — behavior unchanged, remove option if explicitly set (defaults to enforcing radix) [source](./.skilld/docs/src/use/migrate-to-10.0.0.md:L191:203)

## New APIs (v10.0.0 → v10.2.0)

- NEW: `meta.languages` property support for rules (v10.2.0) — allows rules to declare language support [source](./.skilld/releases/v10.2.0.md:L10)

- NEW: Bulk suppressions API implementation (v10.1.0) — adds API support for managing multiple suppressions [source](./.skilld/releases/v10.1.0.md:L11)

- NEW: RuleTester `requireData` assertion option (v10.0.0) — new assertion option for test cases [source](./.skilld/releases/v10.0.0.md:L37)

## Config & Runtime Changes

- BREAKING: `no-shadow-restricted-names` rule now reports `globalThis` by default — `reportGlobalThis` option now defaults to `true`; must rename identifiers or explicitly disable with `{ "reportGlobalThis": false }` [source](./.skilld/docs/src/use/migrate-to-10.0.0.md:L205:222)

- BREAKING: `name` property restored to ESLint core configs exported from `@eslint/js` — may require `@eslint/eslintrc` upgrade if using `FlatCompat` utility [source](./.skilld/docs/src/use/migrate-to-10.0.0.md:L256:264)

- NEW: `Temporal` global added to ES2026 globals and `no-obj-calls` rule (v10.2.0) [source](./.skilld/releases/v10.2.0.md:L11:12)

**Also changed:** Array callback return handling for `Array.fromAsync()` improved · Error location output added to RuleTester failure messages · `max-params` rule `countThis` option · `require-yield` and `no-useless-constructor` error locations updated · Jiti < v2.2.0 support dropped · Minimatch v10 enables POSIX character classes in glob patterns

<!-- /skilld:api-changes -->

<!-- skilld:best-practices -->

## ESLint v10.4.1 Best Practices

## Overview

This document captures non-obvious, production-grade patterns for ESLint v10.4.1. These practices cover configuration, API usage, custom rules, and testing strategies that differ from what developers might naturally assume.

## Best Practices

- Use `defineConfig()` and `globalIgnores()` helpers when creating flat config files — they make configuration intent explicit and prevent accidental pattern misinterpretation [source](./.skilld/docs/src/use/configure/configuration-files.md:L34:46)

- Always specify `files` patterns in configuration objects to prevent unintended rule application to non-matching file types — omitting `files` applies rules to all matched files unless explicitly excluded [source](./.skilld/docs/src/use/configure/configuration-files.md:L143:144)

- Use the `ESLint` class for Node.js applications and file system operations; use the `Linter` class for browser environments or when filesystem access is unavailable — each is optimized for its context [source](./.skilld/docs/src/integrate/nodejs-api.md:L16:18)

- Enable the `stats` option on ESLint instances to measure rule performance — rule timing data reveals bottlenecks without instrumenting individual rules [source](./.skilld/docs/src/integrate/nodejs-api.md:L153:154)

- Use `messageId` references instead of inline `message` strings in `context.report()` — centralizing messages in `meta.messages` reduces duplication across rule file and tests, enabling easier message maintenance [source](./.skilld/docs/src/extend/custom-rules.md:L244:250)

- Declare `meta.fixable` and `meta.hasSuggestions` properties when implementing fixes or suggestions — ESLint will throw an error at runtime if these properties are absent but the feature is used [source](./.skilld/docs/src/extend/custom-rules.md:L61:65)

- Keep fixes as small as possible and avoid changing runtime behaviour — narrow fixes prevent conflicts with other rules; behavioural changes cause user confusion [source](./.skilld/docs/src/extend/custom-rules.md:L356:361)

- Use `RuleTester` for unit testing custom rules, setting `assertionOptions.requireMessage: true` to enforce consistent error assertions — this prevents test coverage gaps from masked violations [source](./.skilld/docs/src/integrate/nodejs-api.md:L865:905)

- Use `extends` in configuration objects to inherit predefined or plugin configurations — this composes configurations modularly and applies transformations consistently across files [source](./.skilld/docs/src/use/configure/configuration-files.md:L602:684)

- Use cascading configuration objects (multiple `files` patterns) for file-specific rules rather than a single monolithic config — cascading applies base rules to all files then adds or overrides for subsets [source](./.skilld/docs/src/use/configure/configuration-files.md:L428:457)

- Set the `name` property in every configuration object, especially shared or plugin configs — names appear in error messages and the config inspector, making it easier to debug which config applied [source](./.skilld/docs/src/use/configure/configuration-files.md:L731:780)

- Access `context.sourceCode` to query tokens, comments, and scope when rules need to inspect whitespace, formatting, or variable tracking — using `sourceCode` methods is the documented API for AST queries [source](./.skilld/docs/src/extend/custom-rules.md:L556:610)

- Specify a JSON Schema in `meta.schema` or explicitly set `schema: false` to opt out of validation — omitting the property defaults to rejecting any rule options [source](./.skilld/docs/src/extend/custom-rules.md:L670:675)

- Copy core rule implementations into custom rules if you need to extend or modify them — core rules are not part of the public API and are not designed for extension [source](./.skilld/docs/src/extend/custom-rules.md:L34:36)
<!-- /skilld:best-practices -->
