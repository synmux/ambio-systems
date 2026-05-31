---
name: three-skilld
description: 'ALWAYS use when writing code importing "three". Consult for debugging, best practices, or modifying three, three.js.'
metadata:
  version: 0.184.0
  generated_by: Anthropic · Haiku 4.5
  generated_at: 2026-05-31
---

# mrdoob/three.js `three@0.184.0`

**Tags:** latest: 0.184.0

**References:** [package.json](./.skilld/pkg/package.json) • [README](./.skilld/pkg/README.md) • [Docs](./.skilld/docs/_INDEX.md) • [Issues](./.skilld/issues/_INDEX.md)

## Search

Use `skilld search "query" -p three` instead of grepping `.skilld/` directories. Run `skilld search --guide -p three` for full syntax, filters, and operators.

<!-- skilld:api-changes -->

## API Changes

This section documents version-specific API changes for Three.js v0.184.0 — focusing on deprecations, breaking changes, and new APIs that LLMs trained on older data may not know.

### Deprecated APIs (Will Be Removed)

- DEPRECATED: `LottieLoader` — deprecated and will be removed with r186. Use lottie-web instead and create animated textures manually. [source](./.skilld/docs/pages/LottieLoader.html.md)

- DEPRECATED: `PostProcessing` — deprecated since r183, replaced by `RenderPipeline`. PostProcessing is now a backward-compatibility wrapper that will be removed in a future version. [source](./.skilld/docs/pages/PostProcessing.html.md)

- DEPRECATED: `VTKLoader` — deprecated since r184 with no explicit replacement announced. [source](./.skilld/docs/pages/VTKLoader.html.md)

- DEPRECATED: `Clock` constructor parameter `autoStart` — deprecated since r183. Use explicit `.start()` and `.stop()` methods instead of relying on automatic start behavior. [source](./.skilld/docs/pages/Clock.html.md:L17)

- DEPRECATED: `KTX2Loader.detectSupportAsync()` — deprecated. Use synchronous `detectSupport()` method instead. [source](./.skilld/docs/pages/KTX2Loader.html.md:L66)

- DEPRECATED: `TSL.PI2` — deprecated constant. Use `TSL.TWO_PI` instead for clarity and consistency. [source](./.skilld/docs/pages/TSL.html.md:L23)

- DEPRECATED: `AnamorphicNode.resolution` property — deprecated. Use `resolutionScale` (number) instead of `resolution` (Vector2). [source](./.skilld/docs/pages/AnamorphicNode.html.md:L49)

- DEPRECATED: `GaussianBlurNode.resolution` property — deprecated. Use `resolutionScale` (number) instead of `resolution` (Vector2). [source](./.skilld/docs/pages/GaussianBlurNode.html.md:L79)

- DEPRECATED: `RenderPipeline.renderAsync()` — deprecated. Use synchronous `render()` method in animation loops instead. [source](./.skilld/docs/pages/RenderPipeline.html.md:L73)

- DEPRECATED: `QuadMesh.renderAsync()` — deprecated. Use synchronous `render()` method instead. [source](./.skilld/docs/pages/QuadMesh.html.md:L53)

- DEPRECATED: `SkyMesh.isSky` property — deprecated. Use `isSkyMesh` property instead for type testing. [source](./.skilld/docs/pages/SkyMesh.html.md:L74)

- DEPRECATED: `UniformNode.label()` method — deprecated. Set `name` property directly instead of using the `label()` method. [source](./.skilld/docs/pages/UniformNode.html.md:L69)

- DEPRECATED: `WorkgroupInfoNode.label()` method — deprecated. Use `setName()` method instead. [source](./.skilld/docs/pages/WorkgroupInfoNode.html.md:L101)

### Recent API Changes

- BREAKING: `material.shadowPositionNode` renamed to `material.receivedShadowPositionNode` — reflects the actual purpose of projecting shadow positions. This enables future support for other shadow-related properties. [source](./.skilld/issues/issue-30849.md:L32)

- NEW: `uniformTexture()` function — new TSL alias for explicit texture uniform declarations. While `texture.value` was always possible, this new function makes intent clearer. [source](./.skilld/issues/issue-30849.md:L34)

- BREAKING: TSL variable naming — removed `transformed` prefix from TSL variables (e.g., `transformedNormalView` → `normalView`, `transformedNormalWorld` → `normalWorld`). Improves readability and reduces verbosity. [source](./.skilld/issues/issue-30849.md:L36)

- DEPRECATED: `append()` in TSL — deprecation evaluated for TSL node chaining. Still required for some void functions but alternative approaches are preferred. [source](./.skilld/issues/issue-30849.md:L30)

**Also changed:** `ComputeNode` added for shader compute patterns · TSL Transpiler improvements for flow control · `.assign()` behavior auto-creates variables when possible

<!-- /skilld:api-changes -->

<!-- skilld:best-practices -->

## Best Practices

- Use TSL (Threejs Shader Language) instead of `.onBeforeCompile()` for shader customization — offers cleaner syntax, automatic optimizations, code reusability across materials, and tree-shaking support without string manipulation [source](./.skilld/docs/TSL.md#introduction-example)

- Use `Fn()` for shader functions with stack support when you need `assign` statements or conditionals — classic JS functions only allow inline approaches [source](./.skilld/docs/TSL.md#function)

- Use `vertexStage()` to move expensive computations from fragment to vertex shader — reduces per-pixel calculations and improves performance [source](./.skilld/docs/TSL.md#varying)

- Export TSL functions with `/*@__PURE__*/` comment prefix to enable tree shaking and reduce bundle size — ensures unused shader code is eliminated during build [source](./.skilld/docs/TSL.md#function)

```js
export const oscSawtooth = /*@__PURE__*/ Fn(([timer = time]) => timer.fract());
```

- Use `uniform.onFrameUpdate()` instead of manual updates in render loops for frame-synchronous values like time — ensures uniforms update once per frame regardless of render-pass count [source](./.skilld/docs/TSL.md#uniformonupdate)

- Share uniforms across multiple materials and post-processing effects using the same uniform instance — automatically optimizes shader compilation and reduces GPU memory [source](./.skilld/docs/TSL.md#share-everything)

```js
const sharedColor = uniform(new THREE.Color());
materialA.colorNode = sharedColor.div(2);
materialB.colorNode = sharedColor.mul(0.5);
```

- Use `vertexStage()` with `varying()` together for optimized calculations — vertex computation with interpolation to fragment shader achieves best performance balance [source](./.skilld/docs/TSL.md#varying)

- Precompile shader materials asynchronously using `renderer.compileAsync()` before first render — prevents frame stalls from shader compilation on first draw call [source](./.skilld/docs/pages/WebGLRenderer.html.md#compileAsync)

- Use object-parameter syntax in `Fn()` for functions with many optional arguments — enables both named and positional calling patterns for flexibility [source](./.skilld/docs/TSL.md#function)

```js
const oscSine = Fn(({ timer = time }) => {
  return timer.mul(2).sin();
});
```

- Set `material.needsUpdate = true` after modifying material properties to signal shader recompilation — required for changes to take effect [source](./.skilld/docs/pages/Material.html.md#needsUpdate)

- Use indexed geometry (BufferGeometry with `.index`) to reuse vertices across triangles — reduces memory footprint and improves performance for complex shapes [source](./.skilld/docs/pages/BufferGeometry.html.md#index)

- Call `geometry.computeBoundingSphere()` after vertex modifications — ensures ray casting and frustum culling work correctly with updated geometry [source](./.skilld/docs/pages/BufferGeometry.html.md#computeBoundingSphere)

- Use `alphaHash` instead of `transparent` + sorting for cheaper alpha transparency — trades precision for performance by using dithering instead of depth sorting [source](./.skilld/docs/pages/Material.html.md#alphaHash)

- Use method chaining for readable TSL expressions — compose operations inline without intermediate variables [source](./.skilld/docs/TSL.md#method-chaining)

```js
material.colorNode = texture(map).rgb.mul(contrast).add(brightness);
```

<!-- /skilld:best-practices -->
