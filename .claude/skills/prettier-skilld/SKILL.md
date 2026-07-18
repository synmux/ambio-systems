---
name: prettier-skilld
description: 'Prettier is an opinionated code formatter. ALWAYS use when writing code importing "prettier". Consult for debugging, best practices, or modifying prettier.'
metadata:
  version: 3.9.5
  generated_by: cached
  generated_at: 2026-07-18
---

# prettier/prettier `prettier@3.9.5`

**Tags:** next: 4.0.0-alpha.13, latest: 3.9.5

**References:** [package.json](./.skilld/pkg/package.json) • [README](./.skilld/pkg/README.md) • [Docs](./.skilld/docs/_INDEX.md) • [Issues](./.skilld/issues/_INDEX.md) • [Discussions](./.skilld/discussions/_INDEX.md) • [Releases](./.skilld/releases/_INDEX.md)

## Search

Use `skilld search "query" -p prettier` instead of grepping `.skilld/` directories. Run `skilld search --guide -p prettier` for full syntax, filters, and operators.

<!-- skilld:api-changes -->

## API Changes

This section documents version-specific API changes for Prettier v3.x — prioritise recent major/minor releases.

- BREAKING: `comment.placement` property undocumented but used by plugins, deleted in v3.9.0 and restored v3.9.5 [source](./.skilld/releases/CHANGELOG.md:L152:L155)

- NEW: Async preprocess support in printer plugins — v3.7.0 added ability for `preprocess` method to return `Promise<AST>` [source](./.skilld/docs/plugins.md:L175)

- NEW: `canAttachComment(node, ancestors)` — second parameter `ancestors` added in v3.7.0 to identify ancestor nodes during comment attachment [source](./.skilld/docs/plugins.md:L469)

- NEW: `printPrettierIgnored` printer method — v3.7.0 added optional method to override handling of prettier-ignore'd nodes instead of reprinting raw text [source](./.skilld/docs/plugins.md:L435)

- NEW: `printers` property in plugin type declarations — v3.8.1 made `printers` property typed and accessible from imported plugins, previously resolved to `any` [source](./.skilld/releases/CHANGELOG.md:L516:L530)

- BREAKING: `prettier.getFileInfo()` change — v3.7.0 internally refactored and broke VSCode extension plugin loading (fixed v3.7.3) [source](./.skilld/releases/CHANGELOG.md:L602:L604)

- BREAKING: `module-sync` condition removed from `package.json` — v3.5.2 removed ESM/CommonJS interop feature due to incompatibility with mixed plugin imports [source](./.skilld/releases/CHANGELOG.md:L776:L778)

**Also changed:** Support for TypeScript 5.2 `using` / `await using` declaration v3.0.3 · Include `printers` export in plugin type definitions v3.0.1 · TypeScript 5.0 `const` modifiers for type parameters v2.8.5 · Custom Parser API removed (replaced by Plugin API) v3.0.0
<!-- /skilld:api-changes -->

<!-- skilld:best-practices -->

## Best Practices

- Always await Prettier's async APIs — use `@prettier/sync` only when synchronous execution is required [source](./.skilld/docs/api.md#L8:12)

- Use `prettier.resolveConfig()` with spread syntax to apply discovered config alongside parsed options, enabling consistent formatting across programmatic and CLI usage [source](./.skilld/docs/api.md#prettier-resolveconfig)

```js
const options = await prettier.resolveConfig(filePath);
const formatted = await prettier.format(text, {
  ...options,
  filepath: filePath,
});
```

- For editor integrations, use `prettier.formatWithCursor()` instead of `format()` to preserve cursor position and prevent jarring jumps when reformatting [source](./.skilld/docs/api.md#prettier-formatwithcursor)

- Validate formatting in CI with `prettier.check()` rather than attempting to parse CLI output — returns a boolean promise matching `--check` semantics [source](./.skilld/docs/api.md#prettier-check)

- Never place the `parser` option at the top level of configuration — only use it inside `overrides` blocks to avoid disabling Prettier's automatic parser inference for all file types [source](./.skilld/docs/configuration.md#setting-the-parser-option)

- Use TypeScript configuration files (`.prettierrc.ts` or `prettier.config.ts`) with `import { type Config }` for type-safe configuration and IDE autocomplete [source](./.skilld/docs/configuration.md#typescript-configuration-files)

- Avoid `eslint-plugin-prettier` for linting workflows — instead use `eslint-config-prettier` to disable conflicting ESLint stylistic rules, reducing performance overhead and editor noise [source](./.skilld/docs/integrating-with-linters.md)

- For pre-commit hooks, choose `lint-staged` when combining Prettier with other code quality tools; use `git-format-staged` when partial-file formatting with strong guarantees is required [source](./.skilld/docs/precommit.md)

- Create a `.prettierignore` file in your project root to make `prettier --write .` safe across all tools and editors — prevents formatting generated files or build artifacts [source](./.skilld/docs/ignore.md#ignoring-files-prettierignore)

- Use `// prettier-ignore` pragma comments (language-agnostic) to selectively exclude individual AST nodes from formatting, preserving intentional manual layouts within files [source](./.skilld/docs/ignore.md#javascript)

- Share Prettier configurations as scoped npm packages (`@username/prettier-config`) and extend them via spread syntax rather than string references to allow composition and overrides [source](./.skilld/docs/sharing-configurations.md)

- Always quote glob patterns with double quotes (`"**/*.js"`) in CLI commands to ensure the shell does not expand them prematurely and to maintain cross-platform compatibility [source](./.skilld/docs/cli.md#file-patterns)

- Use `--check` instead of `--list-different` in CI pipelines for human-friendly output; exits with code 1 and summarises violations, avoiding fragile parsing of file lists [source](./.skilld/docs/cli.md#--check)

- Leverage async preprocessing in plugins (added in v3.7.0) to transform source text before parsing, enabling support for custom template languages and code generation [source](./.skilld/docs/plugins.md#optional-preprocess)

<!-- /skilld:best-practices -->
