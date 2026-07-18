---
name: node-gyp-skilld
description: 'Node.js native addon build tool. ALWAYS use when writing code importing "node-gyp". Consult for debugging, best practices, or modifying node-gyp, node gyp.'
metadata:
  version: 13.0.1
  generated_by: cached
  generated_at: 2026-07-18
---

# nodejs/node-gyp `node-gyp@13.0.1`

**Tags:** latest: 13.0.1

**References:** [package.json](./.skilld/pkg/package.json) • [README](./.skilld/pkg/README.md) • [Issues](./.skilld/issues/_INDEX.md) • [Releases](./.skilld/releases/_INDEX.md)

## Search

Use `skilld search "query" -p node-gyp` instead of grepping `.skilld/` directories. Run `skilld search --guide -p node-gyp` for full syntax, filters, and operators.

<!-- skilld:api-changes -->

## API Changes

This section documents version-specific API changes — prioritise recent major/minor releases.

## Breaking Changes & Removals

- BREAKING: Node version support changed to `^22.22.2 || ^24.15.0 || >=26.0.0` — v13.0.0 dropped support for Node 16, 18, 20, 21. Only Node 22.22.2+, 24.15.0+, and 26+ are now supported [source](./.skilld/releases/v13.0.0.md#breaking-changes)

- BREAKING: `npm_config_python` configuration setting no longer valid — Python must be specified via `--python` CLI flag, `PYTHON` environment variable, or `NODE_GYP_FORCE_PYTHON`. Removed in v12.2.0 [source](./.skilld/releases/v12.2.0.md:L21)

- BREAKING: `make-fetch-happen` replaced with built-in fetch API — Downloads now use native `fetch` instead of the `make-fetch-happen` module since v12.3.0. May affect retry behaviour or error handling in download scenarios [source](./.skilld/releases/v12.3.0.md:L14)

- BREAKING: `url.parse()` and `url.resolve()` replaced with native `URL` class — Switched from deprecated Node.js `url` module methods to the standardised `URL` constructor. URL parsing behaviour may differ slightly [source](./.skilld/releases/v12.3.0.md:L20)

## New Features

- NEW: Visual Studio 2026 (18.x) support — v12.1.0 added detection and support for VS 2026 as a build toolchain on Windows [source](./.skilld/releases/v12.1.0.md:L14)

## Dependency Updates

- Core dependencies upgraded in v13.0.0: `nopt@10.0.0`, `proc-log@7.0.0`, `which@7.0.0` — These internal dependencies have new major versions with potential API changes. If code directly imports these packages, verify compatibility [source](./.skilld/releases/v13.0.0.md:L31-33)

**Also changed:** `gyp-next` updated to v0.22.2 in v12.4.0 · `gyp-next` updated to v0.21.1 in v12.2.0 · `gyp-next` updated to v0.21.0 in v12.0.0 · `env-paths` upgraded to v3.0.0 in v12.0.0 · `make-fetch-happen` upgraded to v15.0.0 in v12.0.0
<!-- /skilld:api-changes -->

<!-- skilld:best-practices -->

## Best Practices

- Use `NODE_GYP_FORCE_PYTHON` environment variable for highest-priority Python version detection — it overrides all other configuration methods and prevents unexpected version mismatches when multiple Python installations exist [source](./.skilld/pkg/README.md#configuring-python-dependency)

- Set `npm_package_config_node_gyp_*` environment variables instead of deprecated `npm_config_*` prefix — npm 11+ removed support for `npm_config_` environment variables, and the new format ensures reliable configuration across npm versions [source](./.skilld/pkg/README.md#environment-variables)

- Run builds with `-j max` or `--jobs n` to parallelise compilation across available CPU cores — dramatically reduces build time on multi-core systems [source](./.skilld/pkg/README.md#command-options)

- Require Python >= v3.12 and node-gyp >= v10 in your package documentation — older combinations fail with cryptic errors due to Python deprecations [source](./.skilld/pkg/README.md#installation)

- Use `variables` section in binding.gyp for configuration that accepts command-line overrides via `--option-name` flags — enables users to customise builds without modifying the file [source](./.skilld/pkg/gyp/docs/UserDocumentation.md:L24)

- Place platform-specific settings within `conditions` blocks keyed by `OS` variable — avoids brittle manual conditionals and ensures correct compilation on all platforms [source](./.skilld/pkg/README.md#the-binding-gyp-file)

- Use `node_shared_openssl` variable to detect whether Node.js bundled OpenSSL statically or linked it from the system — this pattern handles both scenarios automatically without requiring users to manage dual builds [source](./.skilld/docs/Linking-to-OpenSSL.md:L6:12)

- Pass `--dist-url` or `--nodedir` when building for third-party runtimes like Electron — ensures correct headers are downloaded and `config.gypi` is properly generated for non-standard Node.js variants [source](./.skilld/pkg/README.md:L103:113)

- Use `--force-process-config` flag when building against third-party runtimes with known malformed `config.gypi` files — works around configuration errors in older Electron distributions [source](./.skilld/pkg/README.md#command-options)

- Structure binding.gyp with top-level `variables`, `target_defaults`, and `targets` sections — matches the idiomatic gyp pattern and allows sharing settings across multiple targets [source](./.skilld/pkg/gyp/docs/UserDocumentation.md:L23:81)

- Use `.gypi` include files for shared configuration across multiple binding.gyp files — centralises platform detection, common compiler flags, and build paths to avoid duplication [source](./.skilld/pkg/README.md#the-binding-gyp-file)

- Run `node-gyp rebuild` instead of manually running `configure` then `build` — ensures a clean state and catches configuration errors early in development cycles [source](./.skilld/pkg/README.md#how-to-use)

- Don't override npm's bundled node-gyp unless using npm < 6; prefer updating via npm explore commands instead — maintains compatibility with the npm version you're using and avoids version desync [source](./.skilld/docs/Updating-npm-bundled-node-gyp.md)

- Use architecture-specific conditions for OpenSSL headers on Windows (ia32 vs x64) — prevents linker errors when the header layout differs between architectures [source](./.skilld/docs/Linking-to-OpenSSL.md:L27:36)

<!-- /skilld:best-practices -->
