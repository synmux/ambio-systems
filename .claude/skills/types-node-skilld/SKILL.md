---
name: types-node-skilld
description: 'TypeScript definitions for node. ALWAYS use when writing code importing "@types/node". Consult for debugging, best practices, or modifying @types/node, types/node, types node, DefinitelyTyped.'
metadata:
  version: 26.1.1
  generated_by: cached
  generated_at: 2026-07-18
---

# DefinitelyTyped/DefinitelyTyped `@types/node@26.1.1`

**Tags:** ts2.5: 12.12.6, ts2.6: 12.12.6, ts2.0: 12.12.6

**References:** [package.json](./.skilld/pkg/package.json) • [README](./.skilld/pkg/README.md) • [Issues](./.skilld/issues/_INDEX.md) • [Discussions](./.skilld/discussions/_INDEX.md) • [Releases](./.skilld/releases/_INDEX.md)

## Search

Use `skilld search "query" -p @types/node` instead of grepping `.skilld/` directories. Run `skilld search --guide -p @types/node` for full syntax, filters, and operators.

<!-- skilld:api-changes -->

## @types/node v26.1.1 API Changes

This section documents version-specific API changes for @types/node v26.1.1 — focusing on recent major/minor releases and migrations.

## API Changes

- BREAKING: TypeScript < 5.0 support dropped for FFI module — `ffi.d.ts` uses `const` type parameters (TypeScript 5.0+ syntax), causing parse-time errors with TypeScript < 5.0 even with `skipLibCheck: true` [source](./.skilld/discussions/discussion-75225.md)

- NEW: FFI module (`node:ffi`) for native function interface — enables loading dynamic libraries and calling native functions via `dlopen()`, `dlsym()`, `dlclose()`, with memory helper functions (`readUTF8String()`, `readArrayOf8BitIntegers()`, etc.) and a `suffix` constant for platform-specific shared library extensions [source](./.skilld/pkg/ffi.d.ts:L1-100)

- NEW: `crypto.randomUUIDv7()` — generates RFC 9562 version 7 UUIDs (available since Node v24.16.0); previously only `randomUUID()` (v4) was supported [source](./.skilld/pkg/crypto.d.ts:L3019)

- NEW: Test runner context query — `test.getTestContext()` function returns the active test or suite context, allowing access to test metadata from outside the callback [source](./.skilld/pkg/test.d.ts:L973)

- NEW: Test randomization — `randomize` boolean option on test runner options to randomize execution order of tests and test files (deterministic via `seed` option) [source](./.skilld/pkg/test.d.ts:L286)

- NEW: Suite introspection — `SuiteContext.passed` property (boolean), `SuiteContext.attempt` property (zero-based attempt number), and `SuiteContext.diagnostic()` method for suite diagnostics [source](./.skilld/pkg/test.d.ts:L1384-1403)

- NEW: V8 synchronous heap profiling — `v8.startHeapProfiling()` with `SyncHeapProfileHandle` interface containing `stop()` and `cancel()` methods for collecting synchronous heap profiles [source](./.skilld/pkg/v8.d.ts:L26)

**Also changed:** `ReadableStreamReadDoneResult` type compatibility with `lib.dom.d.ts` (v25 migration) · `crypto.randomUUIDV7Options` interface · FFI memory API (`readBigInt64LE`, `readBigUInt64LE`, `readPointer`, `writePointer`, etc.)
<!-- /skilld:api-changes -->

<!-- skilld:best-practices -->

## Best Practices

- Use `node:` prefix when importing Node.js modules to ensure ESM compatibility and clarity — both `import fs from 'node:fs'` and `import { open } from 'node:fs/promises'` are standard patterns [source](./.skilld/pkg/fs/promises.d.ts#L201)

- Prefer fs/promises over callback-based fs APIs for all file I/O operations — the promises-based module provides better error handling, cleaner syntax, and integrates well with async/await patterns [source](./.skilld/pkg/fs/promises.d.ts#L1188)

- Use `AbortSignal` with async operations to enable cancellation without requiring manual cleanup — pass an `AbortSignal` to functions like `readFile()` and `watch()` to support timeouts and user-initiated cancellations [source](./.skilld/pkg/fs/promises.d.ts#L1198:L1210)

- Prefer WHATWG URL API (the `URL` class) over deprecated `url.parse()` — the modern API is standard across JavaScript environments and avoids security issues related to host name spoofing and incorrect credential handling [source](./.skilld/pkg/url.d.ts#L68:L88)

- Use `stream/promises` for promise-based stream pipelines and `stream/iter` for modern iterator-based consumption — these provide composable, chainable APIs for stream transformation without callback nesting [source](./.skilld/pkg/index.d.ts#L95:L98)

- Use `dns/promises` instead of callback-based DNS operations — enables natural async/await syntax and better error propagation in DNS-heavy applications [source](./.skilld/pkg/dns/promises.d.ts#L417)

- Set `chunkSize` explicitly in file read/write operations to optimise performance for your use case — the default (131072 bytes) suits most scenarios, but adjust based on your streaming characteristics [source](./.skilld/pkg/fs/promises.d.ts#L109,L136)

- Use `EventEmitter.once()` instead of `.on()` when listening for single events — avoids manual listener cleanup and reduces memory overhead when handling one-time events [source](./.skilld/pkg/events.d.ts#L236:L256)

- Use `import.meta.url` with `new URL()` to construct file paths in ESM code — provides reliable path resolution across different execution contexts without relying on `__dirname` or `__filename` [source](./.skilld/pkg/fs/promises.d.ts#L746,L1276)

- Recognise that @types/node only supports the last two years of TypeScript versions — do not expect compatibility with TypeScript versions older than ~2 years; upgrade TypeScript or pin @types/node to an older version if this is a constraint [source](./.skilld/discussions/discussion-75225.md)

- Import ES builtin definitions from TypeScript's lib (e.g., `es2025.iterator` or `esnext.iterator` in tsconfig), not from @types/node — @types/node provides Node.js-specific APIs only; async iterator helpers and other ES features come from TypeScript's standard library [source](./.skilld/discussions/discussion-74956.md)

- Use `Abortable` mixin when creating custom resource types that support cancellation — this interface integrates with Node.js conventions for signal-based cancellation and works with existing timeout patterns [source](./.skilld/pkg/fs/promises.d.ts#L70:L77)

- Use `stream/iter` with `pipeTo()` for composition over the callback-based `.pipe()` — provides backpressure handling, error propagation, and chainable transformations without callback pyramid nesting [source](./.skilld/pkg/fs/promises.d.ts#L568:L569)

<!-- /skilld:best-practices -->
