# Interactive 3D Product Showcase — Example Project

A production-minded blueprint for building immersive product presentation experiences using modern frontend technologies and real-time 3D rendering.

This example demonstrates how AI coding agents can combine product storytelling, interactive 3D visualization, animation, responsive interfaces, and performance engineering to create a polished digital product showcase.

The objective is to make products easier to explore, understand, and appreciate through interactive visual experiences.

---

## 1. Project Overview

### Concept

Build an interactive product showcase for a fictional premium consumer electronics product.

Visitors should be able to explore the product from different angles, inspect its details, change available configurations, and understand its features through a combination of 3D visualization and conventional interface elements.

The experience should feel premium and intuitive without sacrificing usability or performance.

### Example Product

**Product:** AURORA ONE

**Category:** Premium wireless headphones.

**Concept:** A fictional pair of premium wireless headphones presented through an immersive 3D product experience.

All product specifications, features, prices, and marketing claims in this example are illustrative. They must not be presented as verified product facts.

### Project Goals

- Create an engaging product introduction.
- Provide interactive 3D product visualization.
- Allow users to inspect product details.
- Demonstrate available color and material variations.
- Present product features clearly.
- Support responsive desktop and mobile experiences.
- Maintain accessibility and performance.
- Keep the product interface usable when 3D is unavailable.

---

## 2. Recommended Technology Stack

| Category | Technology | Purpose |
|---|---|---|
| Framework | Next.js | Application architecture |
| UI | React | Interface composition |
| Language | TypeScript | Type safety |
| Styling | Tailwind CSS | Responsive styling |
| 3D engine | Three.js | Real-time rendering |
| React 3D | React Three Fiber | Declarative 3D scenes |
| 3D utilities | Drei | Scene helpers and controls |
| Animation | GSAP | Complex timelines |
| UI animation | Motion | Interface transitions |
| Icons | Lucide React | Interface icons |
| Validation | Zod | Configuration validation |

Inspect the existing application before selecting or installing dependencies. Avoid adding multiple libraries that perform the same job.

---

## 3. Experience Architecture

The experience should combine an immersive product viewer with a clear product information hierarchy.

### Main Sections

1. Product introduction.
2. Interactive 3D viewer.
3. Product features.
4. Materials and color variations.
5. Product details.
6. Technical specifications.
7. Frequently asked questions.
8. Purchase or inquiry CTA.

### Suggested User Journey

```text id="s0d4a1"
Product Landing
      |
      v
Product Introduction
      |
      v
Interactive 3D Viewer
      |
      +---- Rotate Product
      |
      +---- Inspect Hotspots
      |
      +---- Change Color
      |
      +---- Explore Materials
      |
      v
Feature Details
      |
      v
Specifications
      |
      v
Purchase / Inquiry
```

The visitor should never need to interact with the 3D scene to access essential product information.

---

## 4. Visual Direction

### Recommended Aesthetic

A premium editorial product presentation.

Suggested characteristics:

- Neutral or dark background.
- Large product imagery.
- Carefully controlled lighting.
- Minimal interface elements.
- Strong product typography.
- Generous negative space.
- Subtle motion.
- Clear product details.
- Consistent visual hierarchy.

The design should highlight the product rather than overwhelm it with decorative effects.

### Example Design Tokens

```css id="d02kz7"
:root {
  --color-background: #f5f5f2;
  --color-surface: #ffffff;
  --color-text: #151515;
  --color-muted: #737373;
  --color-accent: #6c7bff;
  --color-border: #deded8;

  --radius-small: 8px;
  --radius-medium: 16px;
  --radius-large: 24px;

  --content-width: 1280px;
}
```

These are starting values. Adapt them to the product's actual brand identity.

### Typography

Use typography to establish hierarchy:

- Large display heading.
- Concise product description.
- Clear feature titles.
- Readable specification labels.
- Distinct CTA labels.

Avoid typography that reduces readability or obscures product information.

---

## 5. 3D Product Viewer

The product viewer is the centerpiece of the experience.

### Core Capabilities

- Display the product model.
- Rotate the product.
- Zoom where appropriate.
- Change product variants.
- Select interactive hotspots.
- Transition between viewing positions.
- Reset the camera.
- Provide a default product orientation.

### Recommended Scene Structure

```text id="b0x5zq"
ProductViewer
├── Canvas
│   ├── Camera
│   ├── Lighting
│   ├── Environment
│   ├── ProductModel
│   ├── Hotspots
│   └── SceneEffects
│
├── ViewerControls
│   ├── RotateControl
│   ├── ZoomControl
│   └── ResetControl
│
└── ProductInformation
    ├── ProductTitle
    ├── VariantSelector
    └── FeaturePanel
```

Separate scene responsibilities from interface responsibilities.

### Product Model Requirements

Prefer a properly optimized GLB or GLTF model.

Before implementation, inspect:

- Polygon count.
- Material count.
- Texture dimensions.
- UV mapping.
- Model scale.
- Pivot and origin.
- Animation tracks.
- File size.
- Licensing and usage permissions.

The product model should be prepared specifically for real-time web rendering.

### Model Loading

Use an appropriate asset loading strategy.

- Load the primary product model.
- Show a meaningful loading state.
- Avoid blocking the entire interface.
- Handle loading failures.
- Reuse loaded assets where possible.
- Avoid repeatedly parsing the same model.

A product page should still provide meaningful content while the model loads.

---

## 6. Product Interaction Design

Interactions should feel natural and predictable.

### 6.1 Rotation

Visitors should be able to inspect the product from different angles.

Recommended behavior:

- Pointer drag on desktop.
- Touch gestures on mobile.
- Smooth rotation.
- Sensible rotation limits where appropriate.
- Reset to the default view.
- No unexpected camera jumps.

### 6.2 Zoom

Allow visitors to inspect product details when zoom adds genuine value.

Requirements:

- Reasonable minimum and maximum distance.
- Avoid clipping through the model.
- Provide a reset option.
- Preserve usability on touch devices.

### 6.3 Variant Selection

Allow visitors to select available product variants.

Example fictional variants:

- Midnight Black.
- Arctic Silver.
- Cloud White.

Variant changes may update:

- Material color.
- Roughness.
- Metallic appearance.
- Product imagery.
- Variant name.
- Associated product information.

Do not imply that a variant is available for purchase unless the underlying product data confirms it.

### 6.4 Hotspots

Interactive hotspots can identify product components.

For the fictional headphones:

- Ear cushions.
- Headband.
- Control buttons.
- Charging port.
- Outer ear cups.

Each hotspot should provide concise information.

Requirements:

- Clear visual indicator.
- Accessible equivalent information.
- Keyboard-accessible selection.
- Touch-friendly target size.
- No reliance on hover alone.

### 6.5 Feature Exploration

A selected feature can update a dedicated information panel.

Example:

```text id="d0k7qz"
Selected Feature
      |
      v
Update Feature Panel
      |
      v
Show Title
      |
      v
Show Description
      |
      v
Optional Camera Transition
```

Keep camera animation and content updates coordinated without coupling all interface state to the rendering loop.

---

## 7. Product Configuration Architecture

Separate product information from rendering logic.

### Example Product Data

```ts
export type ProductVariant = {
  id: string;
  name: string;
  color: string;
  material: string;
};

export type ProductFeature = {
  id: string;
  title: string;
  description: string;
  hotspotPosition: [number, number, number];
};

export type Product = {
  id: string;
  name: string;
  description: string;
  modelPath: string;
  variants: ProductVariant[];
  features: ProductFeature[];
};

export const product: Product = {
  id: "aurora-one",
  name: "AURORA ONE",
  description: "An illustrative premium headphone concept.",
  modelPath: "/models/aurora-one.glb",
  variants: [
    {
      id: "midnight",
      name: "Midnight Black",
      color: "#242424",
      material: "matte",
    },
    {
      id: "silver",
      name: "Arctic Silver",
      color: "#b9bec6",
      material: "metallic",
    },
    {
      id: "white",
      name: "Cloud White",
      color: "#e9e9e6",
      material: "matte",
    },
  ],
  features: [],
};
```

This is illustrative data. Production values, model paths, and feature positions must match the actual assets.

### State Management

Keep application state explicit.

Example state:

```ts
type ProductViewerState = {
  selectedVariantId: string;
  selectedFeatureId: string | null;
  isAutoRotating: boolean;
  isViewerReady: boolean;
};
```

Use local React state when the state belongs to a single component. Introduce shared state only when multiple parts of the application genuinely need it.

Avoid storing high-frequency animation values in React state.

---

## 8. Suggested Component Architecture

```text
src/
├── app/
│   ├── layout.tsx
│   ├── page.tsx
│   └── globals.css
│
├── components/
│   ├── layout/
│   │   ├── Header.tsx
│   │   └── Footer.tsx
│   │
│   ├── product/
│   │   ├── ProductHero.tsx
│   │   ├── ProductViewer.tsx
│   │   ├── ProductFeatures.tsx
│   │   ├── ProductSpecifications.tsx
│   │   ├── ProductVariants.tsx
│   │   └── ProductCTA.tsx
│   │
│   ├── three/
│   │   ├── ProductCanvas.tsx
│   │   ├── ProductScene.tsx
│   │   ├── ProductModel.tsx
│   │   ├── ProductHotspot.tsx
│   │   ├── CameraController.tsx
│   │   └── ProductLighting.tsx
│   │
│   └── ui/
│       ├── Button.tsx
│       ├── LoadingState.tsx
│       ├── VariantSwatch.tsx
│       └── FeaturePanel.tsx
│
├── data/
│   └── product.ts
│
├── hooks/
│   ├── useReducedMotion.ts
│   └── useProductViewer.ts
│
├── lib/
│   └── product-utils.ts
│
└── types/
    └── product.ts

public/
├── models/
├── textures/
├── images/
└── fonts/
```

Adjust the structure to the size and complexity of the actual implementation.

---

## 9. Animation Strategy

Motion should make product exploration feel polished and responsive.

### Recommended Animations

| Element | Animation |
|---|---|
| Product introduction | Subtle entrance |
| Product model | Controlled reveal |
| Product rotation | Smooth interpolation |
| Variant selection | Material transition |
| Hotspot | Small emphasis |
| Feature panel | Fade and position transition |
| Section changes | Restrained scroll reveal |
| CTA | Hover and pressed feedback |

### GSAP

Use GSAP when complex animation timelines are needed.

Possible uses:

- Product reveal sequences.
- Coordinated camera movement.
- Scroll-based storytelling.
- Multi-stage product presentations.
- Complex transition choreography.

### Motion

Use Motion for:

- Interface transitions.
- Variant selector feedback.
- Feature panel changes.
- Dialog and popover transitions.
- Button interactions.

Avoid having GSAP and Motion animate the same property on the same element.

### Reduced Motion

Respect user motion preferences.

- Disable unnecessary auto-rotation.
- Reduce camera movement.
- Simplify scroll transitions.
- Avoid aggressive parallax.
- Keep all product information available.

---

## 10. Lighting and Materials

Product presentation depends heavily on lighting and material quality.

### Lighting Strategy

Possible lighting setup:

- Environment lighting.
- Soft key light.
- Fill light.
- Rim light.
- Controlled ambient illumination.

The lighting should reveal product geometry and material characteristics without producing excessive glare.

### Material Considerations

Review:

- Base color.
- Metallic value.
- Roughness.
- Normal maps.
- Texture resolution.
- Material consistency.

Use realistic values where the actual product materials are known. For conceptual products, clearly treat the appearance as a visual representation rather than verified physical specifications.

### Environment Maps

Use suitable environment maps to improve reflections and material appearance.

Optimize their resolution and loading behavior.

Avoid unnecessary lighting complexity.

---

## 11. Responsive Design

A desktop 3D viewer should not simply be scaled down for mobile.

### Desktop

- Larger interactive viewport.
- Pointer-based controls.
- Detailed product presentation.
- Side-by-side product information where appropriate.

### Tablet

- Adjusted camera framing.
- Simplified layout.
- Larger interaction targets.
- Balanced product and text composition.

### Mobile

- Touch-friendly rotation.
- Simplified controls.
- Smaller rendering workload.
- Product information in a readable stacked layout.
- Clear variant selectors.
- Alternative product imagery where needed.

### Non-3D Fallback

If WebGL is unavailable or the 3D model fails:

- Display an optimized product image.
- Keep variant selection usable where possible.
- Preserve product descriptions.
- Show feature details.
- Keep the primary CTA functional.

Never make the 3D canvas the only source of important product information.

---

## 12. Performance Optimization

3D product viewers can consume significant CPU, GPU, memory, and network resources.

### Geometry

- Optimize polygon count.
- Remove invisible geometry.
- Reuse geometry where possible.
- Use instancing for repeated objects.
- Avoid unnecessary model complexity.

### Textures

- Resize textures according to their use.
- Use compressed texture formats where supported.
- Avoid loading unused maps.
- Reuse compatible textures.
- Consider KTX2/Basis for appropriate assets.

### Models

- Use GLB/GLTF.
- Consider Draco or Meshopt compression.
- Inspect model structure.
- Avoid unnecessarily large embedded assets.
- Load optional assets progressively.

### Rendering

- Avoid excessive real-time shadows.
- Limit post-processing.
- Avoid unnecessary continuous rendering.
- Use demand-based rendering where appropriate.
- Avoid expensive calculations in the render loop.
- Clean up unused resources.

### Loading

1. Render the HTML product information.
2. Load the essential product imagery.
3. Initialize the 3D viewer.
4. Load optional visual details.
5. Enable interactions after the viewer is ready.

### Performance Validation

Measure:

- Initial page load.
- Model download size.
- Texture memory.
- GPU rendering behavior.
- Frame rate during interaction.
- Mobile device behavior.
- JavaScript bundle size.
- Core Web Vitals.

Do not claim the viewer is optimized without testing it on representative devices.

---

## 13. Accessibility

The product showcase must remain usable without visual or pointer-based interaction.

Requirements:

- Semantic HTML.
- Accessible names for viewer controls.
- Keyboard-accessible variant selectors.
- Keyboard-accessible feature information.
- Visible focus indicators.
- Meaningful product image alternatives.
- Clear loading and error messages.
- Reduced-motion support.
- Sufficient color contrast.
- Touch-friendly controls.
- A non-3D product information experience.

Color variants must have readable names; do not identify them by color alone.

Provide a clear reset or alternative navigation mechanism for interactive camera controls.

---

## 14. SEO and Product Information

Ensure important product information exists in normal HTML rather than only inside the 3D canvas.

Recommended content:

- Product name.
- Product description.
- Product category.
- Features.
- Technical specifications.
- Relevant imagery.
- Accurate metadata.

Use structured data only when it accurately reflects a real product and its current information.

For fictional demonstrations, do not publish fabricated prices, ratings, availability, or reviews as real product data.

---

## 15. Testing Strategy

### Functional Testing

- [ ] Product model loads successfully.
- [ ] Loading state works.
- [ ] Model failure is handled.
- [ ] Rotation works with pointer input.
- [ ] Rotation works with touch input.
- [ ] Zoom controls work.
- [ ] Camera reset works.
- [ ] Variant selection updates the product.
- [ ] Hotspots show correct information.
- [ ] Primary CTA works.

### Responsive Testing

- [ ] Desktop layout.
- [ ] Tablet layout.
- [ ] Mobile layout.
- [ ] No horizontal overflow.
- [ ] Touch targets are usable.
- [ ] Product framing remains appropriate.

### Visual Testing

- [ ] Model scale and position.
- [ ] Lighting and materials.
- [ ] Camera composition.
- [ ] Typography.
- [ ] Spacing.
- [ ] Variant transitions.
- [ ] Hotspot placement.
- [ ] Loading and fallback states.

### Accessibility Testing

- [ ] Keyboard navigation.
- [ ] Focus visibility.
- [ ] Screen reader labels.
- [ ] Reduced-motion behavior.
- [ ] Product information without 3D.
- [ ] Color-independent variant labels.

### Performance Testing

- [ ] Model size.
- [ ] Texture size.
- [ ] Initial loading.
- [ ] Interaction frame rate.
- [ ] Mobile rendering.
- [ ] Memory cleanup.
- [ ] Browser console errors.

---

## 16. Implementation Roadmap

### Phase 1 — Product and Asset Preparation

- [ ] Define the product concept.
- [ ] Identify required product information.
- [ ] Select or create the 3D model.
- [ ] Verify asset licensing.
- [ ] Inspect model geometry and materials.
- [ ] Prepare optimized product imagery.

### Phase 2 — Frontend Foundation

- [ ] Initialize the application.
- [ ] Configure TypeScript.
- [ ] Establish design tokens.
- [ ] Build the application shell.
- [ ] Create product information components.
- [ ] Implement responsive layouts.

### Phase 3 — 3D Viewer

- [ ] Configure React Three Fiber.
- [ ] Build the product scene.
- [ ] Load the model.
- [ ] Configure camera and lighting.
- [ ] Add rotation and zoom.
- [ ] Implement camera reset.
- [ ] Handle loading and error states.

### Phase 4 — Product Interactions

- [ ] Implement variants.
- [ ] Add material transitions.
- [ ] Add product hotspots.
- [ ] Build feature panels.
- [ ] Connect viewer interactions to interface state.

### Phase 5 — Animation and Polish

- [ ] Add product reveal.
- [ ] Implement camera transitions.
- [ ] Add interface transitions.
- [ ] Refine hover and pressed states.
- [ ] Add reduced-motion behavior.

### Phase 6 — Optimization and Validation

- [ ] Optimize the model.
- [ ] Compress textures.
- [ ] Review rendering behavior.
- [ ] Test mobile performance.
- [ ] Implement non-3D fallback.
- [ ] Validate accessibility.
- [ ] Perform visual review.
- [ ] Measure performance.

---

## 17. AI Coding Agent Instructions

### Before Implementation

1. Inspect the existing repository.
2. Identify framework and dependency versions.
3. Understand the product requirements.
4. Inspect available product assets.
5. Verify asset licenses and usage permissions.
6. Define the product's visual direction.
7. Plan the scene architecture.
8. Define the interface and viewer state model.
9. Establish responsive and accessibility requirements.

### During Implementation

1. Build the product information interface first.
2. Implement the design system.
3. Load a simple 3D model before adding complexity.
4. Configure camera and lighting.
5. Add interactions incrementally.
6. Keep rendering logic separate from UI logic.
7. Avoid unnecessary React state updates in render loops.
8. Implement graceful loading and failure states.
9. Validate on real browser viewports.

### During Review

Ask:

- Is the product immediately understandable?
- Does the 3D model accurately represent the intended product?
- Are product controls intuitive?
- Can visitors access details without using the 3D viewer?
- Do variant changes work correctly?
- Does the experience work on mobile?
- Are all important interactions accessible?
- Does the page remain usable if WebGL fails?
- Have performance characteristics been measured?

### Definition of Done

- [ ] Product content is complete.
- [ ] 3D viewer loads and works.
- [ ] Product controls behave correctly.
- [ ] Variant selection works.
- [ ] Product details are accessible.
- [ ] Responsive behavior is validated.
- [ ] Reduced-motion support is implemented.
- [ ] Non-3D fallback is functional.
- [ ] Assets are optimized.
- [ ] Performance is measured.
- [ ] No known critical defects remain.

---

## 18. Further Reading

- [Three.js Guide](../../3d-web/threejs.md)
- [React Three Fiber Guide](../../3d-web/react-three-fiber.md)
- [Shader Guide](../../3d-web/shaders.md)
- [3D Optimization Guide](../../3d-web/optimization.md)
- [GSAP Guide](../../animation/gsap.md)
- [Motion Guide](../../animation/motion.md)
- [Scroll Experiences](../../animation/scroll-experiences.md)
- [Component Architecture](../../design-systems/components.md)
- [Responsive Design](../../fundamentals/responsive-design.md)
- [Visual Review Workflow](../../agent-workflows/visual-review.md)
- [Optimization Workflow](../../agent-workflows/optimization.md)
- [3D Scene Builder Skill](../../skills/3d-scene-builder/SKILL.md)
- [Frontend Visual Audit Skill](../../skills/frontend-visual-audit/SKILL.md)

---

**Maintained by [AxomiyaIndie](https://github.com/axomiyaindie)**

This document is an implementation blueprint. AURORA ONE is fictional; its example product details and visual specifications are not verified commercial claims.