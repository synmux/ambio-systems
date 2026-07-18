---
name: eslint-skilld
description: 'An AST-based pattern checker for JavaScript. ALWAYS use when writing code importing "eslint". Consult for debugging, best practices, or modifying eslint.'
metadata:
  version: 10.7.0
  generated_by: cached
  generated_at: 2026-07-18
---

# eslint/eslint `eslint@10.7.0`

**Tags:** es6jsx: 0.11.0-alpha.0, next: 10.0.0-rc.2, latest: 10.7.0

**References:** [package.json](./.skilld/pkg/package.json) • [README](./.skilld/pkg/README.md) • [Issues](./.skilld/issues/_INDEX.md) • [Discussions](./.skilld/discussions/_INDEX.md) • [Releases](./.skilld/releases/_INDEX.md)

## Search

Use `skilld search "query" -p eslint` instead of grepping `.skilld/` directories. Run `skilld search --guide -p eslint` for full syntax, filters, and operators.

<!-- skilld:api-changes -->

## API Changes

This section documents version-specific API changes — prioritize recent major/minor releases.

### Major Breaking Changes in v10.0.0

- BREAKING: Deprecated `SourceCode` methods removed — replace with documented equivalents on `SourceCode` class [source](./.skilld/releases/v10.0.0.md#breaking-changes)

- BREAKING: Deprecated rule context methods removed — use `context` directly without underscore-prefixed methods [source](./.skilld/releases/v10.0.0.md:L17)

- BREAKING: ESLintRC config format support removed entirely — must use flat config (`eslint.config.js`) [source](./.skilld/releases/v10.0.0.md:L18)

- BREAKING: `ScopeManager#addGlobals()` is now required — replaces implicit global tracking [source](./.skilld/releases/v10.0.0.md:L19)

- BREAKING: `LintMessage#nodeType` and `TestCaseError#type` removed — use type definitions from `@eslint/core` [source](./.skilld/releases/v10.0.0.md:L26)

- BREAKING: jiti < 2.2.0 no longer supported — requires jiti v2.2.0+ [source](./.skilld/releases/v10.0.0.md:L27)

- BREAKING: `eslint-env` comments now report as errors — migrate comments to flat config `languageOptions.globals` [source](./.skilld/releases/v10.0.0.md:L25)

- BREAKING: Node.js version requirement increased — now requires `^20.19.0 || ^22.13.0 || >=24` [source](./.skilld/releases/v10.0.0.md:L31)

- BREAKING: `radix` rule options "always" and "as-needed" deprecated — use options object format or omit for auto-detection [source](./.skilld/releases/v10.0.0.md:L23)

- BREAKING: `chalk` replaced with `styleText` — if using `ResultsMeta`, access `color` property instead of chalk instance [source](./.skilld/releases/v10.0.0.md:L11)

- NEW: `name` field added to config objects — all configs now accept optional `name` property [source](./.skilld/releases/v10.0.0.md:L13)

- NEW: JSX reference tracking now enabled by default — no configuration needed, may affect rule behavior [source](./.skilld/releases/v10.0.0.md:L12)

- NEW: `Program` node now spans entire source text — previously spanned only the parsed content [source](./.skilld/releases/v10.0.0.md:L21)

- NEW: `countThis` option added to `max-params` rule — allows counting `this` binding in parameter count [source](./.skilld/releases/v10.0.0.md:L39)

- NEW: Error assertion options in RuleTester — `requireData` option and enhanced error assertions [source](./.skilld/releases/v10.0.0.md:L37)

### New & Changed APIs in v10.1-v10.7

- NEW: `includeIgnoreFile()` function in `eslint/config` module — loads `.eslintignore` files in flat config [source](./.skilld/releases/v10.4.0.md:L11)

- NEW: `meta.languages` support for rules — indicates which languages a rule applies to (JavaScript, TypeScript, JSON, etc.) [source](./.skilld/releases/v10.2.0.md:L10)

- NEW: `Temporal` globals added to ES2026 — new `Temporal` API object supported in `no-obj-calls` rule [source](./.skilld/releases/v10.2.0.md:L12)

- NEW: Bulk-suppressions API support — new API methods for handling multiple suppressions [source](./.skilld/releases/v10.1.0.md:L11)

- ENHANCED: `no-compare-neg-zero` rule now has suggestions — automatic fix suggestions for zero comparisons [source](./.skilld/releases/v10.7.0.md:L13)

- ENHANCED: `preserve-caught-error` rule adds `errorClassNames` option — control which class names to preserve [source](./.skilld/releases/v10.7.0.md:L10)

- ENHANCED: `max-nested-callbacks` adds constructor callback handling — new option tracks constructors separately [source](./.skilld/releases/v10.7.0.md:L11)

- ENHANCED: `radix` rule enhanced — computed `Number.parseInt` member access and invalid signed numeric radix detection [source](./.skilld/releases/v10.7.0.md:L12)

- ENHANCED: `no-constant-binary-expression` detects `Symbol()` and `BigInt()` — adds safety checks [source](./.skilld/releases/v10.6.0.md:L10)

- ENHANCED: Error location reporting improved across v10.5 — `max-nested-callbacks`, `no-with`, `max-lines-per-function`, `max-depth`, `max-statements` now report at precise locations [source](./.skilld/releases/v10.5.0.md:L10-L16)

**Also changed:** `Array.fromAsync` support in `array-callback-return` · `self` parameter option in `no-implied-eval` · `no-shadow` handles function/class expressions · RuleTester failure index output · error locations in `require-yield` and `no-useless-constructor` · `no-var` autofix in `TSModuleBlock` · `no-unused-private-class-members` suggestions · `ignoreClassesWithImplements` applied to class expressions · `eqeqeq` static template literal handling · `for-direction` sequence expression checking
<!-- /skilld:api-changes -->

<!-- skilld:best-practices -->

## Best Practices

- Use the `ESLint` class for file system operations, not the `Linter` class — the latter is designed for in-browser or in-memory linting only and doesn't handle configuration files or filesystem operations [source](./.skilld/docs/src/integrate/nodejs-api.md#eslint-class)

- Use `defineConfig()` when authoring flat config files to enable type inference and automatic plugin resolution — this helper handles config array composition and validation [source](./.skilld/docs/src/use/configure/configuration-files.md:L33:L44)

- Compose configurations via the `extends` key rather than manually merging config objects — this ensures predictable precedence and enables proper rule resolution across shareable configs [source](./.skilld/docs/src/use/configure/combine-configs.md:L12:L35)

- Specify `meta.namespace` in plugins to enable proper caching and identify plugins even when users assign different namespace aliases in their config [source](./.skilld/docs/src/extend/plugins.md:L49:L65)

- Use predicate functions for `fix` and `ruleFilter` options to selectively apply fixes and rules at runtime — enables fine-grained control over which issues are processed without recreating the ESLint instance [source](./.skilld/docs/src/integrate/nodejs-api.md:L158:L152)

- Enable `cache: true` with `cacheStrategy: "content"` for large projects to avoid redundant linting of unchanged files — metadata strategy is faster but content strategy is more reliable across version upgrades [source](./.skilld/docs/src/integrate/nodejs-api.md:L165:L170)

- Use `concurrency: "auto"` when linting multiple files to leverage worker threads — significantly improves performance on multi-core systems at the cost of slightly higher memory usage [source](./.skilld/docs/src/integrate/nodejs-api.md:L181:L182)

- Use `stats: true` in production integrations to track linting performance metrics — enables per-rule timing analysis via the `stats` property on `LintResult` [source](./.skilld/docs/src/integrate/nodejs-api.md:L153:L154)

- Prefer `messageId` over inline `message` in rule violation reports — centralizes messages in the rule's `meta.messages` object, enabling easier maintenance and translation [source](./.skilld/docs/src/extend/custom-rules.md:L246:L250)

- Use `baseConfig` for default settings that apply to all files, and `overrideConfig` to apply additional configuration on top — baseConfig is applied first, making it suitable for setting baseline rules [source](./.skilld/docs/src/integrate/nodejs-api.md:L143:L146)

- Use `applySuppressions: true` when building integrations that need to respect suppression files — automatically filters suppressed messages from results without requiring manual post-processing [source](./.skilld/docs/src/integrate/nodejs-api.md:L174:L177)

- Specify `ignores` without any other keys in a configuration object to create global ignore patterns — these apply across all configuration objects and files, avoiding duplication [source](./.skilld/docs/src/use/configure/configuration-files.md:L139:L144)

- Use `errorOnUnmatchedPattern: false` in integrations that handle missing files gracefully — prevents errors when glob patterns don't match any files [source](./.skilld/docs/src/integrate/nodejs-api.md:L126:L127)

- Leverage `loadESLint()` for integrations that need to support both flat config and legacy eslintrc systems — automatically detects which system the user's project uses and returns the appropriate implementation [source](./.skilld/docs/src/integrate/nodejs-api.md:L560:L596)

<!-- /skilld:best-practices -->
