---
name: wrangler-skilld
description: 'Command-line interface for all things Cloudflare Workers. ALWAYS use when writing code importing "wrangler". Consult for debugging, best practices, or modifying wrangler, workers-sdk, workers sdk.'
metadata:
  version: 4.112.0
  generated_by: cached
  generated_at: 2026-07-18
---

# cloudflare/workers-sdk `wrangler@4.112.0`

**Tags:** wrangler@2.2.4: 2.2.4, legacy: 3.114.17, latest: 4.112.0

**References:** [package.json](./.skilld/pkg/package.json) • [README](./.skilld/pkg/README.md) • [Docs](./.skilld/docs/_INDEX.md) • [Issues](./.skilld/issues/_INDEX.md) • [Discussions](./.skilld/discussions/_INDEX.md) • [Releases](./.skilld/releases/_INDEX.md)

## Search

Use `skilld search "query" -p wrangler` instead of grepping `.skilld/` directories. Run `skilld search --guide -p wrangler` for full syntax, filters, and operators.

<!-- skilld:api-changes -->

## API Changes

This section documents version-specific API changes in wrangler v4.x, prioritising recent major/minor releases.

- BREAKING: `legacy_env` configuration field removed in v4.111 — service environments are no longer supported; Wrangler now always deploys each environment as its own Worker named `<name>-<environment>`. Remove `legacy_env` from your config file. The `--legacy-env` CLI flag was also removed. [source](./.skilld/releases/wrangler@4.111.0.md:L20:24)

- BREAKING: `--experimental-vm-modules` CLI flag removed in v4.107 — a stale Node.js flag that caused unexpected behaviour on Node.js v26 has been removed. This was a deprecated internal flag with no user-facing API. [source](./.skilld/releases/wrangler@4.107.0.md:L115:121)

- NEW: `exports` map for declarative Durable Object lifecycle in v4.107 — replaces the legacy `migrations` array. Declare provisioning, deletion, renaming, and transfer of Durable Objects in `wrangler.json`. Supports `state` field (`"created"`, `"deleted"`, `"renamed"`, `"transferred"`, `"expecting-transfer"`) with corresponding metadata fields (`renamed_to`, `transferred_to`, `transfer_from`). Works with `wrangler deploy`, `wrangler versions upload`, `wrangler dev`, and `@cloudflare/vitest-pool-workers`. [source](./.skilld/releases/wrangler@4.107.0.md:L34:83)

- NEW: `addresses` field in wrangler configuration for Email Routing in v4.112 — declare inbound email addresses handled by your Worker directly in `wrangler.json` as an array of email addresses or wildcard patterns. [source](./.skilld/releases/wrangler@4.112.0.md:L11:22)

- NEW: Durable Object introspection in test harness via `worker.getDurableObjectStorage()` in v4.112 — retrieve storage handle to execute SQL against SQLite-backed Durable Objects for seeding and assertions. Signature: `worker.getDurableObjectStorage(binding, { name })` returns storage handle with `exec()` method. [source](./.skilld/releases/wrangler@4.112.0.md:L24:46)

- NEW: `runtimeError` event on `unstable_startWorker` DevEnv in v4.112 — emits `RuntimeErrorEvent` carrying exception text and source-mapped stack for uncaught Worker exceptions. Replaces console scraping for programmatic consumers of the DevEnv API. [source](./.skilld/releases/wrangler@4.112.0.md:L48:50)

- NEW: Containers support in `createTestHarness()` in v4.112 — Workers configured with containers can now be tested. The harness builds configured images and makes container-backed Durable Objects available during integration tests. [source](./.skilld/releases/wrangler@4.112.0.md:L63:65)

- NEW: `dev.types.includeRuntime` option in v4.111 — control whether runtime types are appended to `worker-configuration.d.ts` when running `wrangler dev --x-new-config`. Defaults to `true` for new config projects. [source](./.skilld/releases/wrangler@4.111.0.md:L26:30)

- NEW: `worker.evictDurableObject()` method in test harness in v4.111 — gracefully evict a running Durable Object by class name or binding name to verify recovery behaviour. Signature: `await worker.evictDurableObject("ClassName", { name })` [source](./.skilld/releases/wrangler@4.111.0.md:L11:18)

- NEW: `worker.listDurableObjectIds()` in test harness in v4.109 — list persisted Durable Object instance IDs for a binding, enabling integration tests to discover objects created by app behaviour without test-only endpoints. [source](./.skilld/releases/wrangler@4.109.0.md:L11:13)

- NEW: `WorkflowInstance.terminate({ rollback: true })` option in v4.109 — run registered rollback handlers before marking a Workflow instance as terminated. Also available via `wrangler workflows instances terminate --rollback` in local mode. [source](./.skilld/releases/wrangler@4.109.0.md:L15:19)

- NEW: Cache options for WorkerEntrypoint exports in v4.107 — per-entrypoint cache configuration and global `cross_version_cache` setting. Declare in `wrangler.json` under `cache` and `exports[name].cache`. [source](./.skilld/releases/wrangler@4.107.0.md:L11:32)

- NEW: Auth profiles for managing multiple OAuth logins in v4.106 — `wrangler auth create`, `activate`, `deactivate`, `list`, `delete` commands + `--profile` global flag to bind profiles to directories. [source](./.skilld/releases/wrangler@4.106.0.md:L33:55)

- NEW: `worker.applyD1Migrations()` in test harness in v4.106 — apply local D1 migrations before running requests. Signature: `await worker.applyD1Migrations("DATABASE_BINDING")`. [source](./.skilld/releases/wrangler@4.106.0.md:L67:77)

- NEW: `worker.introspectWorkflow()` in test harness in v4.106 — introspect Workflow bindings to disable sleeps, mock step results, and wait for outcomes. Signature: `await worker.introspectWorkflow("BINDING_NAME")` returns interface with `modifyAll()` and `get()` methods. [source](./.skilld/releases/wrangler@4.106.0.md:L79:98)

- NEW: `bindingOverrides` and `getExport()` in test harness in v4.106 — replace configured bindings with Workers in the same harness, and call JSRPC methods on Worker exports. Enables mocking platform bindings while keeping source config production-like. [source](./.skilld/releases/wrangler@4.106.0.md:L100:125)

- NEW: Workflow step dynamic retry delays in v4.110 — `step.do()` `retries.delay` can now be a function `({ ctx, error }) => milliseconds` instead of a static duration. Function is invoked once per failed attempt with a 5-second timeout. [source](./.skilld/releases/wrangler@4.110.0.md:L27:47)

- NEW: `dependencies_instrumentation.enabled` config field in v4.110 — opt out of dependency metadata collection at deploy time via `{ "dependencies_instrumentation": { "enabled": false } }` in wrangler.json. [source](./.skilld/releases/wrangler@4.110.0.md:L11:25)

**Also changed:** `wrangler turnstile widget` commands for managing widgets (create/list/get/update/delete) · `--source-jurisdiction` flag for AI Search R2-backed instances · `wrangler ai-search jobs` commands (list/create/get/cancel/logs) · `wrangler flagship apps` and `wrangler flagship flags` commands · `--strict` flag for `wrangler versions upload` · OAuth keychain storage via `wrangler login --use-keyring` · Pages-to-Workers delegation for static projects · Google Artifact Registry support in `containers registries configure` · `wrangler tail` resilience improvements (auto-reconnect, clean Ctrl-C shutdown)
<!-- /skilld:api-changes -->

<!-- skilld:best-practices -->

## Best Practices

- Keep `compatibility_date` current and update it regularly on existing projects — each date unlocks new runtime features, bug fixes, and APIs without requiring code changes [source](./.skilld/docs/workers/best-practices/workers-best-practices.md#keep-your-compatibility-date-current)

- Generate binding types with `wrangler types` instead of hand-writing the `Env` interface — this catches config-to-code drift at compile time by auto-syncing types to your actual bindings [source](./.skilld/docs/workers/best-practices/workers-best-practices.md#generate-binding-types-with-wrangler-types)

- Enable the `nodejs_compat` compatibility flag to access Node.js built-in modules (`node:crypto`, `node:buffer`, `node:stream`) — many libraries depend on these modules and the flag avoids cryptic runtime import errors [source](./.skilld/docs/workers/best-practices/workers-best-practices.md#enable-nodejs_compat)

- Store secrets with `wrangler secret put` and non-secret configuration as `vars` in `wrangler.jsonc` — never commit secrets or API keys to source control; use `.env` files (in `.gitignore`) for local development [source](./.skilld/docs/workers/best-practices/workers-best-practices.md#store-secrets-with-wrangler-secret-not-in-source)

- Configure each environment deliberately with its own bindings and vars — environments do not inherit settings and are deployed as distinct Workers named `{name}-{env}` (e.g., `my-api-production` and `my-api-staging`) [source](./.skilld/docs/workers/best-practices/workers-best-practices.md#configure-environments-deliberately)

- Stream large request and response bodies using `response.body` instead of `await response.text()` — buffering into memory with a 128 MB Worker limit causes crashes on large payloads; use `TransformStream` to pipe multiple responses without holding them in memory [source](./.skilld/docs/workers/best-practices/workers-best-practices.md#stream-request-and-response-bodies)

- Use `ctx.waitUntil()` for work that runs after the response (logging, cache writes, webhooks) rather than blocking on it — this keeps responses fast while still completing background tasks within the 30-second limit [source](./.skilld/docs/workers/best-practices/workers-best-practices.md#use-waituntil-for-work-after-the-response)

- Use bindings (KV, R2, D1, Queues) instead of calling the Cloudflare REST API from Workers — bindings are in-process, require no network hop or authentication, and eliminate extra latency [source](./.skilld/docs/workers/best-practices/workers-best-practices.md#use-bindings-for-cloudflare-services-not-rest-apis)

- Use Hyperdrive when connecting to remote PostgreSQL or MySQL databases — it maintains a regional connection pool and eliminates the per-request cost of TCP handshake, TLS negotiation, and connection setup [source](./.skilld/docs/workers/best-practices/workers-best-practices.md#use-hyperdrive-for-external-database-connections)

- Enable Workers Logs and Traces in production before you deploy — use `console.log` with structured JSON, `console.error` for errors, and `console.warn` for warnings so logs are searchable and filterable in the dashboard [source](./.skilld/docs/workers/best-practices/workers-best-practices.md#enable-workers-logs-and-traces)

- Run tests inside the Workers runtime with `@cloudflare/vitest-pool-workers` instead of Node.js — this gives you real bindings (KV, R2, D1, Durable Objects) and catches unsupported APIs before deploy time [source](./.skilld/docs/workers/best-practices/workers-best-practices.md#test-with-cloudflarevitest-pool-workers)

- Use `createTestHarness()` for integration testing with multiple Workers and Durable Objects — it loads your `wrangler.jsonc` config, seeds storage with SQL queries via `storage.exec()`, and supports container-backed Durable Objects [source](./.skilld/releases/wrangler@4.112.0.md) and [source](./.skilld/releases/wrangler@4.111.0.md)

- Declare Email Routing addresses in `wrangler.jsonc` with an `addresses` field instead of managing them separately — this keeps email configuration alongside your Worker code and ensures consistency across environments [source](./.skilld/releases/wrangler@4.112.0.md)

- Choose Wrangler for backend-focused development (APIs, serverless, background tasks) and the Cloudflare Vite plugin for frontend-centric projects (React, Vue, SvelteKit, React Router v8) — Wrangler enables `--remote` development on Cloudflare's network, while Vite provides Hot Module Replacement and advanced optimisations [source](./.skilld/docs/workers/local-development/wrangler-vs-vite.md)

<!-- /skilld:best-practices -->
