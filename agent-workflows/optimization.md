# AI Agent Optimization Workflow

Performance is a fundamental part of frontend engineering.

A visually impressive application can still provide a poor experience if it loads slowly, responds inconsistently, consumes excessive memory, or performs poorly on mobile devices.

AI coding agents should treat performance optimization as an evidence-driven engineering process.

The goal is not simply to make code smaller or achieve a higher benchmark score. The goal is to deliver fast, responsive, accessible, and reliable user experiences across supported devices.

This guide defines a systematic optimization workflow for modern frontend applications, React projects, interactive websites, and immersive 3D experiences.

## 1. Optimization Principles

### Measure before optimizing

Identify actual bottlenecks before changing code.

### Optimize user experience

Prioritize improvements that users can perceive.

### Preserve functionality

Performance improvements must not break application behavior.

### Avoid unnecessary complexity

Do not introduce additional dependencies, caching layers, or abstractions without a measurable reason.

### Optimize for real devices

A solution that works on a powerful desktop may perform poorly on a low-end mobile device.

### Verify every improvement

Measure performance before and after optimization whenever possible.

### Avoid premature optimization

Keep code maintainable and focus on demonstrated performance problems.

## 2. Understand the Performance Environment

Before optimizing an application, inspect its environment.

Identify:

- Framework and runtime.
- Build tool.
- Package manager.
- Application architecture.
- Rendering strategy.
- Existing dependencies.
- Hosting environment.
- API architecture.
- Asset delivery strategy.
- Supported browsers.
- Target devices.

Inspect the existing project before changing configuration.

Useful files may include:

- `package.json`
- Lockfiles.
- Build configuration.
- Framework configuration.
- Routing configuration.
- Image configuration.
- Deployment configuration.
- Existing performance reports.

Do not replace working infrastructure merely to introduce a preferred optimization tool.

## 3. Establish a Performance Baseline

Before making changes, record the current performance.

Evaluate:

- Initial page loading.
- Largest visible content rendering.
- Interaction responsiveness.
- Layout stability.
- JavaScript execution.
- Network requests.
- Image loading.
- Font loading.
- Memory consumption.
- Animation performance.

Use available tools such as:

- Chrome DevTools.
- Lighthouse.
- PageSpeed Insights.
- WebPageTest.
- Browser Performance API.
- Framework-specific profiling tools.

### Baseline report

Record:

```md
# Performance Baseline

## Environment
- Browser:
- Device:
- Viewport:
- Network conditions:
- Build mode:

## Metrics
- LCP:
- INP:
- CLS:
- Initial JavaScript:
- Total transferred assets:

## Observations
- Main bottlenecks:
- Slow resources:
- Rendering issues:
- Long-running tasks:

## Optimization priorities
1.
2.
3.
```

Record test conditions because different devices, networks, and environments produce different results.

Prefer production builds for meaningful performance measurements.

## 4. Understand Core Web Vitals

Core Web Vitals are important user-experience metrics.

The primary metrics are:

### Largest Contentful Paint (LCP)

Measures how quickly the largest visible content element renders.

Good target:

- Good: 2.5 seconds or less.
- Needs improvement: above 2.5 seconds and up to 4 seconds.
- Poor: above 4 seconds.

Common causes of poor LCP:

- Slow server responses.
- Large hero images.
- Render-blocking resources.
- Delayed font loading.
- Excessive client-side rendering.
- Slow image discovery.

Potential improvements:

- Improve server response time.
- Optimize the main content image.
- Avoid lazy-loading the actual LCP image.
- Use appropriate image formats.
- Preload critical assets when justified.
- Reduce render-blocking resources.
- Improve initial HTML delivery.

### Interaction to Next Paint (INP)

Measures interaction responsiveness throughout a page's lifetime.

Good target:

- Good: 200 milliseconds or less.
- Needs improvement: above 200 milliseconds and up to 500 milliseconds.
- Poor: above 500 milliseconds.

Common causes:

- Long JavaScript tasks.
- Expensive event handlers.
- Excessive React rendering.
- Large synchronous calculations.
- Heavy third-party scripts.
- Complex interactions.

Potential improvements:

- Reduce unnecessary JavaScript.
- Split long tasks.
- Defer nonessential work.
- Optimize event handlers.
- Avoid unnecessary state updates.
- Use appropriate scheduling and rendering techniques.

### Cumulative Layout Shift (CLS)

Measures unexpected visual movement during page loading and interaction.

Good target:

- Good: 0.1 or less.
- Needs improvement: above 0.1 and up to 0.25.
- Poor: above 0.25.

Common causes:

- Images without dimensions.
- Dynamically injected content.
- Late-loading advertisements.
- Unstable font rendering.
- Components that change size unexpectedly.

Potential improvements:

- Reserve image dimensions.
- Define aspect ratios.
- Reserve space for asynchronous content.
- Use stable layouts.
- Manage font loading carefully.

These thresholds describe the standard Core Web Vitals assessment targets. Evaluate field data at the 75th percentile where applicable.

Reference: [Web Vitals](https://web.dev/articles/vitals).

## 5. Optimize JavaScript and Bundle Size

Large JavaScript bundles can delay loading and increase execution costs.

Inspect:

- Initial bundle size.
- Dependency size.
- Duplicate packages.
- Unused code.
- Route-specific code.
- Third-party scripts.
- Large component imports.

### Code splitting

Load application features only when needed.

Example:

```jsx
import { lazy, Suspense } from "react";

const Dashboard = lazy(() => import("./Dashboard"));

function App() {
  return (
    <Suspense fallback={<p>Loading dashboard...</p>}>
      <Dashboard />
    </Suspense>
  );
}
```

Use route-level splitting where appropriate.

### Tree shaking

Prefer imports that allow the build tool to eliminate unused exports.

Avoid importing entire utility libraries when only a small function is required.

### Dependency management

Before adding a dependency:

1. Check whether the functionality already exists.
2. Evaluate package size.
3. Inspect maintenance and compatibility.
4. Consider native browser APIs.
5. Avoid duplicate dependencies.
6. Measure the actual bundle impact.

Do not remove useful dependencies solely because they increase bundle size slightly.

### Third-party scripts

Review analytics, tracking, chat widgets, embeds, and other external scripts.

Load noncritical scripts only when necessary.

Avoid allowing third-party code to block important application interactions.

## 6. Optimize Images and Media

Images are often among the largest resources downloaded by a webpage.

### Image optimization

Consider:

- WebP.
- AVIF.
- Appropriate JPEG or PNG usage.
- Responsive image sizes.
- Compression.
- Correct image dimensions.
- Modern image delivery services.

Example:

```html
<img
  src="/images/product-800.webp"
  srcset="
    /images/product-400.webp 400w,
    /images/product-800.webp 800w,
    /images/product-1200.webp 1200w
  "
  sizes="(max-width: 768px) 100vw, 50vw"
  width="1200"
  height="900"
  alt="Product preview"
  loading="lazy"
/>
```

Adjust dimensions, `sizes`, and loading strategy to the actual layout.

### Loading strategy

- Load important above-the-fold images promptly.
- Lazy-load images below the fold.
- Avoid lazy-loading the likely LCP image.
- Use explicit dimensions or aspect ratios.
- Avoid downloading unnecessarily large images.

### Video optimization

- Compress video assets.
- Use appropriate codecs and formats.
- Avoid autoplaying unnecessary video.
- Use poster images.
- Load video only when appropriate.
- Consider mobile data usage.

### Background images

Use responsive image delivery when large backgrounds are involved.

Avoid shipping desktop-sized backgrounds to small mobile screens without justification.

## 7. Optimize Fonts

Typography can affect loading performance and visual stability.

Review:

- Font file sizes.
- Number of font families.
- Number of weights.
- Variable font support.
- Font formats.
- Loading strategy.
- Fallback behavior.

Recommended practices:

- Prefer WOFF2 for modern web delivery.
- Avoid loading unused font weights.
- Use system fonts when suitable.
- Consider self-hosting when appropriate.
- Use `font-display` deliberately.
- Preload only genuinely critical fonts.

Example:

```css
@font-face {
  font-family: "Brand Sans";
  src: url("/fonts/brand-sans.woff2") format("woff2");
  font-display: swap;
  font-weight: 100 900;
}
```

The weight range shown is suitable for a variable font; use actual supported weights for static font files.

For multilingual applications, verify that the selected font supports every required script.

## 8. Optimize React Rendering

React applications can become inefficient when components render unnecessarily or perform expensive work repeatedly.

Inspect:

- Component rendering frequency.
- State ownership.
- Prop stability.
- Expensive calculations.
- Context updates.
- Large lists.
- Component boundaries.

### Keep state local

Avoid placing frequently changing state at the top of the entire application unless genuinely necessary.

Keep state close to the components that use it.

### Use memoization appropriately

React provides:

- `React.memo`.
- `useMemo`.
- `useCallback`.

Example:

```jsx
import { memo } from "react";

const ProductCard = memo(function ProductCard({ product }) {
  return (
    <article>
      <h2>{product.name}</h2>
      <p>{product.description}</p>
    </article>
  );
});
```

Memoization should be based on measured rendering behavior and appropriate component boundaries.

Do not wrap every component and function in memoization automatically.

### Optimize lists

For large lists:

- Avoid unnecessary rendering.
- Use stable keys.
- Consider pagination.
- Consider virtualization.
- Avoid expensive work inside render loops.

### Avoid unnecessary effects

Do not use effects for calculations that can happen during rendering.

Avoid state updates that create unnecessary rendering cycles.

Follow current React guidance for effect usage and component lifecycle behavior.

## 9. Optimize Rendering and Layout

Browser rendering includes:

1. Style calculation.
2. Layout.
3. Paint.
4. Compositing.

Expensive operations can make interfaces feel sluggish.

Review:

- DOM complexity.
- Layout recalculation.
- Large CSS selectors.
- Expensive visual effects.
- Repeated measurements.
- Forced synchronous layouts.
- Large paint areas.

### Avoid layout thrashing

Avoid repeatedly reading layout measurements and writing styles in alternating operations.

Group DOM reads and writes where imperative DOM work is necessary.

### Use transforms appropriately

For animation, prefer transform and opacity when they produce the intended visual result efficiently.

Example:

```css
.card {
  transition:
    transform 180ms ease,
    opacity 180ms ease;
}

.card:hover {
  transform: translateY(-4px);
}
```

Do not assume every transform is automatically inexpensive. Measure complex effects.

### Contain expensive sections

CSS containment may reduce the scope of layout and paint work.

Example:

```css
.widget {
  contain: layout paint;
}
```

Use containment only when its layout and rendering behavior is appropriate.

## 10. Optimize API and Network Performance

Network performance affects how quickly an application becomes useful.

Inspect:

- Number of requests.
- Response sizes.
- Request waterfalls.
- Server response times.
- Repeated API calls.
- Unnecessary polling.
- Duplicate requests.
- Error retries.

Potential improvements:

- Reduce unnecessary requests.
- Request only required data.
- Use pagination for large datasets.
- Cache appropriate responses.
- Parallelize independent requests.
- Avoid request waterfalls.
- Use compression.
- Use a suitable CDN.
- Keep API payloads efficient.

### Caching

Choose caching strategies based on data freshness and application requirements.

Consider:

- Browser caching.
- CDN caching.
- Application-level caching.
- Server-side caching.
- Framework data caching.
- Service worker caching.

Never cache private or user-specific data in a way that exposes it to other users.

Use correct cache-control policies and invalidation strategies.

### Avoid unnecessary polling

Use polling only when it is appropriate.

Consider server-sent events, WebSockets, or other event-driven approaches when the product genuinely requires real-time updates.

Do not introduce additional infrastructure without a clear need.

## 11. Optimize Loading Experience

A fast application should also communicate loading progress clearly.

Consider:

- Skeleton screens.
- Loading indicators.
- Progressive rendering.
- Route-level loading states.
- Optimistic updates.
- Meaningful error states.
- Retry behavior.

Avoid replacing an entire page with a spinner when only one section is loading.

Reserve layout space for asynchronous content to reduce visual movement.

## 12. Optimize Caching and Asset Delivery

Static assets should be delivered efficiently.

Review:

- Cache headers.
- Asset versioning.
- Compression.
- CDN configuration.
- Immutable asset naming.
- HTML caching.
- API caching.

Hashed assets can generally use long-lived immutable caching.

Example:

```http
Cache-Control: public, max-age=31536000, immutable
```

Use this strategy only for versioned assets whose content changes when the filename changes.

HTML documents and dynamic API responses require different caching policies.

## 13. Optimize Animations

Animations should remain smooth without consuming unnecessary resources.

Inspect:

- Animation duration.
- Frame rate.
- Number of animated elements.
- JavaScript animation workload.
- Scroll event handling.
- Layout-triggering properties.
- Off-screen animations.

Recommended practices:

- Prefer transform and opacity where suitable.
- Avoid animating expensive layout properties unnecessarily.
- Stop or reduce off-screen animation work.
- Respect reduced-motion preferences.
- Clean up animation instances.
- Avoid duplicate animation loops.
- Profile complex sequences.

For GSAP and Motion projects, use the library's recommended lifecycle and cleanup patterns.

Related guides:

- [GSAP](../animation/gsap.md)
- [Motion](../animation/motion.md)
- [Scroll Experiences](../animation/scroll-experiences.md)

## 14. Optimize Three.js and WebGL

3D experiences require additional optimization because rendering can place significant demands on the GPU and memory.

### Geometry

- Reuse geometries.
- Reduce unnecessary polygon counts.
- Use instancing for repeated objects.
- Consider level of detail.
- Avoid excessive object counts.

### Materials

- Reuse materials where appropriate.
- Avoid unnecessary shader complexity.
- Reduce expensive transparency.
- Limit unnecessary material variations.

### Textures

- Resize textures to appropriate dimensions.
- Compress textures where supported.
- Use appropriate texture formats.
- Avoid unnecessarily large texture atlases.
- Monitor GPU memory.

### Lighting and shadows

- Reduce unnecessary shadow-casting lights.
- Limit shadow map resolution.
- Avoid excessive real-time shadow calculations.
- Bake lighting where appropriate.
- Profile expensive lighting setups.

### Draw calls

Excessive draw calls can reduce rendering performance.

Consider:

- Instanced rendering.
- Geometry merging when appropriate.
- Material reuse.
- Scene simplification.
- Efficient batching.

### Post-processing

Post-processing effects can increase GPU workload.

Review:

- Bloom.
- Depth of field.
- Ambient occlusion.
- Motion blur.
- Multiple render passes.
- Resolution scaling.

Keep only effects that meaningfully improve the experience.

### Renderer resolution

Device pixel ratio can significantly affect GPU workload.

Example:

```jsx
<Canvas dpr={[1, 1.5]}>
  {/* 3D scene */}
</Canvas>
```

Choose suitable limits based on visual requirements and device performance.

Do not assume that the highest available pixel ratio is always desirable.

## 15. Optimize React Three Fiber

React Three Fiber applications should follow both React and Three.js optimization principles.

Inspect:

- Component mounting.
- Scene updates.
- Frame-loop operations.
- Object allocation.
- Geometry reuse.
- Material reuse.
- Event handling.
- Resource disposal.

### Avoid unnecessary React state updates in the render loop

Use frame-loop mechanisms for continuous visual updates rather than triggering React state updates on every frame.

Example:

```jsx
import { useRef } from "react";
import { useFrame } from "@react-three/fiber";

function RotatingObject() {
  const meshRef = useRef();

  useFrame((_, delta) => {
    if (meshRef.current) {
      meshRef.current.rotation.y += delta * 0.5;
    }
  });

  return (
    <mesh ref={meshRef}>
      <boxGeometry />
      <meshStandardMaterial />
    </mesh>
  );
}
```

### Reuse resources

Avoid creating new geometries, materials, and other expensive objects unnecessarily.

Understand resource ownership and disposal behavior before manually disposing shared resources.

### Demand rendering

For mostly static scenes, consider demand-based rendering where appropriate.

This can reduce unnecessary rendering when the scene is not changing.

However, continuous animation, controls, and external updates may require a different rendering strategy.

### Monitor scene complexity

Measure:

- Draw calls.
- Triangles.
- Texture memory.
- Frame time.
- Renderer information.

Optimize the actual bottleneck rather than reducing every scene element indiscriminately.

Related guides:

- [Three.js](../3d-web/threejs.md)
- [React Three Fiber](../3d-web/react-three-fiber.md)
- [3D Optimization](../3d-web/optimization.md)

## 16. Optimize for Mobile and Low-End Devices

Mobile devices often have more limited CPU, GPU, memory, and network resources.

Review:

- JavaScript execution.
- Image payloads.
- Font payloads.
- 3D complexity.
- Animation workload.
- Touch responsiveness.
- Memory usage.
- Battery consumption.

Consider:

- Lower-resolution 3D assets.
- Reduced shadow quality.
- Adaptive rendering quality.
- Simplified effects.
- Responsive image sources.
- Smaller JavaScript payloads.
- Reduced animation complexity.
- Graceful fallbacks.

Do not disable important functionality on mobile without a product requirement.

## 17. Optimize Accessibility Alongside Performance

Optimization should not reduce accessibility.

Avoid:

- Removing meaningful loading feedback.
- Hiding content to improve benchmark scores.
- Disabling keyboard interactions.
- Reducing text readability.
- Ignoring reduced-motion preferences.
- Removing semantic markup.
- Using inaccessible custom controls.

Ensure that lazy-loaded content remains accessible and that performance improvements preserve the intended interaction model.

## 18. Performance Profiling Tools

Use tools appropriate to the project.

| Tool | Primary purpose |
|---|---|
| Chrome DevTools | Runtime, network and rendering inspection |
| Lighthouse | Performance and quality audits |
| PageSpeed Insights | Field and lab performance insights |
| WebPageTest | Detailed page-loading analysis |
| React DevTools Profiler | React component rendering |
| Bundle analyzers | JavaScript bundle analysis |
| Three.js renderer statistics | 3D rendering diagnostics |

Useful resources:

- [Chrome DevTools](https://developer.chrome.com/docs/devtools/)
- [Lighthouse](https://developer.chrome.com/docs/lighthouse/)
- [PageSpeed Insights](https://pagespeed.web.dev/)
- [WebPageTest](https://www.webpagetest.org/)
- [React Profiler](https://react.dev/reference/react/Profiler)
- [Three.js Documentation](https://threejs.org/docs/)

Tool availability depends on the agent's environment.

Do not report measurements from tools that were not actually run.

## 19. Optimization Workflow

Follow a repeatable optimization cycle.

### Step 1: Inspect

Understand the application architecture, dependencies, and rendering behavior.

### Step 2: Measure

Establish a baseline under documented conditions.

### Step 3: Identify

Locate the most important bottlenecks.

### Step 4: Prioritize

Rank improvements by user impact, engineering effort, and risk.

### Step 5: Implement

Make focused changes without unnecessarily rewriting working systems.

### Step 6: Validate

Run relevant tests and verify that functionality remains intact.

### Step 7: Measure again

Compare results against the original baseline under comparable conditions.

### Step 8: Document

Record improvements, regressions, limitations, and remaining work.

## 20. Optimization Priority Framework

Use the following order as a general starting point:

1. Fix broken functionality and severe responsiveness problems.
2. Improve slow server responses and critical resource loading.
3. Optimize the LCP element and initial rendering.
4. Reduce unnecessary JavaScript and expensive execution.
5. Fix layout instability.
6. Improve interaction responsiveness.
7. Optimize images, fonts, and media.
8. Improve repeated rendering and expensive animations.
9. Optimize 3D rendering and GPU workload.
10. Apply smaller refinements.

The correct priority depends on measured evidence.

Do not optimize a small decorative icon while the primary page content takes several seconds to load.

## 21. Performance Optimization Report

Document significant optimization work.

Example:

```md
# Performance Optimization Report

## Project
Application name:

## Environment
- Browser:
- Device:
- Build mode:
- Network conditions:

## Baseline
- LCP:
- INP:
- CLS:
- Bundle size:
- Initial loading time:

## Identified Bottlenecks
1.
2.
3.

## Changes Implemented
1.
2.
3.

## Results
- LCP before / after:
- INP before / after:
- CLS before / after:
- Bundle size before / after:

## Validation
- Build:
- Tests:
- Responsive review:
- Functional regression:

## Remaining Issues
1.
2.

## Limitations
Document unavailable tools, untested devices, and measurement constraints.
```

Use consistent measurement conditions when comparing before and after results.

Do not invent performance scores or improvements.

## 22. Common Optimization Mistakes

Avoid these practices:

- Optimizing without measuring.
- Adding dependencies for trivial improvements.
- Memoizing every React component.
- Lazy-loading critical above-the-fold content.
- Preloading too many resources.
- Compressing images until they become visibly poor.
- Removing animations without considering the design.
- Disabling useful functionality on mobile.
- Adding caching without an invalidation strategy.
- Reducing 3D quality without checking the actual bottleneck.
- Reporting Lighthouse scores without recording test conditions.
- Optimizing development mode instead of the production build.
- Claiming field performance improvements based only on a local benchmark.

## 23. AI Agent Optimization Checklist

### Before optimization

- [ ] Project architecture inspected.
- [ ] Dependencies reviewed.
- [ ] Production build configuration understood.
- [ ] Performance baseline recorded.
- [ ] Main bottlenecks identified.
- [ ] Optimization priorities established.

### Frontend performance

- [ ] JavaScript bundle reviewed.
- [ ] Unnecessary dependencies investigated.
- [ ] Code splitting considered.
- [ ] Images optimized.
- [ ] Fonts optimized.
- [ ] API requests reviewed.
- [ ] Caching strategy evaluated.
- [ ] Rendering costs investigated.

### React performance

- [ ] Component rendering inspected.
- [ ] State ownership reviewed.
- [ ] Expensive calculations identified.
- [ ] Large lists evaluated.
- [ ] Effects reviewed.
- [ ] Memoization used only where justified.

### Animation and 3D

- [ ] Animation workload inspected.
- [ ] Reduced motion supported.
- [ ] Geometry and materials reviewed.
- [ ] Texture sizes evaluated.
- [ ] Draw calls investigated.
- [ ] GPU workload considered.
- [ ] Mobile rendering evaluated.
- [ ] Resources cleaned up appropriately.

### Validation

- [ ] Production build succeeds.
- [ ] Relevant tests pass.
- [ ] Core functionality remains intact.
- [ ] Responsive behavior reviewed.
- [ ] Performance measured again.
- [ ] Regressions investigated.
- [ ] Results documented honestly.

## 24. Definition of Done

Optimization work is complete when:

1. The original bottlenecks have been identified.
2. Performance measurements have been collected where tools permit.
3. Changes address real problems.
4. Existing functionality remains intact.
5. Accessibility has been preserved.
6. Responsive behavior remains correct.
7. Relevant tests and production builds have been checked.
8. Performance improvements have been measured where possible.
9. Regressions and trade-offs have been documented.
10. The final report accurately represents the work performed.

Performance engineering is an ongoing process. The best implementation is not necessarily the one with the smallest bundle or highest benchmark score. It is the one that delivers a fast, reliable, accessible, and enjoyable experience while remaining maintainable.

---

## Related Guides

- [AI Agent Planning Workflow](./planning.md)
- [AI Agent Implementation Workflow](./implementation.md)
- [AI Agent Visual Review Workflow](./visual-review.md)
- [Frontend Architecture](../fundamentals/frontend-architecture.md)
- [Responsive Design](../fundamentals/responsive-design.md)
- [3D Optimization](../3d-web/optimization.md)
- [React Three Fiber](../3d-web/react-three-fiber.md)
- [GSAP](../animation/gsap.md)
- [Motion](../animation/motion.md)
- [Frontend Visual Audit Skill](../skills/frontend-visual-audit/SKILL.md)