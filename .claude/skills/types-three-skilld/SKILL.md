---
name: types-three-skilld
description: 'ALWAYS use when writing code importing "@types/three". Consult for debugging, best practices, or modifying @types/three, types/three, types three, DefinitelyTyped.'
metadata:
  version: 0.185.1
  generated_by: Anthropic · Haiku 4.5
  generated_at: 2026-07-18
---

# DefinitelyTyped/DefinitelyTyped `@types/three@0.185.1`

**Tags:** ts2.0: 0.92.22, ts2.1: 0.92.22, ts2.2: 0.92.22

**References:** [package.json](./.skilld/pkg/package.json) • [README](./.skilld/pkg/README.md) • [Docs](./.skilld/docs/_INDEX.md) • [Issues](./.skilld/issues/_INDEX.md) • [Discussions](./.skilld/discussions/_INDEX.md) • [Releases](./.skilld/releases/_INDEX.md)

## Search

Use `skilld search "query" -p @types/three` instead of grepping `.skilld/` directories. Run `skilld search --guide -p @types/three` for full syntax, filters, and operators.

<!-- skilld:api-changes -->

## API Changes

This section documents version-specific API changes in @types/three v0.185.1 — focusing on breaking changes, deprecations, and new APIs from recent releases.

BREAKING: `Clock` class deprecated since r185 — Use `Timer` class instead, which provides better API design with `.update()` method preventing multiple calls to `getDelta()`/`getElapsed()` returning different values within a frame [source](./.skilld/src/core/Clock.d.ts:L1:10)

BREAKING: `PostProcessing` renamed to `RenderPipeline` since r183 — the old name still works as deprecated alias but new code should import `RenderPipeline` directly [source](./.skilld/src/renderers/common/PostProcessing.d.ts:L1:5)

BREAKING: `outputBufferType` property/method deprecated since r182 — Use `getOutputBufferType()` instead, returns `TextureDataType` [source](./.skilld/src/renderers/common/Renderer.d.ts:L1:10)

BREAKING: `renderAsync()` deprecated on Renderer and QuadMesh — Use synchronous `render()` method paired with `await renderer.init()` when creating the renderer for WebGPU initialization pattern [source](./.skilld/src/renderers/common/QuadMesh.d.ts:L1:5)

BREAKING: Async PMREM methods `fromSceneAsync()`, `fromEquirectangularAsync()`, `fromCubemapAsync()` deprecated — Migrate to synchronous variants (`fromScene()`, `fromEquirectangular()`, `fromCubemap()`) and use `await renderer.init()` instead for GPU resource initialization [source](./.skilld/src/renderers/common/extras/PMREMGenerator.d.ts:L1:20)

DEPRECATED: Multiple async-only Renderer methods (`clearAsync()`, `clearColorAsync()`, `clearDepthAsync()`, `clearStencilAsync()`) — These async-only variants no longer needed with the new `renderer.init()` + synchronous `render()` pattern [source](./.skilld/src/renderers/common/Renderer.d.ts:L1:50)

DEPRECATED: `Line2NodeMaterial.lineColorNode` property since r185 — Use `NodeMaterial.colorNode` instead for consistent colour node handling across all node materials [source](./.skilld/src/materials/nodes/Line2NodeMaterial.d.ts:L1:10)

NEW: `Timer` class — Replaces `Clock` with improved semantics; call `.update()` once per frame to avoid stale delta values when `getDelta()`/`getElapsed()` called multiple times, includes Page Visibility API support via `.connect(document)` [source](./.skilld/src/core/Timer.d.ts:L1:40)

NEW: `Renderer.init()` method — Async initialization for WebGPU renderer; returns `Promise<this>` and must be awaited before rendering on WebGPU backend [source](./.skilld/src/renderers/common/Renderer.d.ts:L1:3)

NEW: `RenderPipeline` class — Replaces `PostProcessing` in WebGPU rendering pipeline; provides unified interface for render target and post-processing setup [source](./.skilld/src/renderers/common/RenderPipeline.d.ts:L1:5)

NEW: `getOutputBufferType()` method on Renderer — Returns the texture data type used for output buffers; replaces the deprecated `outputBufferType` getter [source](./.skilld/src/renderers/common/Renderer.d.ts:L1:3)

NEW: Node-based loader classes for TypeScript support — `NodeLoader`, `NodeMaterialLoader`, `NodeObjectLoader` provide typed loading of node-based materials and scenes [source](./.skilld/src/loaders/nodes/NodeLoader.d.ts:L1:5)

NEW: `ClippingGroup` class — New group type for managing clipping plane hierarchies in WebGPU renderer [source](./.skilld/src/objects/ClippingGroup.d.ts:L1:3)

NEW: WebGPU-specific lighting classes — `IESSpotLight` and `ProjectorLight` extend lighting capabilities for WebGPU renderer with photometric and projection-based lighting [source](./.skilld/src/Three.WebGPU.d.ts:L1:30)

NEW: WebGPU rendering utilities — `BlendMode`, `CanvasTarget`, `CubeRenderTarget`, `IndirectStorageBufferAttribute`, `InspectorBase` provide low-level control and inspection of WebGPU rendering state [source](./.skilld/src/Three.WebGPU.d.ts:L1:35)

**Also changed:** `renderAsync()` on RenderPipeline · `supportsFeature()` async variant · Page Visibility API support in Timer · Node material colour property consolidation · WebGPU backend async initialization workflow
<!-- /skilld:api-changes -->

<!-- skilld:best-practices -->

## Best Practices

- Always call `.dispose()` on geometries, materials, and textures when they're no longer needed to free GPU memory and prevent memory leaks — three.js objects hold WebGL resources that won't be automatically garbage collected [source](./.skilld/pkg/src/core/Object3D.d.ts:L90)

- Use `Scene<TEventMap>` generic parameter when creating scenes to enable type-safe event listening, extending `Object3DEventMap` for custom events [source](./.skilld/pkg/src/scenes/Scene.d.ts:L25)

- Prefer `Group` for hierarchical object grouping instead of bare `Object3D` — the documentation explicitly recommends this pattern for scene organisation [source](./.skilld/pkg/src/core/Object3D.d.ts:L95)

- Use `Object3D<TEventMap extends Object3DEventMap>` generic parameter to type-safely handle events emitted by objects via the `EventDispatcher` pattern [source](./.skilld/pkg/src/core/EventDispatcher.d.ts:L35)

- Set `Material.side = THREE.DoubleSide` when raycasting needs to detect intersections on back-facing triangles — by default only front-facing geometry is detectable [source](./.skilld/pkg/src/core/Raycaster.d.ts:L102)

- Normalise mouse coordinates to NDC (normalised device coordinates) between -1 and 1 before passing to `raycaster.setFromCamera()` — the coordinate system expects X/Y in range [-1, 1] [source](./.skilld/pkg/src/core/Raycaster.d.ts:L81)

- Use `Layers` API to selectively control visibility and raycaster interaction — more efficient than iterating objects manually: `object.layers.enable(layerNumber)` and `raycaster.layers.set(layerNumber)` [source](./.skilld/pkg/src/core/Raycaster.d.ts:L115)

- Configure `WebGLRenderer` with appropriate `outputColorSpace` (usually `SRGBColorSpace`) to match CSS/image colour spaces — mismatched colour spaces cause visual artefacts [source](./.skilld/pkg/src/renderers/WebGLRenderer.d.ts:L161)

- Apply `toneMapping` on `WebGLRenderer` for HDR-like effects in physical materials — `THREE.ACESFilmicToneMapping` is recommended for production quality [source](./.skilld/pkg/src/renderers/WebGLRenderer.d.ts:L163)

- Use `BufferGeometry<Attributes, TEventMap>` generics to type-safely extend attribute handling and enable event typing on geometry instances [source](./.skilld/pkg/src/core/BufferGeometry.d.ts:L31)

- Split meshes with multiple materials into geometry groups using `.addGroup()` rather than creating separate mesh objects — reduces draw calls and GPU overhead [source](./.skilld/pkg/src/core/BufferGeometry.d.ts:L76)

- Call `renderer.setSize()` in response to window resize events to match CSS and canvas resolution — skipping this causes blurry rendering or stretched content [source](./.skilld/pkg/src/renderers/WebGLRenderer.d.ts:L204)

- Set `BufferGeometry.morphTargetsRelative = true` when using morph targets as relative offsets rather than absolute positions — determines animation interpolation semantics [source](./.skilld/pkg/src/core/BufferGeometry.d.ts:L67)

- Leverage `Texture<TImage, TEventMap>` generics to type image data and events — enables stronger type checking when passing typed arrays or canvas elements [source](./.skilld/pkg/src/textures/Texture.d.ts:L80)

<!-- /skilld:best-practices -->
