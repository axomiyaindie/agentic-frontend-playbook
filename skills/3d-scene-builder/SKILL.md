---
name: 3d-scene-builder
description: Plan, build, improve, and optimize interactive browser-based 3D scenes using Three.js, React Three Fiber, Drei, WebGL, and related tools. Use when creating 3D websites, interactive product visualizations, 3D portfolios, immersive landing pages, or browser-based 3D experiences.
---

# 3D Scene Builder

## Purpose

Guide AI coding agents through the design, implementation, and optimization of production-quality interactive 3D web experiences.

Prioritize visual quality, rendering performance, maintainability, accessibility, and compatibility with the existing project.

## Workflow

### 1. Understand the requirements

Identify:

- The purpose of the 3D experience.
- The intended visual style.
- Required objects and interactions.
- Target devices and screen sizes.
- Performance expectations.
- Available 3D assets and references.
- Existing frontend framework and rendering setup.

Do not begin implementation before understanding the intended experience.

### 2. Inspect the project

Before changing code:

1. Inspect the repository structure.
2. Identify the existing framework and build tooling.
3. Check installed Three.js and React Three Fiber versions.
4. Review existing components and styling conventions.
5. Identify available models, textures, and other assets.
6. Preserve existing project architecture.

Do not install a second rendering stack when an appropriate one already exists.

### 3. Choose the rendering approach

Choose based on project requirements.

- Use Three.js for direct control over the rendering pipeline.
- Use React Three Fiber for declarative 3D scenes in React applications.
- Use Drei when its helpers simplify common React Three Fiber tasks.
- Use custom shaders when built-in materials cannot achieve the required visual result.

Do not introduce unnecessary abstraction or dependencies.

### 4. Plan the scene

Define:

- Scene hierarchy.
- Camera type and position.
- Lighting strategy.
- Geometry and materials.
- Background and environment.
- Animation behavior.
- Interaction model.
- Asset loading strategy.

Prefer a clear, maintainable scene structure.

### 5. Implement the scene

Build incrementally:

1. Establish the rendering canvas.
2. Configure the camera.
3. Create primary geometry.
4. Add materials and lighting.
5. Integrate required assets.
6. Implement animation.
7. Add user interactions.
8. Integrate the scene into the surrounding interface.

Use appropriate resource management and lifecycle cleanup.

### 6. Optimize rendering

Review:

- Polygon and draw-call counts.
- Texture resolution and compression.
- Model complexity.
- Lighting and shadow costs.
- Animation calculations.
- Asset loading and caching.
- Memory consumption.
- Mobile GPU performance.

Use instancing, level of detail, compressed assets, and lazy loading where appropriate.

Do not optimize blindly; identify actual bottlenecks.

### 7. Validate the experience

Test:

- Initial loading.
- Camera behavior.
- Interaction responsiveness.
- Desktop and mobile layouts.
- Different viewport sizes.
- WebGL availability.
- Error and loading states.
- Reduced-motion behavior.
- Graceful fallback behavior.

Confirm that the surrounding interface remains usable if 3D rendering fails.

## Engineering Rules

- Follow existing project conventions.
- Use version-compatible APIs.
- Keep scene components modular.
- Dispose of resources when appropriate.
- Avoid unnecessary React state updates during rendering.
- Avoid excessive real-time shadows.
- Avoid unnecessarily large textures.
- Never block essential navigation behind 3D rendering.
- Provide meaningful loading and failure states.
- Respect accessibility and reduced-motion preferences.

## Expected Output

A completed 3D implementation should include:

- A functional 3D scene.
- Appropriate camera and lighting.
- Responsive integration.
- Working interactions where required.
- Performance-conscious asset handling.
- Accessible fallbacks.
- Validation results and known limitations.

## Common Mistakes

Avoid:

- Adding 3D without a clear design purpose.
- Using oversized models and textures.
- Rendering unnecessary objects.
- Creating expensive lighting configurations.
- Ignoring mobile performance.
- Failing to clean up resources.
- Using APIs incompatible with installed versions.
- Treating a successful desktop preview as proof of mobile readiness.

## Completion Checklist

- [ ] Requirements understood.
- [ ] Existing project inspected.
- [ ] Rendering approach justified.
- [ ] Scene structure implemented.
- [ ] Materials and lighting reviewed.
- [ ] Interactions tested.
- [ ] Performance considered.
- [ ] Responsive behavior checked.
- [ ] Accessibility and fallbacks considered.
- [ ] Limitations documented.
