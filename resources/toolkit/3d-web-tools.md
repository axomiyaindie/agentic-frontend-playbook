# 3D Web Development Tools

A collection of 3D engines, React integrations, asset optimization tools, and resources for creating immersive browser-based experiences.

## 3D Engines

### Three.js
- **Website:** https://threejs.org/
- **GitHub:** https://github.com/mrdoob/three.js
- **Purpose:** JavaScript library for creating and displaying 3D graphics in browsers.
- **Use cases:** 3D portfolios, product configurators, interactive scenes, and WebGL experiences.
- **Getting started:** https://threejs.org/manual/

### Babylon.js
- **Website:** https://www.babylonjs.com/
- **GitHub:** https://github.com/BabylonJS/Babylon.js
- **Purpose:** Full-featured real-time 3D engine for web applications.
- **Use cases:** Interactive 3D applications, simulations, and browser-based games.
- **Getting started:** https://doc.babylonjs.com/

### PlayCanvas
- **Website:** https://playcanvas.com/
- **GitHub:** https://github.com/playcanvas/engine
- **Purpose:** Web-first 3D engine and development platform.
- **Use cases:** Browser games, interactive 3D experiences, and real-time applications.
- **Getting started:** https://developer.playcanvas.com/

## React Three.js Ecosystem

### React Three Fiber
- **Website:** https://r3f.docs.pmnd.rs/
- **GitHub:** https://github.com/pmndrs/react-three-fiber
- **Purpose:** React renderer for Three.js.
- **Use cases:** Declarative 3D scenes in React and Next.js applications.
- **Getting started:** https://r3f.docs.pmnd.rs/getting-started/introduction

### Drei
- **Website:** https://drei.docs.pmnd.rs/
- **GitHub:** https://github.com/pmndrs/drei
- **Purpose:** Collection of useful helpers and abstractions for React Three Fiber.
- **Use cases:** Camera controls, environment lighting, loaders, staging, and scene utilities.
- **Getting started:** `npm install @react-three/drei`

### React Three Postprocessing
- **Website:** https://react-postprocessing.docs.pmnd.rs/
- **GitHub:** https://github.com/pmndrs/react-postprocessing
- **Purpose:** Post-processing effects for React Three Fiber.
- **Use cases:** Bloom, depth of field, tone mapping, and visual effects.
- **Getting started:** Follow the official documentation for installation and effect usage.

## Animation and Timeline Tools

### Theatre.js
- **Website:** https://www.theatrejs.com/
- **GitHub:** https://github.com/theatre-js/theatre
- **Purpose:** Visual animation timeline editor for web projects and 3D scenes.
- **Use cases:** Product animations, camera choreography, and interactive storytelling.
- **Getting started:** https://www.theatrejs.com/docs/latest

## 3D Creation and Asset Optimization

### Blender
- **Website:** https://www.blender.org/
- **GitHub:** https://github.com/blender/blender
- **Purpose:** Open-source 3D creation software.
- **Use cases:** Modeling, materials, rigging, animation, and rendering.
- **Getting started:** https://docs.blender.org/manual/en/latest/

### glTF Transform
- **Website:** https://gltf-transform.dev/
- **GitHub:** https://github.com/donmccurdy/glTF-Transform
- **Purpose:** Tools for inspecting, processing, and optimizing glTF and GLB assets.
- **Use cases:** Compressing models, optimizing textures, and preparing assets for real-time web rendering.
- **Getting started:** `npm install --global @gltf-transform/cli`

### Khronos glTF Sample Viewer
- **Website:** https://github.khronos.org/glTF-Sample-Viewer-Release/
- **GitHub:** https://github.com/KhronosGroup/glTF-Sample-Viewer
- **Purpose:** Reference viewer for glTF assets.
- **Use cases:** Previewing models and checking materials and rendering behavior.
- **Getting started:** Open the viewer and load a supported glTF asset.

## 3D Asset Libraries

### Poly Haven
- **Website:** https://polyhaven.com/
- **Purpose:** Library of HDRIs, textures, and 3D models.
- **Use cases:** Environment lighting, realistic materials, and scene assets.
- **Getting started:** Browse assets and check the individual usage and license information.

### Sketchfab
- **Website:** https://sketchfab.com/
- **Purpose:** Platform for discovering and previewing 3D models.
- **Use cases:** Finding reference models and downloadable assets.
- **Getting started:** Check the license and download permissions for each individual model.

### Kenney Assets
- **Website:** https://kenney.nl/assets
- **GitHub:** https://github.com/KenneyNL
- **Purpose:** Game and prototyping asset collections.
- **Use cases:** Rapid prototyping and interactive 3D projects.
- **Getting started:** Download an asset pack and review its included license information.

## Production Recommendations

- Prefer optimized glTF or GLB assets.
- Compress geometry and textures where appropriate.
- Lazy-load expensive scenes and models.
- Use level of detail when appropriate.
- Provide loading states and graceful fallbacks.
- Test performance on mobile devices and integrated GPUs.
- Verify asset licenses before redistribution or commercial use.