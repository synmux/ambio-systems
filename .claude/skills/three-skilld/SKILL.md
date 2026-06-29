---
name: three-skilld
description: 'ALWAYS use when writing code importing "three". Consult for debugging, best practices, or modifying three, three.js.'
metadata:
  version: 0.185.0
  generated_by: Anthropic · Haiku 4.5
  generated_at: 2026-06-29
---

# mrdoob/three.js `three@0.185.0`

**Tags:** latest: 0.185.0

**References:** [package.json](./.skilld/pkg/package.json) • [README](./.skilld/pkg/README.md) • [Docs](./.skilld/docs/_INDEX.md) • [Issues](./.skilld/issues/_INDEX.md)

## Search

Use `skilld search "query" -p three` instead of grepping `.skilld/` directories. Run `skilld search --guide -p three` for full syntax, filters, and operators.

<!-- skilld:best-practices -->

## Best Practices

- Use `InstancedMesh` for rendering many objects with identical geometry and material but different transformations — reduces draw calls dramatically for performance-critical scenes [source](./.skilld/docs/pages/InstancedMesh.html.md:L1-10)

- Set `needsUpdate = true` on `instanceMatrix` after calling `setMatrixAt()` and on `instanceColor` after `setColorAt()` to notify the engine of transformation changes [source](./.skilld/docs/pages/InstancedMesh.html.md:L51-63)

- Always call `dispose()` on `InstancedMesh`, `BatchedMesh`, and `EffectComposer` when no longer used to free GPU resources and prevent memory leaks [source](./.skilld/docs/pages/InstancedMesh.html.md:L77-79)

- Use `BatchedMesh` for rendering large numbers of objects with the same material but different geometries — provides multi-draw batch rendering to reduce draw calls [source](./.skilld/docs/pages/BatchedMesh.html.md:L1-5)

- Reserve buffer space when adding geometries to `BatchedMesh` if planning to replace with larger geometries later via the `reservedVertexCount` and `reservedIndexCount` parameters [source](./.skilld/docs/pages/BatchedMesh.html.md:L110-130)

- Set `needsUpdate = true` on materials after modifying properties to trigger shader recompilation and reflect changes in the next render [source](./.skilld/docs/pages/Material.html.md:L175-179)

- Disable depth writing for 2D overlays by setting `depthWrite = false` to layer elements without z-index artifacts [source](./.skilld/docs/pages/Material.html.md:L139-145)

- Use `depthTexture` instead of `depthBuffer` on render targets for post-processing to access depth data in shaders [source](./.skilld/docs/pages/RenderTarget.html.md:L43-47)

- Enable MSAA on render targets by setting `samples` to a value > 0 (typically 4 or 8) for smoother output, but balance against performance cost [source](./.skilld/docs/pages/RenderTarget.html.md:L79-85)

- Disable `generateMipmaps` and set it to `false` if creating mipmaps manually to avoid redundant automatic generation [source](./.skilld/docs/pages/Texture.html.md:L119-125)

- Dispose and recreate textures to change dimensions, format, or type — modifying these properties directly after first use has no effect [source](./.skilld/docs/pages/Texture.html.md:L1-7)

- Set `global = true` on nodes that should be declared only once (e.g., `AttributeNode`) in shader graph systems to leverage the internal caching system [source](./.skilld/docs/pages/Node.html.md:L20-25)

- Update `AnimationMixer` with delta time in the render loop via `mixer.update(deltaTime)` to advance animations smoothly [source](./.skilld/docs/pages/AnimationMixer.html.md:L119-129)

- Call `AnimationMixer.uncacheAction()`, `uncacheClip()`, or `uncacheRoot()` to deallocate memory resources, but ensure related actions are stopped first [source](./.skilld/docs/pages/AnimationMixer.html.md:L91-116)
<!-- /skilld:best-practices -->
