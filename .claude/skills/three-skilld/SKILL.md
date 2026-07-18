---
name: three-skilld
description: 'JavaScript 3D library. ALWAYS use when writing code importing "three". Consult for debugging, best practices, or modifying three, three.js.'
metadata:
  version: 0.185.1
  generated_by: cached
  generated_at: 2026-07-18
---

# mrdoob/three.js `three@0.185.1`

**Tags:** latest: 0.185.1

**References:** [package.json](./.skilld/pkg/package.json) • [README](./.skilld/pkg/README.md) • [Docs](./.skilld/docs/_INDEX.md) • [Issues](./.skilld/issues/_INDEX.md)

## Search

Use `skilld search "query" -p three` instead of grepping `.skilld/` directories. Run `skilld search --guide -p three` for full syntax, filters, and operators.

<!-- skilld:api-changes -->

## API Changes

This section documents version-specific API changes for three v0.185.1 — prioritising recent major/minor releases and changes that affect current users.

- BREAKING: `PostProcessing` class — renamed to `RenderPipeline` since r183, PostProcessing is a backward-compatibility wrapper only [source](./.skilld/docs/pages/PostProcessing.html.md:L15)

- DEPRECATED: `LottieLoader` — will be removed with r186, use lottie-web instead and create animated textures manually [source](./.skilld/docs/pages/LottieLoader.html.md:L42)

- DEPRECATED: `TSL.colorToDirection()` — since r185, use `TSL.unpackRGBToNormal()` instead [source](./.skilld/docs/pages/TSL.html.md)

- DEPRECATED: `TSL.directionToColor()` — since r185, use `TSL.packNormalToRGB()` instead [source](./.skilld/docs/pages/TSL.html.md)

- DEPRECATED: `TSL.directionToFaceDirection()` — since r185, use `TSL.negateOnBackSide()` instead [source](./.skilld/docs/pages/TSL.html.md)

- DEPRECATED: `Line2NodeMaterial.lineColorNode` — since r185, use `NodeMaterial.colorNode` instead [source](./.skilld/docs/pages/Line2NodeMaterial.html.md:L77)

- DEPRECATED: `PassNode.getResolution()` — since r181, use `PassNode.getResolutionScale()` instead [source](./.skilld/docs/pages/PassNode.html.md)

- DEPRECATED: `PassNode.setResolution()` — since r181, use `PassNode.setResolutionScale()` instead [source](./.skilld/docs/pages/PassNode.html.md)

- DEPRECATED: `Renderer.getColorBufferType()` — since r182, use `Renderer.getOutputBufferType()` instead [source](./.skilld/docs/pages/Renderer.html.md)

- DEPRECATED: `LWOLoader` — since r185, LWO format loader is deprecated [source](./.skilld/docs/pages/LWOLoader.html.md:L41)

- DEPRECATED: `VTKLoader` — since r184, VTK format loader is deprecated [source](./.skilld/docs/pages/VTKLoader.html.md:L37)

- DEPRECATED: `TSL.PI2` constant — use `TSL.TWO_PI` instead [source](./.skilld/docs/pages/TSL.html.md:L23)

- DEPRECATED: `Clock` constructor `autoStart` parameter — since r183 [source](./.skilld/docs/pages/Clock.html.md:L17)

- DEPRECATED: `SkyMesh.isSky` property — use `SkyMesh.isSkyMesh` instead [source](./.skilld/docs/pages/SkyMesh.html.md:L72)

- DEPRECATED: `SVGLoader.createShapes()` — since r185 [source](./.skilld/docs/pages/SVGLoader.html.md)

- DEPRECATED: `DRACOExporter.parse()` — use `DRACOExporter.parseAsync()` instead [source](./.skilld/docs/pages/DRACOExporter.html.md)

- DEPRECATED: `TSL.premultiplyAlphaBlur()` — since r180, use `TSL.gaussianBlur()` with `premultipliedAlpha: true` option instead [source](./.skilld/docs/pages/TSL.html.md)

**Also changed:** `TSL.clearcoatNormalView` deprecated r178 · `TSL.normalView` deprecated r178 · `TSL.normalWorld` deprecated r178 · `viewportResolution` constant deprecated r169 (use `screenSize` instead) · `RenderPipeline.renderAsync()` deprecated
<!-- /skilld:api-changes -->

<!-- skilld:best-practices -->

## Best Practices

- Prefer TSL over manual shader manipulation for cleaner, more maintainable code — TSL is a node-based shader system that eliminates string manipulation and enables composition, automatic optimizations, and cross-platform compilation to WGSL/GLSL [source](./.skilld/docs/TSL.md#why-tsl)

- Always pair environment maps with MeshStandardMaterial and use PMREMGenerator to pre-process them for physically accurate rendering — environment maps provide lighting context that MeshStandardMaterial requires for proper shading [source](./.skilld/docs/pages/MeshStandardMaterial.html.md#envmap)

- Use TextureLoader.loadAsync() instead of the callback-based .load() method for cleaner async/await patterns in modern JavaScript [source](./.skilld/docs/pages/TextureLoader.html.md#code-example)

- Employ Clock.getDelta() in your render loop to obtain consistent frame-independent delta time for animations and physics — this ensures smooth behaviour across varying frame rates [source](./.skilld/docs/pages/AnimationMixer.html.md#update)

- Create one AnimationMixer per animated object to enable independent animation playback and control — calling clipAction() on the same mixer for different objects ensures action reuse and memory efficiency [source](./.skilld/docs/pages/AnimationMixer.html.md#constructor)

- Use InstancedMesh when rendering many objects with identical geometry and material but different world transformations — this drastically reduces draw calls and improves performance [source](./.skilld/docs/pages/InstancedMesh.html.md)

- Leverage indexed geometry (BufferGeometry with an index attribute) to reuse vertices across multiple triangles — this reduces GPU memory overhead and improves performance [source](./.skilld/docs/pages/BufferGeometry.html.md#index)

- Set Material.side to DoubleSide when raycasting against surfaces where both front and back faces may be intersected — by default only front-facing faces are detected [source](./.skilld/docs/pages/Raycaster.html.md#intersectobject)

- Share a single LoadingManager across related loaders to unify progress tracking and load completion events — this is essential when loading interdependent assets like models and textures [source](./.skilld/docs/pages/LoadingManager.html.md#code-example)

- Use UniformsUtils.merge() when combining custom shader uniforms with built-in fog or lighting uniforms — this ensures proper merging and avoids uniform name collisions [source](./.skilld/docs/pages/ShaderMaterial.html.md#fog)

- Disable Object3D.matrixAutoUpdate on static geometry to skip redundant matrix recalculations every frame — manually call updateMatrix() when the object's position, rotation, or scale changes [source](./.skilld/docs/pages/Object3D.html.md#matrixautoupdate)

- Monitor GPU memory and rendering performance via WebGLRenderer.info — track memory usage, draw call counts, and texture allocation to identify bottlenecks [source](./.skilld/docs/pages/WebGLRenderer.html.md#info)

- Always set the needsUpdate flag on InstancedMesh.instanceMatrix and InstancedMesh.instanceColor after batch updates — without this flag, changes are not propagated to the GPU [source](./.skilld/docs/pages/InstancedMesh.html.md#setmatrixat)

- Assign appropriate colorSpace to textures based on their content — use SRGBColorSpace for colour data (diffuse, emissive maps) and NoColorSpace for non-colour data (normal, metalness, roughness maps) [source](./.skilld/docs/pages/MeshStandardMaterial.html.md#colorspace-details)

<!-- /skilld:best-practices -->
