---
name: node-gyp-skilld
description: 'ALWAYS use when writing code importing "node-gyp". Consult for debugging, best practices, or modifying node-gyp, node gyp.'
metadata:
  version: 13.0.0
  generated_by: Anthropic · Haiku 4.5
  generated_at: 2026-06-29
---

# nodejs/node-gyp `node-gyp@13.0.0`

**Tags:** latest: 13.0.0

**References:** [package.json](./.skilld/pkg/package.json) • [README](./.skilld/pkg/README.md) • [Docs](./.skilld/docs/_INDEX.md) • [Issues](./.skilld/issues/_INDEX.md) • [Releases](./.skilld/releases/_INDEX.md)

## Search

Use `skilld search "query" -p node-gyp` instead of grepping `.skilld/` directories. Run `skilld search --guide -p node-gyp` for full syntax, filters, and operators.

<!-- skilld:api-changes -->

## node-gyp API Changes

## API Changes

This section documents version-specific API changes — prioritise recent major/minor releases.

- BREAKING: Node engine range changed to `^22.22.2 || ^24.15.0 || >=26.0.0` in v13.0.0 — drops support for Node 16, 18, and 20 [source](./.skilld/releases/v13.0.0.md:L14)

- BREAKING: Built-in `fetch` API replaces `make-fetch-happen` dependency as of v12.3.0 — internal HTTP handling now uses standard Node.js fetch [source](./.skilld/pkg/CHANGELOG.md#1226)

- BREAKING: URL constructor preferred over `url.resolve()` and `url.parse()` — v12.3.0 switched to `new URL()` for URL handling [source](./.skilld/pkg/CHANGELOG.md:L64)

- BREAKING: Gyp class now uses ECMAScript class syntax (v10.0.0) — previously created with `util.inherits`, may have subtle differences in inheritance chain [source](./.skilld/releases/v10.0.0.md:L15)

- BREAKING: All internal functions return promises, no longer accept callbacks (v10.0.0) — affects direct consumers of internal APIs, not CLI users [source](./.skilld/releases/v10.0.0.md:L16)

- BREAKING: `rimraf` dependency removed (v10.0.0) — node-gyp no longer uses rimraf, uses native Node.js `fs.rm()` with recursive option [source](./.skilld/releases/v10.0.0.md:L24)

- BREAKING: `npmlog` replaced with `proc-log` (v10.0.0) — logging API changed if using node-gyp as a library [source](./.skilld/releases/v10.0.0.md:L26)

- BREAKING: Python 2 support fully removed (v8.0.0) — Python 3.6+ required; Python search order changed to prioritise `python` after `python3` [source](./.skilld/pkg/CHANGELOG.md:L785)

- BREAKING: Minimum Python version raised from 2.6 to 2.7 (v6.0.0) — earlier versions of node-gyp required older Python; v6+ needs 2.7 minimum [source](./.skilld/pkg/CHANGELOG.md:L894)

**Also changed:** Node engine range v12.0.0 aligned to npm 11 · `mkdirp` replaced with native `{recursive: true}` mkdir (v7.0.0) · Visual Studio 2026 support added (v12.1.0) · OpenHarmony platform support (v11.4.2) · Configuration reading from `package.json` (v11.4.0)

<!-- /skilld:api-changes -->

<!-- skilld:best-practices -->

## Best Practices

- Use only stable, released Node.js versions (not pre-release versions with `-pre` suffix) — pre-release versions prevent node-gyp from downloading headers automatically; instead configure the `--nodedir` flag [source](./.skilld/docs/Error-pre-versions-of-node-cannot-be-installed.md#how-to-avoid-the-short-answer)

- Verify that your npm's bundled node-gyp is current by checking the `gyp info using node-gyp@` string in error logs; if the version is less than the current release, update it using platform-specific instructions [source](./.skilld/docs/README.md)

- Configure Python explicitly when multiple versions are installed — set `npm_config_python` environment variable, use the `--python` command-line flag, or configure `npm config set python` to point to the correct Python executable [source](./.skilld/pkg/README.md:L70:L101)

- When building for third-party Node.js runtimes (Electron, etc.), always pass `--dist-url` or `--nodedir` flags to target the correct runtime headers instead of relying on the running Node.js instance [source](./.skilld/pkg/README.md:L103:L117)

- Use `--force-process-config` when building for older Electron versions that shipped with malformed `config.gypi` files in their headers distribution [source](./.skilld/pkg/README.md:L115:L117)

- Handle OpenSSL linking conditionally in binding.gyp by checking the `node_shared_openssl` variable — include bundled OpenSSL headers when false, system headers when true — this ensures compatibility across Node.js versions [source](./.skilld/docs/Linking-to-OpenSSL.md#windowsquestion)

- Structure binding.gyp with `variables`, `conditions`, `target_defaults`, and `targets` sections at the top level — use `conditions` to handle platform-specific settings like Windows OpenSSL paths [source](./.skilld/pkg/gyp/docs/UserDocumentation.md:L18:L100)

- Set up variables in binding.gyp (with `%` suffix for defaults) to make configurations referenceable across conditions and targets without code duplication [source](./.skilld/pkg/gyp/docs/InputFormatReference.md:L1:L80)

- Avoid using deprecated packages in native addon projects — `node-sass` is unmaintained; use the maintained `sass` package instead for Sass compilation [source](./.skilld/pkg/README.md#node-sass-is-deprecated)

- Disable LTO (Link Time Optimization) manually on Windows addon builds if required — node-gyp v13.0.0+ disables it by default to prevent build failures [source](./.skilld/releases/v13.0.0.md)

- Check that your Node.js version meets node-gyp v13.0.0's minimum requirement of `^22.22.2 || ^24.15.0 || >=26.0.0` before attempting builds; older versions are not supported [source](./.skilld/releases/v13.0.0.md)

- When npm bundles an outdated node-gyp (npm 8 and older), use `npm explore` to update it in place — this prevents repeated failures during native addon installation [source](./.skilld/docs/Updating-npm-bundled-node-gyp.md#linux-macos-solaris-etc)

- Use `npm config set node_gyp` (npm 6 or older) to point npm to a global node-gyp installation for consistent versioning — this avoids npm's internal outdated copy overriding your updates [source](./.skilld/docs/Force-npm-to-use-global-node-gyp.md#linux-and-macos)

- Be aware that `ffi-napi` is no longer maintained and has proven problematic on modern systems — consider alternatives like `koffi` or `node-ffi-rs` for FFI functionality [source](./.skilld/pkg/README.md#ffi-napi-is-no-longer-maintained)
<!-- /skilld:best-practices -->
