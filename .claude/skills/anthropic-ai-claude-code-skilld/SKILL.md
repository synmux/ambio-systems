---
name: anthropic-ai-claude-code-skilld
description: 'ALWAYS use when writing code importing "@anthropic-ai/claude-code". Consult for debugging, best practices, or modifying @anthropic-ai/claude-code, anthropic-ai/claude-code, anthropic-ai claude-code, anthropic ai claude code, claude-code-2.1.88, claude code 2.1.88.'
metadata:
  version: 2.1.159
  generated_by: Anthropic · Haiku 4.5
  generated_at: 2026-05-31
---

# Exhen/claude-code-2.1.88 `@anthropic-ai/claude-code@2.1.159`

**Tags:** stable: 2.1.150, latest: 2.1.159, next: 2.1.159

**References:** [package.json](./.skilld/pkg/package.json) • [README](./.skilld/pkg/README.md)

## Search

Use `skilld search "query" -p @anthropic-ai/claude-code` instead of grepping `.skilld/` directories. Run `skilld search --guide -p @anthropic-ai/claude-code` for full syntax, filters, and operators.

<!-- skilld:api-changes -->

## API Changes

This section documents version-specific API changes — prioritize recent major/minor releases.

- DEPRECATED: `shell_id` in `TaskStopInput` — old parameter is deprecated, use `task_id` instead [source](./.skilld/pkg/sdk-tools.d.ts:L527)

- NEW: `AskUserQuestionInput` — structured API for asking users multiple-choice questions with descriptions and previews [source](./.skilld/pkg/sdk-tools.d.ts:L608)

- NEW: `BashInput` `timeout` parameter — specify command execution timeout in milliseconds (max 600000) [source](./.skilld/pkg/sdk-tools.d.ts:L349)

- NEW: `BashInput` `run_in_background` parameter — execute commands asynchronously without blocking [source](./.skilld/pkg/sdk-tools.d.ts:L369)

- NEW: `FileEditOutput` `structuredPatch` field — structured diff information showing exact line changes [source](./.skilld/pkg/sdk-tools.d.ts:L2539)

- NEW: `FileWriteOutput` `structuredPatch` field — structured diff information for file writes with line positions [source](./.skilld/pkg/sdk-tools.d.ts:L2583)

- NEW: `BashOutput` git operation tracking — structured `gitOperation` field detects and reports git/gh commands (commits, pushes, branches, PRs) [source](./.skilld/pkg/sdk-tools.d.ts:L2464)

**Also changed:** `TaskUpdateInput` metadata · `FileEditOutput` userModified flag · `BashOutput` structured content blocks · `EnterWorktreeInput` path parameter

<!-- /skilld:api-changes -->

<!-- skilld:best-practices -->

## Best Practices

- Always define workflow `meta` as a pure object literal with no computed values — the harness parses it statically, and dynamic values will be undefined in metadata. Use `name`, `description`, and `phases` fields only. [source](./.skilld/pkg/sdk-tools.d.ts:L2269)

- Pass workflow `args` as actual JSON values, not JSON-encoded strings — a stringified array or object breaks `.filter()` and `.map()` because args receives it as a single string rather than a parsed array. [source](./.skilld/pkg/sdk-tools.d.ts:L2285)

- Use `CronCreateInput` with `recurring: false` for one-shot reminders — set a pinned minute/hour/day-of-month to fire exactly once at the target time, then auto-delete. Omit this for recurring schedules. [source](./.skilld/pkg/sdk-tools.d.ts:L2309)

- Avoid scheduling at :00 and :30 minute marks in `CronCreateInput` — all users scheduling at those marks causes thundering herd on the service. Pick :07, :23, :37, etc. to distribute load evenly. [source](./.skilld/pkg/sdk-tools.d.ts:L2299)

- Check for all terminal states in `MonitorInput` filters, not just success markers — a monitor that greps only for the success pattern stays silent on crash or hang. Widen the filter to include error/failure signatures (Traceback, Error, FAILED, Killed). [source](./.skilld/pkg/sdk-tools.d.ts:L2365)

- Use `AgentInput` `isolation: "worktree"` when spawning multiple agents that mutate files in parallel — prevents conflicts and ensures clean, isolated changes, though it adds ~200-500ms setup cost per agent. [source](./.skilld/pkg/sdk-tools.d.ts:L2339)

- Structure `BashInput` descriptions by command complexity — for simple CLI tools (git, npm, ls), use 5-10 words; for piped or obscure-flag commands, provide enough context to clarify the operation. Avoid words like "complex" or "risk". [source](./.skilld/pkg/sdk-tools.d.ts:L2353)

- Prefer `GrepInput` `type` parameter over `glob` for standard file types — using `type: "js"` is more efficient than `glob: "*.js"` because the former uses ripgrep's internal type definitions. [source](./.skilld/pkg/sdk-tools.d.ts:L2507)

- Use `GrepInput` `head_limit: 0` sparingly for unbounded results — defaults to 250, which is a sensible limit; 0 disables it and wastes context on large result sets. Only use 0 when you genuinely need all matches. [source](./.skilld/pkg/sdk-tools.d.ts:L2511)

- Apply `grep --line-buffered` in `MonitorInput` pipes — without it, buffering delays event delivery by minutes. Always use when piping grep in monitor commands that emit events. [source](./.skilld/pkg/sdk-tools.d.ts:L2365)

- Stop prior workflow in `WorkflowInput` with `resumeFromRunId` before resuming — call `TaskStop` on the prior run first; resuming without stopping causes state conflicts. [source](./.skilld/pkg/sdk-tools.d.ts:L2295)

- Set `CronCreateInput` `durable: true` only when explicitly requested across sessions — defaults to `false` (in-memory), which is correct for session-scoped reminders. Durability persists to `.claude/scheduled_tasks.json` and survives restarts. [source](./.skilld/pkg/sdk-tools.d.ts:L2313)

- Structure `ExitPlanModeInput` `allowedPrompts` with semantic action descriptions — use "run tests", "install dependencies", not specific commands, so the harness can match similar operations without explicit enumeration. [source](./.skilld/pkg/sdk-tools.d.ts:L2399)
<!-- /skilld:best-practices -->
