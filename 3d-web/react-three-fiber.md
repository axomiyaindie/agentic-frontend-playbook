# React Three Fiber (R3F)

React Three Fiber (R3F) is a React renderer for Three.js. It allows developers to build interactive 3D scenes using React components, JSX, hooks, and familiar frontend development patterns.

Instead of manually creating and managing every Three.js object, developers describe a 3D scene declaratively. R3F translates that component structure into Three.js objects and manages their lifecycle.

This guide covers the architecture, implementation patterns, hooks, interactions, asset loading, performance, and engineering practices AI coding agents should understand when building React-based 3D experiences.

## 1. What Is React Three Fiber?

React Three Fiber connects the React component model with the Three.js rendering engine.

It provides:

- Declarative 3D scene composition.
- React components for Three.js objects.
- Hooks for accessing scene state and frame updates.
- Integration with React state and application architecture.
- Component lifecycle management.
- Support for Three.js materials, geometries, lights, and cameras.
- Integration with Drei and other ecosystem libraries.

R3F is not a replacement for Three.js. It is a React-based way to work with Three.js.

Understanding Three.js fundamentals is important before building complex R3F applications.

Read [Three.js Fundamentals](./threejs.md) first if you are unfamiliar with scenes, cameras, materials, lighting, and geometry.

## 2. When to Use React Three Fiber

R3F is particularly useful when a 3D experience is part of a React application.

Common use cases include:

- Interactive 3D landing pages.
- Product configurators.
- 3D portfolios.
- Animated product showcases.
- Interactive storytelling.
- Immersive dashboards.
- Virtual environments.
- Web-based 3D editors.
- Interactive educational experiences.

R3F is especially valuable when the 3D scene needs to communicate with surrounding React components, application state, routing, or user interfaces.

For a simple standalone 3D experiment, plain Three.js may be sufficient. Avoid adding React and R3F to a project when their additional architecture does not provide meaningful value.

## 3. Project Setup

For an existing React application, install the required packages:

```bash
npm install three @react-three/fiber
```

For helper components and utilities:

```bash
npm install @react-three/drei
```

For a new project, Vite is a practical starting point:

```bash
npm create vite@latest r3f-starter -- --template react
cd r3f-starter
npm install
npm install three @react-three/fiber @react-three/drei
npm run dev
```

Check the official compatibility guidance when selecting package versions. React Three Fiber major versions have specific React compatibility requirements.

Do not blindly upgrade React, Three.js, R3F, and Drei independently. Verify that the selected versions work together.

## 4. Recommended Project Structure

A small project can start with a simple structure:

```text
src/
├── App.jsx
├── main.jsx
├── components/
│   ├── Scene.jsx
│   └── Experience.jsx
├── objects/
│   └── ProductModel.jsx
├── hooks/
│   └── useSceneControls.js
├── assets/
│   └── models/
└── styles/
    └── global.css
```

For larger projects, organize the 3D experience by responsibility:

```text
src/
├── app/
│   ├── App.jsx
│   └── routes/
├── components/
│   ├── ui/
│   └── layout/
├── three/
│   ├── CanvasRoot.jsx
│   ├── scenes/
│   │   ├── ProductScene.jsx
│   │   └── PortfolioScene.jsx
│   ├── objects/
│   ├── materials/
│   ├── lights/
│   ├── effects/
│   ├── hooks/
│   └── utilities/
├── assets/
│   ├── models/
│   ├── textures/
│   └── environments/
└── styles/
```

Keep application UI, scene composition, reusable 3D objects, asset loading, and interaction logic organized.

Do not create excessive abstractions for a small scene. Introduce additional structure when complexity justifies it.

## 5. The Canvas Component

`Canvas` is the primary entry point for an R3F scene.

It creates and manages the underlying Three.js renderer, scene, camera, and rendering lifecycle.

```jsx
import { Canvas } from '@react-three/fiber';

function App() {
  return (
    <Canvas>
      <mesh>
        <boxGeometry args={[1, 1, 1]} />
        <meshStandardMaterial color="royalblue" />
    </mesh>
    </Canvas>
  );
}

export default App;
```

The Canvas component supports configuration through properties such as:

- `camera`
- `gl`
- `shadows`
- `dpr`
- `frameloop`
- `orthographic`
- `events`
- `onCreated`

Example:

```jsx
<Canvas
  camera={{ position: [0, 2, 6], fov: 45 }}
  shadows
  dpr={[1, 2]}
>
  <Experience />
</Canvas>
```

Use the Canvas configuration deliberately. The correct camera, pixel ratio, shadow settings, and rendering mode depend on the experience and target devices.

## 6. JSX and Three.js Objects

R3F uses JSX elements to describe Three.js objects.

Many Three.js classes can be represented through corresponding JSX elements.

| Three.js class | R3F JSX element |
|---|---|
| Scene | Managed by Canvas |
| Mesh | `<mesh />` |
| Group | `<group />` |
| BoxGeometry | `<boxGeometry />` |
| SphereGeometry | `<sphereGeometry />` |
| MeshStandardMaterial | `<meshStandardMaterial />` |
| PerspectiveCamera | `<perspectiveCamera />` |
| DirectionalLight | `<directionalLight />` |
| PointLight | `<pointLight />` |

Example:

```jsx
function Box() {
  return (
    <mesh position={[0, 0, 0]}>
      <boxGeometry args={[1, 1, 1]} />

      <meshStandardMaterial
        color="#4f8cff"
        roughness={0.4}
        metalness={0.2}
      />
    </mesh>
  );
}
```

R3F maps JSX elements to Three.js objects and manages their creation, updates, and removal.

The `args` property supplies constructor arguments for the underlying Three.js object.

For example:

```jsx
<sphereGeometry args={[1, 32, 32]} />
```

This creates a sphere with radius 1 and 32 width and height segments.

Use JSX for ordinary scene composition. Use explicit Three.js objects when a task requires custom imperative behavior or functionality not conveniently represented through JSX.

## 7. Component-Based Scene Architecture

One of the biggest advantages of R3F is reusable component-based scene construction.

Example:

```jsx
function Product() {
  return (
    <group>
      <mesh>
        <boxGeometry args={[2, 1, 1]} />
        <meshStandardMaterial color="#202020" />
      </mesh>

      <mesh position={[0, 0.6, 0]}>
        <sphereGeometry args={[0.25, 32, 32]} />
        <meshStandardMaterial color="#4f8cff" />
      </mesh>
    </group>
  );
}
```

Compose the scene using smaller components:

```jsx
function Experience() {
  return (
    <>
      <ambientLight intensity={0.5} />

      <directionalLight
        position={[4, 6, 3]}
        intensity={2}
      />

      <Product />
    </>
  );
}
```

This improves:

- Reusability.
- Maintainability.
- Readability.
- Testing.
- Separation of responsibilities.
- Collaboration between frontend and 3D development.

Prefer components with clear responsibilities instead of one enormous scene component containing all objects, lights, animations, and interactions.

## 8. The useFrame Hook

`useFrame` is one of the most important R3F hooks.

It runs a callback before each rendered frame and is used for continuous updates such as rotation, movement, procedural animation, and camera changes.

```jsx
import { useRef } from 'react';
import { useFrame } from '@react-three/fiber';

function RotatingBox() {
  const meshRef = useRef();

  useFrame((state, delta) => {
    meshRef.current.rotation.y += delta * 0.5;
  });

  return (
    <mesh ref={meshRef}>
      <boxGeometry args={[1, 1, 1]} />
      <meshStandardMaterial color="orange" />
    </mesh>
  );
}
```

Important concepts:

- `state` provides access to the current R3F state.
- `delta` represents elapsed time since the previous frame.
- `meshRef` provides access to the underlying Three.js object.

Use delta time for frame-rate-independent animation.

### Important performance rule

Do not use React state updates inside `useFrame` for continuous animation.

Avoid:

```jsx
useFrame(() => {
  setRotation((value) => value + 0.01);
});
```

This triggers repeated React updates and can create unnecessary rendering work.

Prefer direct updates to Three.js objects:

```jsx
useFrame((state, delta) => {
  meshRef.current.rotation.y += delta;
});
```

Use React state for meaningful application changes, not every animation frame.

## 9. The useThree Hook

`useThree` provides access to the R3F state and renderer context.

```jsx
import { useThree } from '@react-three/fiber';

function SceneInformation() {
  const { camera, gl, scene, size, viewport } = useThree();

  console.log(camera);
  console.log(gl);
  console.log(scene);
  console.log(size);
  console.log(viewport);

  return null;
}
```

Common values include:

- `camera`: active Three.js camera.
- `gl`: renderer.
- `scene`: current scene.
- `size`: canvas dimensions in pixels.
- `viewport`: dimensions in Three.js world units.
- `clock`: frame timing information.
- `pointer`: normalized pointer coordinates.
- `raycaster`: scene raycasting utility.

Use `useThree` inside components rendered within the R3F Canvas context.

It is not a general-purpose React hook for components outside Canvas.

## 10. Loading Models with useGLTF

Drei provides `useGLTF` for loading glTF and GLB models.

```jsx
import { useGLTF } from '@react-three/drei';

function ProductModel() {
  const { scene } = useGLTF('/models/product.glb');

  return <primitive object={scene} />;
}
```

For production projects, remember that loaded model scenes may be shared or cached.

If multiple instances of a model need independent transformations or materials, consider cloning the scene or using an appropriate instancing strategy.

Do not mutate shared cached materials without understanding the consequences for other instances.

### Preloading models

```jsx
useGLTF.preload('/models/product.glb');
```

Preloading can reduce perceived loading time when the asset is likely to be needed.

Do not preload every asset indiscriminately. Prioritize assets that improve the initial experience.

### Handling loading states

Use React Suspense and an appropriate fallback:

```jsx
import { Suspense } from 'react';
import { Canvas } from '@react-three/fiber';

function App() {
  return (
    <Canvas>
      <Suspense fallback={null}>
        <ProductModel />
      </Suspense>
    </Canvas>
  );
}
```

For a polished experience, provide a visible HTML loading interface outside the Canvas when loading may take noticeable time.

Also account for failed asset requests and unavailable network connections.

## 11. Drei: Useful Helpers and Components

`@react-three/drei` is a collection of useful helpers built around React Three Fiber and Three.js.

It reduces repetitive implementation work and provides common building blocks.

Frequently used utilities include:

| Component or hook | Purpose |
|---|---|
| `OrbitControls` | Orbit camera interaction |
| `Environment` | Environment-based lighting |
| `ContactShadows` | Ground contact shadows |
| `Float` | Floating animation |
| `Text` | 3D text |
| `Html` | Render HTML inside a 3D scene |
| `useGLTF` | Load glTF and GLB models |
| `useTexture` | Load textures |
| `Bounds` | Fit camera framing to objects |
| `Stage` | Convenient product presentation setup |
| `PresentationControls` | Interactive presentation controls |
| `MeshReflectorMaterial` | Reflective surface material |

Example:

```jsx
import {
  OrbitControls,
  Environment,
  Float
} from '@react-three/drei';

function Experience() {
  return (
    <>
      <Environment preset="studio" />

      <Float speed={2} rotationIntensity={0.3}>
        <ProductModel />
      </Float>

      <OrbitControls
        enableZoom={false}
        minPolarAngle={Math.PI / 3}
        maxPolarAngle={Math.PI / 1.8}
      />
    </>
  );
}
```

Drei is a utility library, not a requirement for every R3F application.

Use its components when they simplify implementation and match the intended experience. Check component documentation and version compatibility before relying on a specific API.

## 12. Camera Controls

Camera interaction is important for product previews, 3D portfolios, and interactive environments.

`OrbitControls` allows users to rotate, zoom, and pan around a target.

```jsx
import { OrbitControls } from '@react-three/drei';

function Experience() {
  return (
    <>
      <ProductModel />

      <OrbitControls
        enablePan={false}
        minDistance={3}
        maxDistance={8}
      />
    </>
  );
}
```

For guided product presentations, consider limiting camera movement to preserve the intended composition.

Other useful approaches include:

- Programmatic camera animation.
- Scroll-driven camera movement.
- Fixed camera compositions.
- PresentationControls for interactive product rotation.
- Custom camera controllers.

Avoid giving users unrestricted camera movement when it makes the experience confusing or allows important content to disappear.

## 13. Interactions and Events

R3F supports pointer events on interactive scene objects.

Example:

```jsx
import { useState } from 'react';

function InteractiveBox() {
  const [active, setActive] = useState(false);

  return (
    <mesh
      scale={active ? 1.2 : 1}
      onClick={() => setActive(!active)}
      onPointerOver={() => setActive(true)}
      onPointerOut={() => setActive(false)}
    >
      <boxGeometry args={[1, 1, 1]} />
      <meshStandardMaterial
        color={active ? 'hotpink' : 'royalblue'}
      />
    </mesh>
  );
}
```

Common event handlers include:

- `onClick`
- `onPointerDown`
- `onPointerUp`
- `onPointerOver`
- `onPointerOut`
- `onPointerMove`
- `onDoubleClick`
- `onPointerMissed`

R3F uses raycasting to determine which objects receive pointer events.

For complex nested scenes, understand event propagation and use `event.stopPropagation()` where appropriate.

### Interaction design principles

- Provide clear visual feedback.
- Avoid relying exclusively on hover.
- Support touch devices.
- Keep interactive areas large enough.
- Provide accessible HTML controls for important actions.
- Ensure users can understand the result of an interaction.

A 3D object should not become the only way to access essential application functionality.

## 14. State Management: React vs. Three.js

A common architectural mistake is using React state for every small change in a 3D scene.

Choose the right update mechanism for each responsibility.

| Requirement | Recommended approach |
|---|---|
| Selected product option | React state |
| Open or closed UI panel | React state |
| Current application route | Router state |
| Continuous mesh rotation | `useFrame` |
| High-frequency object movement | Refs and Three.js objects |
| Camera movement | Controls or frame updates |
| User preferences | Application state |
| Animation timeline | Animation system such as GSAP |

React should manage application-level state and meaningful interface changes.

Three.js objects and refs should handle frequent visual updates.

This separation helps avoid unnecessary React reconciliation and improves rendering performance.

## 15. Animation with R3F

R3F supports several animation approaches.

### useFrame

Best for:

- Continuous rotation.
- Procedural motion.
- Physics-related updates.
- Camera tracking.
- Simple interactive animations.

### Three.js AnimationMixer

Best for:

- Imported character animations.
- GLTF animation clips.
- Model-based animation systems.

### GSAP

Best for:

- Timeline-based animation.
- Scroll-triggered experiences.
- Coordinated transitions.
- Complex landing-page motion.

### Motion

Best for:

- React interface transitions.
- Component animations.
- UI state changes.
- Layout animation.

Choose one primary owner for each animated property.

For example, do not let GSAP and `useFrame` both independently control the same mesh position without a clear coordination strategy.

## 16. Scroll-Driven Experiences

Scroll-based 3D experiences are common in immersive websites.

Drei provides `useScroll` for scroll-driven animation when used with its `ScrollControls` system.

```jsx
import {
  ScrollControls,
  useScroll
} from '@react-three/drei';

import { useFrame } from '@react-three/fiber';
import { useRef } from 'react';

function AnimatedObject() {
  const ref = useRef();
  const scroll = useScroll();

  useFrame(() => {
    const progress = scroll.offset;

    ref.current.rotation.y = progress * Math.PI * 2;
    ref.current.position.y = -progress * 2;
  });

  return (
    <mesh ref={ref}>
      <torusGeometry args={[1, 0.3, 16, 64]} />
      <meshStandardMaterial color="cyan" />
    </mesh>
  );
}

function Experience() {
  return (
    <ScrollControls pages={3} damping={0.2}>
      <AnimatedObject />
    </ScrollControls>
  );
}
```

This is a basic illustration of scroll-driven transforms. A complete website may need synchronized HTML sections, responsive scroll behavior, and clear control over page navigation.

For sophisticated storytelling, consider the relationship between:

- Scroll position.
- Camera movement.
- Object transformations.
- HTML content.
- Animation timelines.
- Mobile input behavior.

Avoid creating scroll experiences that make normal navigation difficult or cause motion discomfort.

## 17. HTML Inside a 3D Scene

Drei's `Html` component allows HTML elements to appear positioned relative to 3D objects.

```jsx
import { Html } from '@react-three/drei';

function ProductLabel() {
  return (
    <mesh>
      <sphereGeometry args={[0.5, 32, 32]} />
      <meshStandardMaterial color="orange" />

      <Html position={[0, 1, 0]} center>
        <div className="product-label">
          Featured Product
        </div>
      </Html>
    </mesh>
  );
}
```

This is useful for:

- Product labels.
- Interactive annotations.
- Tooltips.
- Navigation markers.
- 3D information panels.

For important text and controls, ordinary HTML layout may be more appropriate than placing everything inside the 3D canvas.

## 18. Responsive 3D Experiences

Responsive 3D design requires more than resizing the Canvas.

Consider:

- Container dimensions.
- Camera framing.
- Object positioning.
- Field of view.
- Device pixel ratio.
- Interaction methods.
- Geometry detail.
- Lighting and shadows.
- Loading performance.

Example:

```jsx
import { useThree } from '@react-three/fiber';

function ResponsiveScene() {
  const { viewport } = useThree();

  const isMobile = viewport.width < 5;

  return (
    <ProductModel
      scale={isMobile ? 0.75 : 1}
    />
  );
}
```

This is a simple world-space example, not a universal mobile breakpoint strategy.

For production interfaces, combine viewport measurements with actual container dimensions and responsive HTML layout.

Test on real mobile devices whenever possible.

## 19. Performance Optimization

R3F applications can become expensive when scenes contain many objects, complex shaders, large textures, or excessive effects.

Important practices:

### Reduce unnecessary React updates

Do not update React state every frame.

Use refs and `useFrame` for continuous visual changes.

### Reuse geometry and materials

Avoid creating new geometries and materials unnecessarily.

Share resources when objects have the same geometry and material requirements.

### Use instancing

For many repeated objects, consider:

- `InstancedMesh`
- Drei's `Instances`
- Batched geometry where appropriate

Instancing can significantly reduce draw calls for repeated geometry.

### Optimize models

- Reduce unnecessary polygon counts.
- Compress textures.
- Remove unused materials.
- Use appropriate texture resolutions.
- Optimize GLB files.
- Consider level of detail for complex scenes.

### Control rendering costs

- Limit device pixel ratio.
- Avoid excessive shadows.
- Reduce expensive post-processing.
- Avoid unnecessary transparency.
- Keep shader complexity appropriate.
- Use demand rendering when continuous animation is unnecessary.

### Use performance tools

Drei includes utilities such as `PerformanceMonitor` and `Stats` that can help inspect performance.

Example:

```jsx
import { Stats } from '@react-three/drei';

function Experience() {
  return (
    <>
      <Stats />
      <ProductModel />
    </>
  );
}
```

Use development profiling tools during optimization and test production builds on representative devices.

For deeper optimization techniques, see [3D Web Optimization](./optimization.md).

## 20. Rendering Modes and Demand Rendering

R3F supports different frame-loop modes through the Canvas `frameloop` property.

Common options:

- `always`: continuously render frames.
- `demand`: render when invalidated.
- `never`: rendering is controlled manually.

Example:

```jsx
<Canvas frameloop="demand">
  <Experience />
</Canvas>
```

Demand rendering is useful for mostly static scenes that only need updates after interactions or state changes.

When using demand rendering, imperative updates may need to call `invalidate()` to request a new frame.

Do not use demand rendering for an experience that requires continuous animation unless the animation system is designed to request frames appropriately.

## 21. Resource Lifecycle and Cleanup

R3F manages much of the lifecycle of declaratively created objects, but custom resources still require careful ownership.

Pay attention to:

- Manually created geometries.
- Manually created materials.
- Textures.
- Render targets.
- Post-processing resources.
- Event listeners.
- External controls.
- Animation mixers.
- Custom subscriptions.

R3F supports automatic disposal for many declaratively managed objects when they are removed from the scene.

The `dispose` property can be used to customize disposal behavior. For example, `dispose={null}` can prevent automatic disposal when a resource is intentionally shared.

Understand resource ownership before disabling automatic disposal or sharing cached objects.

For manually managed resources, use React lifecycle cleanup or an explicit resource-management strategy.

Avoid disposing of shared assets while another scene or component still uses them.

## 22. Error Handling and Loading Experience

A production-ready 3D application should handle more than successful rendering.

Consider:

- Model loading failures.
- Missing texture files.
- Network interruptions.
- Unsupported browser features.
- WebGL initialization failures.
- Slow devices.
- Component errors.
- Empty or incomplete assets.

Recommended strategies:

1. Provide loading indicators.
2. Display a fallback when an asset fails.
3. Use React error boundaries for component failures.
4. Provide an alternative HTML presentation where practical.
5. Avoid blocking the entire application while a nonessential 3D asset loads.
6. Test with slow network conditions.

A beautiful 3D scene should enhance the application, not prevent users from accessing its essential content.

## 23. Accessibility

Canvas content is not automatically accessible in the same way as ordinary HTML.

Important principles:

- Provide meaningful HTML descriptions for important 3D content.
- Include accessible controls for scene actions.
- Support keyboard interaction where applicable.
- Do not depend only on pointer hover.
- Respect reduced-motion preferences.
- Provide a non-3D fallback for essential information.
- Maintain readable contrast in surrounding interface elements.

Use HTML for forms, navigation, headings, buttons, and essential content.

Treat the 3D scene as an interactive visual layer rather than a replacement for the entire semantic interface.

## 24. Common Mistakes

Avoid these mistakes when developing R3F applications:

- Treating R3F as a replacement for understanding Three.js.
- Using React state for every animation frame.
- Putting the entire application into one Canvas component.
- Creating unnecessary components and abstractions.
- Loading large models without optimization.
- Mutating shared cached materials unexpectedly.
- Using unrestricted camera controls.
- Adding expensive effects without measuring performance.
- Ignoring mobile interaction.
- Forgetting custom resource cleanup.
- Depending exclusively on 3D content for important information.
- Installing incompatible versions of React, Three.js, R3F, and Drei.
- Claiming a scene is visually correct without inspecting it.

## 25. AI Coding Agent Workflow

AI coding agents should follow a structured process when implementing an R3F experience.

### Before implementation

- Inspect the existing React application.
- Identify installed React, Three.js, R3F, and Drei versions.
- Read the existing project architecture.
- Understand the visual reference and interaction requirements.
- Determine which objects and assets are required.
- Identify mobile and performance constraints.
- Decide what belongs in HTML and what belongs in Canvas.

### During implementation

- Create a minimal working Canvas first.
- Separate the scene into reusable components.
- Keep UI state separate from high-frequency animation updates.
- Use Drei helpers where appropriate.
- Load models and textures efficiently.
- Implement responsive camera and object behavior.
- Add interactions incrementally.
- Handle loading, errors, and cleanup.
- Avoid introducing unnecessary dependencies.

### During validation

- Run the application and confirm Canvas renders.
- Check browser console errors.
- Verify all models and textures load.
- Test camera movement and interactions.
- Test mobile and desktop viewport sizes.
- Check loading and failure states.
- Inspect rendering performance.
- Confirm that unmounting scenes does not leak resources.
- Verify that essential information remains accessible without 3D interaction.

Do not report visual or browser testing as completed unless it was actually performed.

## 26. Official Resources

Use these resources for technical reference:

- [React Three Fiber Documentation](https://r3f.docs.pmnd.rs/)
- [React Three Fiber GitHub Repository](https://github.com/pmndrs/react-three-fiber)
- [Drei Documentation](https://drei.docs.pmnd.rs/)
- [Drei GitHub Repository](https://github.com/pmndrs/drei)
- [Three.js Documentation](https://threejs.org/docs/)
- [Three.js Manual](https://threejs.org/manual/)

Consult the official documentation for current APIs, package compatibility, and implementation details.

## 27. Engineering Checklist

Before considering an R3F implementation complete:

- [ ] React, Three.js, R3F, and Drei versions are compatible.
- [ ] Canvas is configured correctly.
- [ ] Scene architecture is modular and understandable.
- [ ] Reusable 3D components have clear responsibilities.
- [ ] `useFrame` is used appropriately.
- [ ] React state is not updated unnecessarily every frame.
- [ ] Models and textures load correctly.
- [ ] Loading and error states are handled.
- [ ] Interactions work on relevant input devices.
- [ ] Camera behavior supports the intended experience.
- [ ] Responsive behavior is tested.
- [ ] Rendering performance is acceptable.
- [ ] Resource ownership and cleanup are understood.
- [ ] Essential content has accessible HTML alternatives.
- [ ] Browser console and build output have been checked.
- [ ] Visual verification has been performed where available.

---

**Next guide:** [GLSL Shaders](./shaders.md) — understanding vertex shaders, fragment shaders, uniforms, custom materials, procedural effects, and GPU-based visual experiences.