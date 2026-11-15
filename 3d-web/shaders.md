# GLSL Shaders & GPU Programming

Shaders are small programs executed on the GPU to control how 3D objects are rendered. They provide precise control over geometry transformations, surface appearance, lighting, colors, distortions, and procedural visual effects.

GLSL (OpenGL Shading Language) is commonly used to write shaders for WebGL applications.

For modern frontend and 3D web development, shaders make it possible to create visual experiences that go beyond standard materials and lighting.

This guide introduces shader fundamentals, GLSL syntax, Three.js integration, React Three Fiber implementation, procedural effects, optimization, and engineering workflows for AI coding agents.

## 1. What Are Shaders?

A shader is a program that runs on the GPU during the rendering pipeline.

Shaders are responsible for different stages of rendering, including:

- Transforming vertices.
- Calculating surface properties.
- Producing pixel colors.
- Creating procedural patterns.
- Simulating lighting effects.
- Distorting geometry.
- Applying visual effects.

Common applications include:

- Animated gradients.
- Liquid and fluid-like surfaces.
- Glowing objects.
- Dissolve and reveal effects.
- Distorted backgrounds.
- Procedural textures.
- Atmospheric effects.
- Holographic materials.
- Interactive 3D backgrounds.
- Custom transitions.

Shaders are particularly useful when the desired effect cannot be achieved efficiently or precisely with standard materials.

## 2. Understanding the GPU Rendering Pipeline

A simplified rendering pipeline:

1. Application code provides geometry, attributes, uniforms, and textures.
2. The vertex shader processes geometry vertices.
3. The GPU assembles primitives such as triangles.
4. Rasterization determines which screen pixels are covered.
5. The fragment shader calculates output colors for fragments.
6. The renderer combines the output with the framebuffer and other rendering operations.

Two important shader stages are:

| Shader | Responsibility |
|---|---|
| Vertex shader | Processes vertex positions and related vertex data |
| Fragment shader | Calculates the color and other outputs for fragments |

A simplified conceptual flow:

```text
Geometry + Attributes
        |
        v
  Vertex Shader
        |
        v
 Primitive Assembly
        |
        v
   Rasterization
        |
        v
 Fragment Shader
        |
        v
   Final Rendering
```

The exact graphics pipeline contains additional stages and operations, but this model is sufficient for understanding many Three.js shader applications.

## 3. GLSL Fundamentals

GLSL is a strongly typed language designed for GPU programming.

It has syntax similar to C, but it includes specialized data types and functions for graphics calculations.

### Common data types

| Type | Description |
|---|---|
| `float` | Single-precision floating-point value |
| `int` | Integer |
| `bool` | Boolean |
| `vec2` | Two-component vector |
| `vec3` | Three-component vector |
| `vec4` | Four-component vector |
| `mat2` | 2×2 matrix |
| `mat3` | 3×3 matrix |
| `mat4` | 4×4 matrix |
| `sampler2D` | 2D texture sampler |

Example:

```glsl
float intensity = 0.8;

vec2 uv = vec2(0.5, 0.5);

vec3 color = vec3(0.2, 0.5, 1.0);

vec4 finalColor = vec4(color, 1.0);
```

### Vector operations

GLSL supports vector arithmetic:

```glsl
vec3 a = vec3(1.0, 2.0, 3.0);
vec3 b = vec3(2.0, 1.0, 4.0);

vec3 sum = a + b;
vec3 difference = a - b;
vec3 scaled = a * 2.0;
```

Useful functions include:

- `dot()`
- `cross()`
- `normalize()`
- `length()`
- `distance()`
- `mix()`
- `clamp()`
- `smoothstep()`
- `step()`
- `sin()`
- `cos()`
- `pow()`
- `abs()`
- `mod()`
- `fract()`

Example:

```glsl
float distanceFromCenter = length(uv - vec2(0.5));

float mask = smoothstep(
  0.4,
  0.1,
  distanceFromCenter
);
```

These functions are fundamental to procedural visual effects.

## 4. Vertex Shaders

The vertex shader processes each vertex of the geometry.

It commonly transforms local-space vertex positions into clip-space coordinates.

A basic vertex shader:

```glsl
void main() {
  gl_Position =
    projectionMatrix *
    modelViewMatrix *
    vec4(position, 1.0);
}
```

In Three.js, the built-in variables in standard shader programs can include:

- `position`: vertex position.
- `normal`: vertex normal.
- `uv`: texture coordinates.
- `modelMatrix`: object transformation matrix.
- `viewMatrix`: camera view matrix.
- `projectionMatrix`: camera projection matrix.
- `modelViewMatrix`: combined model and view transformation.

The exact available variables depend on the shader type and how it is configured.

### Vertex displacement

Vertex shaders can modify geometry before rasterization.

```glsl
uniform float uTime;

void main() {
  vec3 displacedPosition = position;

  displacedPosition.z +=
    sin(position.x * 4.0 + uTime) * 0.1;

  gl_Position =
    projectionMatrix *
    modelViewMatrix *
    vec4(displacedPosition, 1.0);
}
```

This produces a simple wave-like displacement.

Vertex displacement is useful for:

- Ocean surfaces.
- Animated terrain.
- Organic shapes.
- Distorted objects.
- Procedural motion.

The geometry must contain enough vertices to represent the desired deformation smoothly.

## 5. Fragment Shaders

The fragment shader determines the output color for fragments produced during rasterization.

A minimal fragment shader:

```glsl
void main() {
  gl_FragColor = vec4(0.2, 0.5, 1.0, 1.0);
}
```

This outputs a blue color with full opacity in a WebGL 1-style shader.

For WebGL 2 GLSL, the output is explicitly declared:

```glsl
out vec4 outColor;

void main() {
  outColor = vec4(0.2, 0.5, 1.0, 1.0);
}
```

In Three.js, shader language and compatibility depend on the renderer and material configuration. Do not mix GLSL versions or output conventions without checking the selected shader configuration.

Fragment shaders are commonly used for:

- Gradients.
- Procedural patterns.
- Texture effects.
- Surface coloration.
- Noise.
- Fresnel effects.
- Glows.
- Distortion.

## 6. Uniforms, Attributes, and Varyings

Shader programs need data from the application and geometry.

Three important concepts are uniforms, attributes, and varyings.

### Uniforms

Uniforms provide values shared across shader invocations for a draw call.

Examples:

- Animation time.
- Mouse position.
- Color.
- Resolution.
- Intensity.
- Texture references.

```glsl
uniform float uTime;
uniform vec3 uColor;
```

### Attributes

Attributes provide per-vertex data.

Examples:

- Position.
- Normal.
- UV coordinates.
- Custom vertex data.

```glsl
attribute vec3 position;
attribute vec2 uv;
```

In WebGL 2, custom vertex inputs use `in` declarations rather than the WebGL 1 `attribute` keyword.

### Varyings

Varyings pass interpolated data from the vertex shader to the fragment shader.

WebGL 1 example:

```glsl
varying vec2 vUv;

void main() {
  vUv = uv;

  gl_Position =
    projectionMatrix *
    modelViewMatrix *
    vec4(position, 1.0);
}
```

Fragment shader:

```glsl
varying vec2 vUv;

void main() {
  gl_FragColor = vec4(vUv, 0.5, 1.0);
}
```

In GLSL ES 3.00, the corresponding qualifiers are `out` in the vertex shader and `in` in the fragment shader.

## 7. UV Coordinates

UV coordinates describe positions on a surface in two-dimensional texture space.

They generally range from 0 to 1.

- U represents the horizontal texture coordinate.
- V represents the vertical texture coordinate.

Example:

```glsl
vec2 uv = vUv;

vec3 color = vec3(
  uv.x,
  uv.y,
  0.5
);
```

This produces a gradient that changes across the surface.

UV coordinates are essential for:

- Texture mapping.
- Procedural gradients.
- Surface distortion.
- Image sampling.
- Animated patterns.
- Custom material effects.

Understanding UV space is one of the most important foundations for writing useful fragment shaders.

## 8. ShaderMaterial in Three.js

Three.js provides `ShaderMaterial` for creating custom shader programs.

Example:

```js
import * as THREE from 'three';

const material = new THREE.ShaderMaterial({
  uniforms: {
    uColor: {
      value: new THREE.Color('#4f8cff')
    }
  },

  vertexShader: `
    void main() {
      gl_Position =
        projectionMatrix *
        modelViewMatrix *
        vec4(position, 1.0);
    }
  `,

  fragmentShader: `
    uniform vec3 uColor;

    void main() {
      gl_FragColor = vec4(uColor, 1.0);
    }
  `
});
```

Apply the material to geometry:

```js
const geometry = new THREE.SphereGeometry(
  1,
  64,
  64
);

const mesh = new THREE.Mesh(
  geometry,
  material
);

scene.add(mesh);
```

`ShaderMaterial` provides Three.js shader conventions and built-in uniforms and attributes.

For more direct control over shader declarations, `RawShaderMaterial` is available. It requires the developer to supply more of the shader interface explicitly.

Choose the material based on the amount of control required.

## 9. Shader Animation with Time Uniforms

A common technique is passing elapsed time from JavaScript into the shader.

Create a uniform:

```js
const uniforms = {
  uTime: {
    value: 0
  }
};
```

Update it inside the animation loop:

```js
function animate() {
  requestAnimationFrame(animate);

  uniforms.uTime.value += 0.016;

  renderer.render(scene, camera);
}

animate();
```

Use it in GLSL:

```glsl
uniform float uTime;

void main() {
  float wave = sin(uTime);

  vec3 color = vec3(
    0.2 + wave * 0.1,
    0.4,
    1.0
  );

  gl_FragColor = vec4(color, 1.0);
}
```

For accurate timing, pass elapsed time or a frame delta calculated from a clock rather than assuming every frame takes exactly 16 milliseconds.

## 10. Procedural Gradients

Gradients can be generated mathematically without loading image textures.

Example:

```glsl
varying vec2 vUv;

void main() {
  vec3 colorA = vec3(0.1, 0.2, 0.6);
  vec3 colorB = vec3(0.5, 0.2, 0.8);

  vec3 color = mix(
    colorA,
    colorB,
    vUv.y
  );

  gl_FragColor = vec4(color, 1.0);
}
```

The `mix()` function interpolates between two values.

For more advanced gradients:

- Combine multiple color stops.
- Use `smoothstep()` for controlled transitions.
- Use radial distance from a point.
- Animate gradient coordinates.
- Combine gradients with noise.

Procedural gradients are useful for premium backgrounds, hero sections, and abstract visual elements.

## 11. Radial Gradients and Glows

Radial effects can be generated by measuring distance from a center point.

```glsl
varying vec2 vUv;

void main() {
  vec2 center = vec2(0.5);

  float distanceFromCenter =
    distance(vUv, center);

  float glow = 1.0 - smoothstep(
    0.0,
    0.5,
    distanceFromCenter
  );

  vec3 color = vec3(0.3, 0.6, 1.0) * glow;

  gl_FragColor = vec4(color, 1.0);
}
```

This creates a simple radial glow.

For more refined results, combine multiple radial fields, color interpolation, and controlled falloff.

## 12. Noise and Procedural Patterns

Noise is useful for creating natural-looking visual variation.

Common approaches include:

- Value noise.
- Gradient noise.
- Simplex noise.
- Worley noise.
- Fractal Brownian Motion (FBM).

Applications include:

- Clouds.
- Terrain.
- Organic movement.
- Liquid-like distortion.
- Smoke-inspired effects.
- Surface variation.
- Animated backgrounds.

A simple hash-based random function:

```glsl
float random(vec2 st) {
  return fract(
    sin(dot(st, vec2(12.9898, 78.233))) *
    43758.5453
  );
}
```

This can be used to create basic procedural variation.

It is not a replacement for a well-designed coherent noise algorithm. For smoother natural patterns, use a suitable noise implementation.

### Fractal Brownian Motion

FBM combines noise across multiple frequencies and amplitudes.

Conceptually:

1. Start with a base noise function.
2. Sample it at a particular frequency.
3. Increase the frequency.
4. Reduce the amplitude.
5. Accumulate the results across multiple octaves.

FBM is useful for clouds, terrain, organic patterns, and abstract surfaces.

Be mindful of the number of noise evaluations per fragment. Procedural noise can become expensive at high resolutions.

## 13. Fresnel Effects

A Fresnel effect changes the appearance of a surface depending on the angle between its normal and the viewing direction.

It is commonly used for:

- Holographic materials.
- Glowing edges.
- Glass-like surfaces.
- Rim lighting.
- Stylized outlines.

Conceptual implementation:

```glsl
varying vec3 vNormal;
varying vec3 vViewPosition;

void main() {
  vec3 normal = normalize(vNormal);
  vec3 viewDirection = normalize(vViewPosition);

  float fresnel = pow(
    1.0 - abs(dot(normal, viewDirection)),
    3.0
  );

  vec3 baseColor = vec3(0.1, 0.3, 0.8);
  vec3 glowColor = vec3(0.3, 0.8, 1.0);

  vec3 color = mix(
    baseColor,
    glowColor,
    fresnel
  );

  gl_FragColor = vec4(color, 1.0);
}
```

This is a simplified conceptual example. A production shader must calculate and pass the normal and view direction correctly in a consistent coordinate space.

## 14. Mouse Interaction in Shaders

Interactive shader effects can use pointer coordinates passed as uniforms.

JavaScript:

```js
const uniforms = {
  uMouse: {
    value: new THREE.Vector2(0.5, 0.5)
  }
};

window.addEventListener('pointermove', (event) => {
  uniforms.uMouse.value.set(
    event.clientX / window.innerWidth,
    1.0 - event.clientY / window.innerHeight
  );
});
```

Fragment shader:

```glsl
uniform vec2 uMouse;
varying vec2 vUv;

void main() {
  float distanceFromMouse =
    distance(vUv, uMouse);

  float influence = 1.0 - smoothstep(
    0.0,
    0.3,
    distanceFromMouse
  );

  vec3 baseColor = vec3(0.05, 0.1, 0.2);
  vec3 effectColor = vec3(0.2, 0.7, 1.0);

  vec3 color = mix(
    baseColor,
    effectColor,
    influence
  );

  gl_FragColor = vec4(color, 1.0);
}
```

This creates a simple pointer-following glow.

For production:

- Convert pointer coordinates relative to the canvas.
- Account for the canvas position and dimensions.
- Handle pointer exit.
- Consider touch input.
- Avoid unnecessary allocations.
- Smooth pointer movement when appropriate.
- Clean up event listeners.

## 15. React Three Fiber Shader Integration

R3F allows shader materials to be used inside React components.

A basic shader material:

```jsx
import { shaderMaterial } from '@react-three/drei';
import { extend } from '@react-three/fiber';
import * as THREE from 'three';

const GradientMaterial = shaderMaterial(
  {
    uColorA: new THREE.Color('#1d4ed8'),
    uColorB: new THREE.Color('#9333ea'),
    uTime: 0
  },

  `
    varying vec2 vUv;

    void main() {
      vUv = uv;

      gl_Position =
        projectionMatrix *
        modelViewMatrix *
        vec4(position, 1.0);
    }
  `,

  `
    uniform vec3 uColorA;
    uniform vec3 uColorB;
    uniform float uTime;

    varying vec2 vUv;

    void main() {
      float gradient = vUv.y + sin(
        vUv.x * 6.0 + uTime
      ) * 0.1;

      vec3 color = mix(
        uColorA,
        uColorB,
        gradient
      );

      gl_FragColor = vec4(color, 1.0);
    }
  `
);

extend({ GradientMaterial });
```

Use the material in a component:

```jsx
import { useFrame } from '@react-three/fiber';
import { useRef } from 'react';

function GradientSphere() {
  const materialRef = useRef();

  useFrame((state) => {
    materialRef.current.uTime =
      state.clock.elapsedTime;
  });

  return (
    <mesh>
      <sphereGeometry args={[1, 64, 64]} />

      <gradientMaterial
        ref={materialRef}
      />
    </mesh>
  );
}
```

This example demonstrates the integration pattern. Confirm shader output conventions and GLSL version compatibility for the target renderer.

Keep custom shader definitions separate from large scene components when they are reused.

## 16. Custom Shader Material with R3F

For more control, use Three.js `ShaderMaterial` directly.

```jsx
import { shaderMaterial } from '@react-three/drei';
import { useFrame } from '@react-three/fiber';
import { useRef } from 'react';
import * as THREE from 'three';

const CustomMaterial = shaderMaterial(
  {
    uTime: 0,
    uColor: new THREE.Color('#4f8cff')
  },

  `
    varying vec2 vUv;

    void main() {
      vUv = uv;

      gl_Position =
        projectionMatrix *
        modelViewMatrix *
        vec4(position, 1.0);
    }
  `,

  `
    uniform float uTime;
    uniform vec3 uColor;

    varying vec2 vUv;

    void main() {
      float wave = sin(
        vUv.x * 10.0 + uTime
      );

      vec3 color = uColor * (
        0.8 + wave * 0.2
      );

      gl_FragColor = vec4(color, 1.0);
    }
  `
);

function CustomSphere() {
  const material = useRef();

  useFrame((state) => {
    material.current.uTime =
      state.clock.elapsedTime;
  });

  return (
    <mesh>
      <sphereGeometry args={[1, 64, 64]} />
      <primitive
        object={new CustomMaterial()}
        ref={material}
        attach="material"
      />
    </mesh>
  );
}
```

For reusable components, create and manage material instances deliberately. Avoid constructing new GPU resources on every React render.

Choose one consistent shader material pattern within a component rather than combining several competing approaches.

## 17. Vertex Displacement in R3F

Vertex displacement can create animated 3D surfaces.

Common examples include:

- Floating landscapes.
- Animated spheres.
- Ocean waves.
- Organic surfaces.
- Distorted product forms.

The geometry needs enough vertices for smooth deformation.

When implementing vertex displacement:

1. Start with a suitable geometry.
2. Pass time and effect parameters through uniforms.
3. Modify vertex positions in the vertex shader.
4. Account for normals and lighting.
5. Test the effect from different camera angles.
6. Measure performance on target devices.

If the geometry deforms substantially, the original normals may no longer describe the displaced surface accurately.

Consider recalculating or approximating normals as appropriate.

## 18. Textures and Shader Sampling

Fragment shaders can sample textures using texture coordinates.

WebGL 1-style example:

```glsl
uniform sampler2D uTexture;
varying vec2 vUv;

void main() {
  vec4 texel = texture2D(
    uTexture,
    vUv
  );

  gl_FragColor = texel;
}
```

WebGL 2 uses `texture()` rather than the WebGL 1 `texture2D()` function.

Three.js texture handling also involves color-space settings, filtering, wrapping, and orientation.

Use appropriate texture color-space configuration for color maps and distinguish them from non-color data maps such as roughness and normal maps.

Avoid loading unnecessarily large textures. Texture memory can become a major performance bottleneck.

## 19. Shader Effects for Premium Web Experiences

Shaders can create distinctive visual effects for modern websites.

Useful effects include:

| Effect | Typical application |
|---|---|
| Animated gradient | Hero backgrounds |
| Radial glow | Interactive focal points |
| Noise distortion | Organic backgrounds |
| Fresnel glow | 3D product edges |
| Vertex waves | Animated surfaces |
| Dissolve | Reveal transitions |
| Chromatic aberration | Stylized post-processing |
| Liquid distortion | Background transitions |
| Holographic effect | Product presentation |
| Particle shader | Atmospheric environments |

A strong visual direction should guide shader design.

Do not add effects merely because they are technically impressive. They should reinforce the product, storytelling, or interaction.

## 20. Post-Processing

Post-processing applies additional visual operations after the main scene has been rendered.

Common effects include:

- Bloom.
- Depth of field.
- Vignette.
- Noise.
- Chromatic aberration.
- Color grading.
- Blur.
- Screen-space distortion.

In R3F, post-processing can be implemented using the ecosystem's supported post-processing libraries.

A common approach uses `@react-three/postprocessing`:

```bash
npm install @react-three/postprocessing postprocessing
```

Example:

```jsx
import {
  EffectComposer,
  Bloom
} from '@react-three/postprocessing';

function Effects() {
  return (
    <EffectComposer>
      <Bloom
        intensity={0.8}
        luminanceThreshold={0.2}
      />
    </EffectComposer>
  );
}
```

Add effects to the scene:

```jsx
function Experience() {
  return (
    <>
      <ProductModel />
      <Effects />
    </>
  );
}
```

Check current package documentation for supported properties and compatibility.

Post-processing can increase GPU cost significantly. Use only the effects that meaningfully improve the visual result.

## 21. Shader Performance Optimization

Shaders execute many times across rendered fragments and vertices. Expensive calculations can become costly quickly.

Important optimization principles:

### Reduce fragment complexity

Avoid unnecessary calculations in fragment shaders, particularly when the effect covers a large portion of the screen.

### Control resolution

High device pixel ratios increase the number of fragments processed.

Consider limiting rendering resolution on mobile and high-density screens.

### Avoid unnecessary noise calculations

Noise functions, multiple octaves, and complex mathematical operations can become expensive.

Use only as much procedural detail as the visual effect needs.

### Optimize geometry

Vertex shader cost is influenced by vertex count.

Use geometry complexity appropriate to the deformation and final viewing distance.

### Reuse shader materials

Avoid repeatedly creating materials and shader programs unnecessarily.

### Minimize texture bandwidth

Use appropriate texture resolutions and formats.

### Avoid unnecessary post-processing

Each additional render pass can increase rendering cost.

### Profile before optimizing

Measure performance instead of guessing which part of a shader is expensive.

Test on representative low-powered devices, not only a high-end development machine.

## 22. Shader Debugging

Shader debugging can be challenging because shader programs execute on the GPU.

Common problems include:

- Compilation errors.
- Invalid GLSL syntax.
- Incorrect uniform types.
- Missing attributes.
- Incompatible GLSL versions.
- Incorrect coordinate spaces.
- Unexpected color-space behavior.
- Incorrect texture sampling.
- NaN or infinite values.
- Incorrect geometry normals.

Recommended debugging process:

1. Start with a minimal shader.
2. Confirm the geometry renders.
3. Output a constant color.
4. Add UV coordinates.
5. Add uniforms individually.
6. Add mathematical operations gradually.
7. Inspect shader compilation logs.
8. Verify coordinate spaces.
9. Test across supported browsers and devices.

A useful debugging fragment shader:

```glsl
varying vec2 vUv;

void main() {
  gl_FragColor = vec4(
    vUv.x,
    vUv.y,
    0.0,
    1.0
  );
}
```

This helps verify that UV coordinates are being passed correctly.

## 23. WebGL and WebGPU Considerations

Three.js has traditionally used WebGL for browser-based 3D rendering.

WebGL remains an important target for broad browser compatibility.

WebGPU provides a newer graphics and compute API with a different programming model. It can enable more advanced GPU workloads, but availability and support depend on browsers, devices, and the chosen Three.js implementation.

Important distinctions:

- GLSL is commonly used for WebGL shader programming.
- WebGPU commonly uses WGSL for shaders.
- A GLSL shader is not automatically compatible with WebGPU.
- Three.js provides renderer and material options that evolve over time.
- Feature support must be tested in the actual target environment.

Do not assume a custom GLSL implementation will work unchanged with a WebGPU renderer.

When building cross-platform applications, choose the rendering backend intentionally and provide fallbacks where necessary.

## 24. Common Shader Development Mistakes

Avoid these mistakes:

- Writing complex shaders before testing a minimal shader.
- Mixing GLSL 1 and GLSL 3 syntax.
- Forgetting to pass required varyings.
- Using incorrect coordinate spaces.
- Ignoring surface normals after displacement.
- Using excessive procedural noise.
- Running expensive effects at full device resolution.
- Creating new materials every frame.
- Forgetting to clean up manually managed resources.
- Using incompatible shader and renderer configurations.
- Assuming WebGL GLSL works unchanged in WebGPU.
- Ignoring texture color-space configuration.
- Using shader effects that make content difficult to read.
- Skipping mobile performance testing.

## 25. AI Coding Agent Workflow

AI coding agents should use a structured approach when implementing custom shaders.

### Before implementation

- Inspect the existing Three.js or R3F architecture.
- Identify the rendering backend.
- Check the installed Three.js version.
- Understand the visual reference.
- Identify the required effect and its coordinate space.
- Determine whether a standard material or existing shader helper is sufficient.
- Define mobile and performance constraints.

### During implementation

- Begin with a minimal working shader.
- Establish vertex and fragment interfaces.
- Introduce uniforms incrementally.
- Validate coordinate transformations.
- Separate shader source from scene composition when appropriate.
- Use reusable shader components for repeated effects.
- Avoid unnecessary GPU resource creation.
- Provide sensible defaults and fallbacks.

### During validation

- Confirm shaders compile successfully.
- Check the browser console.
- Verify the effect on actual geometry.
- Test different camera positions.
- Inspect lighting and normals.
- Check texture and color-space behavior.
- Test different viewport sizes.
- Measure performance on mobile.
- Confirm cleanup and resource lifecycle.

AI agents must not claim that a shader effect is visually correct merely because the source code compiles.

## 26. Further Learning

Official resources:

- [Three.js Documentation](https://threejs.org/docs/)
- [Three.js ShaderMaterial](https://threejs.org/docs/#api/en/materials/ShaderMaterial)
- [Three.js RawShaderMaterial](https://threejs.org/docs/#api/en/materials/RawShaderMaterial)
- [React Three Fiber Documentation](https://r3f.docs.pmnd.rs/)
- [The Book of Shaders](https://thebookofshaders.com/)
- [Shadertoy](https://www.shadertoy.com/)
- [WebGL Fundamentals](https://webglfundamentals.org/)
- [MDN WebGL Documentation](https://developer.mozilla.org/en-US/docs/Web/API/WebGL_API)

Use these resources to explore shader techniques, inspect working examples, and understand browser graphics APIs.

## 27. Engineering Checklist

Before considering a shader implementation complete:

- [ ] Shader purpose and visual requirements are clearly defined.
- [ ] Vertex and fragment shader interfaces are correct.
- [ ] GLSL syntax matches the selected renderer configuration.
- [ ] Uniforms and attributes are correctly declared.
- [ ] Coordinate spaces are understood.
- [ ] Geometry supports the intended deformation.
- [ ] Normals are handled appropriately.
- [ ] Texture color-space settings are correct.
- [ ] Shader compilation succeeds.
- [ ] GPU resource lifecycle is managed.
- [ ] Performance is acceptable on mobile.
- [ ] Post-processing is used intentionally.
- [ ] Fallback behavior is considered.
- [ ] Essential interface content remains accessible.
- [ ] Visual output has been inspected where available.

---

**Next guide:** [3D Web Optimization](./optimization.md) — GPU performance, draw calls, geometry, textures, rendering costs, asset compression, memory management, and production optimization.