---
name: nuxt-a11y-skilld
description: 'ALWAYS use when writing code importing "@nuxt/a11y". Consult for debugging, best practices, or modifying @nuxt/a11y, nuxt/a11y, nuxt a11y, a11y.'
metadata:
  version: 1.0.0-alpha.1
  generated_by: Anthropic · Haiku 4.5
  generated_at: 2026-05-31
---

# nuxt/a11y `@nuxt/a11y@1.0.0-alpha.1`

**Tags:** latest: 1.0.0-alpha.1, alpha: 1.0.0-alpha.1

**References:** [package.json](./.skilld/pkg/package.json) • [README](./.skilld/pkg/README.md) • [Issues](./.skilld/issues/_INDEX.md)

## Search

Use `skilld search "query" -p @nuxt/a11y` instead of grepping `.skilld/` directories. Run `skilld search --guide -p @nuxt/a11y` for full syntax, filters, and operators.

<!-- skilld:api-changes -->

## API Changes

@nuxt/a11y v1.0.0-alpha.1 is the initial alpha release of the Nuxt Accessibility module. There are no previous versions, so no deprecated, removed, or renamed APIs to document.

### Key APIs in v1.0.0-alpha.1

The module provides the following stable APIs:

- **ModuleOptions** — configure the module via `nuxt.config.ts` with `enabled`, `defaultHighlight`, `logIssues`, and `axe` configuration [source](./.skilld/pkg/dist/module.d.mts:L4:12)

- **A11yViolation** — typed interface for accessibility violations with properties: `id`, `impact`, `help`, `helpUrl`, `description`, `nodes`, `tags`, `timestamp`, and optional `route` [source](./.skilld/pkg/dist/runtime/types.d.ts:L7:17)

- **A11yWindow** — extends Window interface with testing functions: `__nuxt_a11y_run__()`, `__nuxt_a11y_enableConstantScanning__()`, `__nuxt_a11y_disableConstantScanning__()` [source](./.skilld/pkg/dist/runtime/types.d.ts:L29:33)

- **PublicRuntimeConfig** — exposes `axe`, `a11yDefaultHighlight`, and `a11yLogIssues` at runtime [source](./.skilld/pkg/dist/module.d.mts:L16:20)

### Future Changes

The following features are under consideration for future releases:

- WCAG conformance level filter (A/AA/AAA) — planned feature to allow filtering violations by compliance level [source](./.skilld/issues/issue-218.md:L18:35)

- CLI command for generating reports — proposed `nuxt a11y --output=report.md` for CI/CD integration [source](./.skilld/issues/issue-209.md:L16:20)

- Integration with @nuxt/test-utils — planned testing utilities for accessibility scanning in test suites [source](./.skilld/issues/issue-207.md:L12:18)
<!-- /skilld:api-changes -->

<!-- skilld:best-practices -->

## Best Practices for @nuxt/a11y v1.0.0-alpha.1

## Configuration Patterns

- Load `@nuxt/a11y` before `@nuxt/devtools` in your `nuxt.config.ts` modules array to ensure DevTools RPC handlers register correctly. If loaded after DevTools, the a11y tab may fail to communicate with the module [source](./.skilld/issues/issue-216.md)

- Use `axe.runOnly` to target specific WCAG compliance standards based on your legal or contractual requirements (WCAG 2.0 Level AA for ADA/Section 508, WCAG 2.1 Level AA for RGAA/EN 301 549, etc.). This prevents noise from higher-level AAA-only rules [source](./.skilld/pkg/README.md#L180:183)

```typescript
a11y: {
  axe: {
    runOptions: {
      runOnly: ['wcag2aa'], // Target AA compliance
    },
  },
}
```

- Disable console logging (`logIssues: false`) in production or CI environments to avoid cluttering logs; logging is most useful during active development [source](./.skilld/pkg/README.md#L150:160)

- Configure individual axe-core rules via `axe.options.rules` to enable, disable, or adjust specific checks—for example, relaxing `color-contrast` rules if your design system uses CSS variables that axe-core doesn't resolve correctly [source](./.skilld/pkg/README.md#L172:177)

```typescript
a11y: {
  axe: {
    options: {
      rules: {
        'color-contrast': { enabled: true },
        'image-alt': { enabled: false }, // Disable if you handle alt text differently
      },
    },
  },
}
```

## Development Workflow Patterns

- Enable `defaultHighlight: true` during active development to immediately visualize violations on the page as you navigate and modify components, reducing the friction of manual scanning [source](./.skilld/pkg/README.md#L142:147)

- Use auto-scan mode in development to catch regressions in real-time as you interact with the application. The module debounces scans to prevent performance issues from excessive rescans [source](./.skilld/pkg/README.md#L89:95)

- Click violation cards in the DevTools panel to pin and highlight all affected elements with numbered badges, then click individual elements to toggle their highlighting. Use "Scroll to element" to jump directly to violations on the page [source](./.skilld/pkg/README.md#L84:88)

## Deployment & Infrastructure

- When running your Nuxt app behind an nginx reverse proxy, ensure WebSocket upgrade headers (`Upgrade` and `Connection`) are properly forwarded to prevent infinite RPC reconnection loops. The a11y DevTools client communicates via WebSocket [source](./.skilld/issues/issue-243.md)

```nginx
location /admin {
    proxy_set_header Upgrade $http_upgrade;
    proxy_set_header Connection "upgrade";
}
```

- The module only runs in development mode by default (`enabled: true` in dev, disabled in production). Explicitly set `enabled: false` in production builds to prevent bundle overhead [source](./.skilld/pkg/README.md#L129:135)

## Scoping & Limitations

- Understand that the "no issues" result does not mean your application is fully accessible—axe-core detects automated violations, but many accessibility issues (e.g., keyboard navigation, screen reader compatibility, logical heading structure) require manual testing and user feedback [source](./.skilld/issues/issue-173.md)

- Be aware that the module prevents highlighting of `<html>` and `<body>` elements and displays a helpful notification instead. Focus highlighting and debugging on child elements within the page [source](./.skilld/pkg/README.md#L87)

## Testing & CI Integration

- Route violations are tracked separately as you navigate your application. Use this organization to prioritize fixes by page importance—critical violations on high-traffic routes should be addressed first [source](./.skilld/pkg/README.md#L30)
<!-- /skilld:best-practices -->
