---
name: types-three-skilld
description: 'ALWAYS use when writing code importing "@types/three". Consult for debugging, best practices, or modifying @types/three, types/three, types three, DefinitelyTyped.'
metadata:
  version: 0.184.1
  generated_by: Anthropic · Haiku 4.5
  generated_at: 2026-05-31
---

# DefinitelyTyped/DefinitelyTyped `@types/three@0.184.1`

**Tags:** ts2.5: 0.92.22, ts2.3: 0.92.22, ts2.7: 0.92.22

**References:** [package.json](./.skilld/pkg/package.json) • [README](./.skilld/pkg/README.md) • [Docs](./.skilld/docs/_INDEX.md) • [Issues](./.skilld/issues/_INDEX.md) • [Discussions](./.skilld/discussions/_INDEX.md) • [Releases](./.skilld/releases/_INDEX.md)

## Search

Use `skilld search "query" -p @types/three` instead of grepping `.skilld/` directories. Run `skilld search --guide -p @types/three` for full syntax, filters, and operators.

<!-- skilld:api-changes -->

## API Changes

This section documents version-specific API changes for @types/three v0.184.1, focusing on breaking changes and dependency updates that affect type definitions.

- BREAKING: `@webgpu/types` dependency removed from package.json in v0.184.0 — `GPUDevice` and `GPUCanvasContext` are now empty stub interfaces in `WebGPUBackend.d.ts`. Users requiring proper WebGPU types must install `@webgpu/types` manually. This resolves conflicts with TypeScript 6's built-in WebGPU types [source](./.skilld/discussions/discussion-74856.md#top-comments)

- FIXED: `Scene<TEventMap>` generic parameter — In v0.183.1, the module augmentation in `NodeManager.d.ts` caused VSCode to resolve to a non-generic `Scene` interface instead of the generic class declaration, breaking code like `scene: THREE.Scene<THREE.Object3DEventMap>`. Fixed in v0.184.0 to properly preserve generic type parameters [source](./.skilld/discussions/discussion-74599.md)

**Also changed:** SpotLightNode module augmentation issues in r177+ related to three.js versions (not a type definition change)

<!-- /skilld:api-changes -->

<!-- skilld:best-practices -->

## @types/three v0.184.1 Best Practices

## Best Practices

- Parametrize event listeners with EventDispatcher's generic event map types for compile-time event validation — use `EventDispatcher<TEventMap>` where TEventMap defines valid event types like `{ added: {}; removed: {} }` to enable type-safe `addEventListener()` and prevent misspelled event names [source](./.skilld/pkg/src/core/EventDispatcher.d.ts:L41-L82)

- Scene has a generic event map parameter despite simple appearance — annotate with `Scene<TEventMap>` when dispatching custom events or handling event maps, not plain `Scene` [source](./.skilld/pkg/src/scenes/Scene.d.ts:L28)

- Always explicitly type Texture when storing image sources — use `Texture<HTMLImageElement>` for DOM images or `Texture<HTMLCanvasElement>` for canvas sources to enable proper memory management and disposal patterns [source](./.skilld/pkg/src/textures/Texture.d.ts:L109)

- Use `loadAsync()` instead of `.load()` callbacks when you need Promise-based async handling — loaders provide both callback-based `.load(url, onLoad?, onProgress?, onError?)` and Promise-based `.loadAsync(url, onProgress?)` patterns [source](./.skilld/pkg/src/loaders/Loader.d.ts:L35-L41)

- Use Loader's two-parameter generics for type-safe loading — `Loader<TData, TUrl>` allows constraining both the return type (TData, default `unknown`) and URL type (TUrl, default `string`) for custom loader implementations [source](./.skilld/pkg/src/loaders/Loader.d.ts:L6)

- Chain loader configuration methods for readable setup — Loader provides fluent API methods like `setPath()`, `setCrossOrigin()`, `setResourcePath()` that return `this` for chainable configuration [source](./.skilld/pkg/src/loaders/Loader.d.ts:L43-L48)

- Declare buffer data using the TypedArray union type — use the `TypedArray` union exported from BufferAttribute (Int8Array through Float64Array) as the standard type for typed array data to ensure GPU compatibility [source](./.skilld/pkg/src/core/BufferAttribute.d.ts:L6-L15)

- Extract event type keys with `Extract<keyof TEventMap, string>` in generic addEventListener implementations — this pattern in EventDispatcher ensures type-safe event listeners with proper event data inference [source](./.skilld/pkg/src/core/EventDispatcher.d.ts:L52-L55)

- Extend Object3D with preserved event maps through the hierarchy — when subclassing Object3D, pass the generic type parameter forward like `class Group<TEventMap extends Object3DEventMap> extends Object3D<TEventMap>` to maintain type safety across inheritance chains [source](./.skilld/pkg/src/objects/Group.d.ts:L25)

- Use readonly type guard properties for safe type discrimination — prefer the `readonly isScene: true` pattern over string type checks when testing instance types, as the readonly boolean literal provides compile-time narrowing [source](./.skilld/pkg/src/scenes/Scene.d.ts:L28-L34)

- Define separate JSON serialization interfaces for round-trip data safety — use dedicated `*JSON` interface types like `TextureJSON` or `SceneJSON` for parsing/serialization to match the three.js file format and avoid mixing runtime and persisted representations [source](./.skilld/pkg/src/textures/Texture.d.ts:L47-L81)

- Pass LoadingManager to loaders for coordinated resource loading and cross-origin handling — Loader accepts an optional LoadingManager parameter in the constructor to manage request headers, cross-origin policy, and progress tracking across multiple loader instances [source](./.skilld/pkg/src/loaders/Loader.d.ts:L7)

- Use NormalBufferAttributes or NormalOrGLBufferAttributes type aliases for geometry attribute maps — BufferGeometry defines these aliases to properly type attribute maps that may contain BufferAttribute, InterleavedBufferAttribute, or GLBufferAttribute instances [source](./.skilld/pkg/src/core/BufferGeometry.d.ts:L13-L17)

- Install @webgpu/types separately if using WebGPU rendering on TypeScript <6 — @types/three 0.184.0+ removed the @webgpu/types dependency to avoid conflicts with TypeScript 6's native WebGPU types; manually install @webgpu/types for older TypeScript versions when using WebGPURe nderer [source](./.skilld/discussions/discussion-74856.md)

<!-- /skilld:best-practices -->
