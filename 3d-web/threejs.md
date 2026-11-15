# Three.js Fundamentals

Three.js is a JavaScript 3D library for creating and displaying interactive 3D graphics in web browsers. It provides an abstraction over WebGL, making it easier to build 3D scenes, product visualizations, immersive websites, interactive environments, and real-time experiences.

This guide introduces the core concepts, architecture, implementation patterns, and engineering practices AI coding agents should understand when building Three.js applications.

## 1. When to Use Three.js

Three.js is particularly useful for:

- Interactive 3D product showcases.
- Immersive landing pages and portfolios.
- 3D configurators and product previews.
- Interactive educational visualizations.
- Data visualization in three dimensions.
- Animated environments and virtual experiences.
- Custom WebGL effects and shader-driven visuals.

Before introducing 3D, determine whether it genuinely improves the experience. CSS, SVG, canvas, or conventional frontend components may be more appropriate for simpler interfaces.

## 2. Core Concepts

A Three.js application is organized around several fundamental objects.

| Concept | Responsibility |
|---|---|
| Scene | Contains objects, lights, and other scene elements |
| Camera | Defines the viewer's perspective |
| Renderer | Draws the scene onto a canvas |
| Geometry | Defines an object's shape |
| Material | Defines an object's surface appearance |
| Mesh | Combines geometry and material |
| Light | Illuminates objects |
| Texture | Adds image-based surface details |
| Animation loop | Updates and renders the scene over time |

A typical rendering pipeline looks like this:

1. Create a scene.
2. Configure a camera.
3. Initialize a renderer.
4. Create geometry and materials.
5. Combine them into meshes.
6. Add objects and lights to the scene.
7. Render the scene.
8. Update and render continuously when animation is required.

## 3. Project Setup

For a modern application, use a JavaScript build tool such as Vite.

Create a project:

```bash
npm create vite@latest threejs-starter -- --template vanilla
cd threejs-starter
npm install
npm install three
npm run dev
```

A minimal project structure:

```text
threejs-starter/
├── index.html
├── package.json
├── src/
│   ├── main.js
│   ├── style.css
│   └── scene/
│       ├── createScene.js
│       ├── createCamera.js
│       └── createRenderer.js
└── public/
    └── assets/
```

For larger projects, separate scene creation, asset loading, animation, controls, and cleanup into dedicated modules.

## 4. Creating a Scene

A scene is the root container for objects that Three.js renders.

```js
import * as THREE from 'three';

const scene = new THREE.Scene();

scene.background = new THREE.Color(0x101018);
```

You can add meshes, lights, groups, cameras, and other objects to the scene.

Use `THREE.Group` to organize related objects into logical units.

```js
const group = new THREE.Group();

group.add(meshA);
group.add(meshB);

scene.add(group);
```

Groups make it easier to transform and manage collections of objects.

## 5. Understanding Cameras

The camera determines what the viewer sees.

### Perspective Camera

`PerspectiveCamera` creates a perspective projection where distant objects appear smaller.

```js
const camera = new THREE.PerspectiveCamera(
  45,
  window.innerWidth / window.innerHeight,
  0.1,
  100
);

camera.position.set(0, 2, 6);
camera.lookAt(0, 0, 0);
```

Its parameters are:

- Field of view: vertical viewing angle in degrees.
- Aspect ratio: viewport width divided by height.
- Near clipping plane: closest visible distance.
- Far clipping plane: furthest visible distance.

### Orthographic Camera

`OrthographicCamera` preserves the apparent size of objects regardless of their distance.

It is useful for:

- Isometric scenes.
- Architectural diagrams.
- Technical visualizations.
- 2D-like 3D interfaces.

Choose a camera based on the intended visual experience, not simply because one is more familiar.

## 6. Renderer Configuration

The renderer converts the scene and camera into pixels.

```js
const renderer = new THREE.WebGLRenderer({
  antialias: true,
  alpha: true
});

renderer.setSize(
  window.innerWidth,
  window.innerHeight
);

renderer.setPixelRatio(
  Math.min(window.devicePixelRatio, 2)
);

document.body.appendChild(renderer.domElement);
```

For physically based materials and modern color workflows, configure output color space and tone mapping intentionally:

```js
renderer.outputColorSpace = THREE.SRGBColorSpace;
renderer.toneMapping = THREE.ACESFilmicToneMapping;
renderer.toneMappingExposure = 1;
```

These settings affect the final appearance. Validate the result against the desired art direction rather than treating them as universal defaults.

## 7. Geometry

Geometry defines the shape and vertex data of an object.

Common built-in geometries include:

| Geometry | Typical use |
|---|---|
| BoxGeometry | Boxes, product containers, architectural elements |
| SphereGeometry | Planets, balls, abstract forms |
| PlaneGeometry | Floors, backgrounds, surfaces |
| TorusGeometry | Rings and decorative objects |
| CylinderGeometry | Pipes, columns, containers |
| ConeGeometry | Stylized objects and directional forms |
| BufferGeometry | Custom geometry and optimized vertex data |

Example:

```js
const geometry = new THREE.BoxGeometry(1, 1, 1);
```

For custom shapes and procedural geometry, use `BufferGeometry` and understand its attributes, indices, normals, and vertex layout.

Avoid unnecessarily high segment counts. More vertices increase processing and rendering costs.

## 8. Materials

Materials define how a surface responds to light and how it appears.

Important material types:

- `MeshStandardMaterial`: physically based material suitable for most realistic surfaces.
- `MeshPhysicalMaterial`: adds advanced physical effects such as clearcoat and transmission.
- `MeshBasicMaterial`: does not respond to lighting.
- `MeshLambertMaterial`: supports diffuse lighting.
- `MeshPhongMaterial`: supports specular highlights.
- `ShaderMaterial`: allows custom GLSL shader implementation.

Example:

```js
const material = new THREE.MeshStandardMaterial({
  color: 0x4f8cff,
  roughness: 0.4,
  metalness: 0.2
});
```

For realistic materials, consider the relationship between lighting, environment maps, roughness, metalness, and color management.

Do not use physically based material properties as arbitrary decorative sliders. Tune them according to the intended surface.

## 9. Creating Meshes

A mesh combines geometry and material.

```js
const geometry = new THREE.BoxGeometry(1, 1, 1);

const material = new THREE.MeshStandardMaterial({
  color: 0x4f8cff
});

const cube = new THREE.Mesh(geometry, material);

scene.add(cube);
```

A mesh has transform properties:

```js
cube.position.set(0, 0, 0);
cube.rotation.set(0, 0, 0);
cube.scale.set(1, 1, 1);
```

These properties control its position, orientation, and size.

Use meaningful object names when building complex scenes:

```js
cube.name = 'hero-product';
```

This makes debugging and scene inspection easier.

## 10. Lighting

Lighting has a major impact on the visual quality of a scene.

Common light types:

| Light | Purpose |
|---|---|
| AmbientLight | General illumination without a specific direction |
| HemisphereLight | Sky and ground ambient illumination |
| DirectionalLight | Sun-like directional illumination |
| PointLight | Light emitted from a point |
| SpotLight | Focused cone-shaped illumination |
| RectAreaLight | Broad rectangular light source |

Example:

```js
const ambientLight = new THREE.AmbientLight(
  0xffffff,
  0.5
);

const directionalLight = new THREE.DirectionalLight(
  0xffffff,
  2
);

directionalLight.position.set(4, 6, 3);

scene.add(ambientLight, directionalLight);
```

Good lighting should support shape recognition, depth, hierarchy, and material appearance.

For polished product scenes, experiment with:

- Key light.
- Fill light.
- Rim light.
- Environment lighting.
- Contact shadows.
- Controlled reflections.

More lights do not automatically produce better visuals. Use a deliberate lighting setup.

## 11. Textures and Asset Loading

Textures add image-based detail to geometry and materials.

Common texture maps include:

- Color map.
- Normal map.
- Roughness map.
- Metalness map.
- Ambient occlusion map.
- Displacement map.
- Emissive map.

Load textures with `TextureLoader`:

```js
const textureLoader = new THREE.TextureLoader();

const colorTexture = textureLoader.load(
  '/assets/product-color.webp'
);

const material = new THREE.MeshStandardMaterial({
  map: colorTexture
});
```

For 3D models, use `GLTFLoader` for glTF and GLB assets.

```js
import { GLTFLoader } from 'three/addons/loaders/GLTFLoader.js';

const loader = new GLTFLoader();

loader.load(
  '/assets/model.glb',
  (gltf) => {
    scene.add(gltf.scene);
  },
  undefined,
  (error) => {
    console.error('Model loading failed:', error);
  }
);
```

For production applications, handle loading progress, failures, missing assets, and fallback states.

Prefer optimized glTF/GLB assets. Consider texture compression, geometry compression, and appropriate texture resolution.

## 12. Animation Loop

Three.js applications commonly use `requestAnimationFrame` to update and render a scene.

```js
const clock = new THREE.Clock();

function animate() {
  requestAnimationFrame(animate);

  const delta = clock.getDelta();

  cube.rotation.y += delta * 0.5;

  renderer.render(scene, camera);
}

animate();
```

Use delta time so animation speed remains consistent across different frame rates.

For more complex animation systems, consider:

- AnimationMixer for imported model animations.
- GSAP for timeline-based animation.
- Motion for UI transitions.
- Custom procedural animation for interactive objects.

Avoid mixing several animation systems without a clear ownership strategy.

## 13. Responsive Rendering

A 3D canvas must adapt to viewport changes.

```js
function handleResize() {
  const width = window.innerWidth;
  const height = window.innerHeight;

  camera.aspect = width / height;
  camera.updateProjectionMatrix();

  renderer.setSize(width, height);

  renderer.setPixelRatio(
    Math.min(window.devicePixelRatio, 2)
  );
}

window.addEventListener('resize', handleResize);
```

For embedded scenes, use the actual container dimensions instead of assuming the canvas occupies the full browser window. A `ResizeObserver` is useful for this.

Responsive 3D experiences may also need different camera positions, object scales, detail levels, and interaction patterns on mobile devices.

## 14. User Interaction

Three.js supports interactive experiences through pointer events and raycasting.

Raycasting determines which 3D objects intersect with a pointer ray.

```js
const raycaster = new THREE.Raycaster();
const pointer = new THREE.Vector2();

function handlePointerMove(event) {
  pointer.x = (event.clientX / window.innerWidth) * 2 - 1;
  pointer.y = -(event.clientY / window.innerHeight) * 2 + 1;

  raycaster.setFromCamera(pointer, camera);

  const intersections = raycaster.intersectObjects(
    scene.children,
    true
  );

  if (intersections.length > 0) {
    console.log('Hovered object:', intersections[0].object);
  }
}

window.addEventListener('pointermove', handlePointerMove);
```

For production use, account for the canvas bounding rectangle, nested scene objects, pointer capture, touch input, and interaction cleanup.

Common interaction patterns include:

- Hover highlights.
- Click-to-select objects.
- Drag-to-rotate product models.
- Scroll-controlled camera movement.
- Interactive hotspots.
- 3D product configuration.

Use accessible HTML controls alongside canvas interactions. Do not make essential information available only through a 3D scene.

## 15. Organizing a Larger Scene

A maintainable architecture separates responsibilities.

Example:

```text
src/
├── main.js
├── scene/
│   ├── createScene.js
│   ├── createCamera.js
│   ├── createRenderer.js
│   └── createLights.js
├── objects/
│   └── createProduct.js
├── systems/
│   ├── animation.js
│   └── interaction.js
├── assets/
│   └── loadAssets.js
└── utils/
    └── resize.js
```

Keep scene creation separate from application UI, asset loading, animation, and interaction logic.

For larger experiences, define clear ownership of:

- Scene state.
- Camera controls.
- Animation updates.
- Asset lifecycle.
- Event listeners.
- Resource disposal.

## 16. Performance Fundamentals

3D rendering can become expensive quickly. Performance must be considered during design and implementation.

Important practices:

1. Keep geometry complexity appropriate to the object.
2. Reuse geometries and materials where possible.
3. Use instancing for repeated objects.
4. Limit unnecessary draw calls.
5. Optimize model and texture assets.
6. Avoid excessive real-time shadows.
7. Limit device pixel ratio on high-density screens.
8. Avoid unnecessary allocations inside animation loops.
9. Dispose of unused geometries, materials, and textures.
10. Profile on mobile and lower-powered devices.

Example of resource disposal:

```js
mesh.geometry.dispose();

if (Array.isArray(mesh.material)) {
  mesh.material.forEach((material) => material.dispose());
} else {
  mesh.material.dispose();
}
```

When removing an object from a scene, remember that removing it does not automatically dispose of its GPU resources.

Treat shared resources carefully: dispose of a geometry, material, or texture only when it is no longer used elsewhere.

For advanced performance techniques, see [3D Web Optimization](./optimization.md).

## 17. Cleanup and Lifecycle Management

A production-quality scene must clean up resources when it is no longer needed.

Typical cleanup responsibilities include:

- Stop animation loops.
- Remove event listeners.
- Disconnect resize observers.
- Dispose of geometries and materials.
- Dispose of textures when no longer shared.
- Dispose of render targets and controls.
- Dispose of the renderer when the scene is permanently destroyed.
- Remove the renderer canvas from the DOM.

A clean lifecycle prevents memory leaks when scenes are mounted and unmounted repeatedly in frontend applications.

## 18. Common Mistakes

Avoid these implementation mistakes:

- Creating a scene without defining a clear visual purpose.
- Using excessive polygon counts.
- Adding too many lights and real-time shadows.
- Loading unoptimized 3D models.
- Ignoring mobile performance.
- Using fixed canvas dimensions.
- Animating without delta time.
- Forgetting resource disposal.
- Creating multiple render loops accidentally.
- Attaching event listeners without cleanup.
- Using 3D interactions without accessible alternatives.
- Treating a visually attractive screenshot as proof of a functional implementation.

## 19. AI Coding Agent Workflow

When an AI coding agent builds a Three.js experience, it should follow a disciplined workflow.

### Before implementation

- Inspect the existing project and dependencies.
- Identify the framework and rendering environment.
- Understand the requested experience and visual references.
- Determine whether Three.js is necessary.
- Identify required models, textures, and external assets.
- Establish performance and accessibility constraints.

### During implementation

- Build the smallest working scene first.
- Separate scene, camera, renderer, and object responsibilities.
- Add lighting and materials intentionally.
- Introduce animation and interaction incrementally.
- Handle asynchronous asset loading.
- Implement responsive behavior.
- Add proper cleanup.

### During validation

- Confirm the application builds successfully.
- Verify that the scene renders in the browser.
- Test camera framing and object visibility.
- Test pointer and touch interactions.
- Check console errors and failed asset requests.
- Test different viewport sizes.
- Inspect performance on mobile-sized viewports.
- Verify cleanup when the scene is removed.

Do not claim visual verification unless the browser or a screenshot was actually inspected.

## 20. Further Learning

Use the official resources for deeper technical reference:

- [Three.js Documentation](https://threejs.org/docs/)
- [Three.js Manual](https://threejs.org/manual/)
- [Three.js Examples](https://threejs.org/examples/)
- [Three.js GitHub Repository](https://github.com/mrdoob/three.js)
- [Khronos glTF Resources](https://www.khronos.org/gltf/)

## 21. Engineering Checklist

Before considering a Three.js implementation complete:

- [ ] Scene, camera, and renderer are configured correctly.
- [ ] Geometry and materials match the intended design.
- [ ] Lighting supports the visual direction.
- [ ] Assets load with appropriate error handling.
- [ ] Animation uses frame-rate-independent timing.
- [ ] Canvas responds to container resizing.
- [ ] Interaction works with relevant input methods.
- [ ] GPU resources have a clear cleanup lifecycle.
- [ ] Performance is acceptable on mobile devices.
- [ ] Essential content has accessible HTML alternatives.
- [ ] Browser console and build output have been checked.
- [ ] Visual verification has been performed where available.

---

**Next guide:** [React Three Fiber](./react-three-fiber.md) — building declarative Three.js experiences with React, component-based scene architecture, hooks, and Drei.