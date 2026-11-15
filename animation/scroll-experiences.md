# Scroll Experiences: Immersive Web Interactions

Scroll experiences transform ordinary page navigation into interactive visual storytelling.

Instead of treating scrolling only as a way to move through content, modern websites can use scroll position to control animation, reveal information, transition between scenes, and create immersive product presentations.

Scroll-driven experiences are commonly used for:

- Premium landing pages.
- Product storytelling.
- Interactive portfolios.
- Editorial websites.
- Product demonstrations.
- 3D product showcases.
- Creative agency websites.
- Long-form visual narratives.
- Interactive data presentations.

This guide establishes practical engineering principles for developers and AI coding agents building scroll-driven web experiences.

## 1. Understanding Scroll Experiences

Scroll experiences use the user's scroll position or viewport movement to control visual and interactive behavior.

There are two fundamental approaches.

### Scroll-triggered animation

An animation starts when an element enters or leaves a particular viewport position.

Examples:

- A heading fades into view.
- A card moves upward when it becomes visible.
- An image reveals itself.
- A section begins an entrance sequence.

### Scroll-linked animation

Animation progress is continuously connected to scroll progress.

Examples:

- A product rotates as the user scrolls.
- An image gradually scales.
- A progress indicator follows page position.
- A 3D camera moves through a scene.
- A horizontal presentation advances with vertical scrolling.

These approaches can be combined to create sophisticated interactive websites.

## 2. Choosing the Right Technology

Several technologies can power scroll experiences.

| Technology | Best suited for |
|---|---|
| GSAP ScrollTrigger | Complex timelines, pinning, scrubbed animation |
| Motion | React component animation and scroll-linked values |
| Lenis | Smooth scrolling behavior |
| React Three Fiber | Interactive 3D scenes |
| Three.js | Custom 3D rendering |
| CSS Scroll-Driven Animations | Native CSS-based scroll effects |
| Intersection Observer | Viewport visibility detection |

Choose technologies according to the requirements.

Do not install several animation libraries when one can solve the problem.

## 3. Planning a Scroll Experience

Before writing animation code, understand the content and desired behavior.

Define:

1. The purpose of the experience.
2. The content sequence.
3. The sections involved.
4. The scroll interaction model.
5. The animation states.
6. The visual transitions.
7. The mobile behavior.
8. The accessibility requirements.
9. The performance budget.
10. The fallback experience.

A useful planning structure:

| Section | Content | Scroll behavior |
|---|---|---|
| Hero | Main message | Initial entrance |
| Introduction | Product overview | Fade and reveal |
| Features | Key benefits | Staggered transitions |
| Product showcase | Main product | Pinned presentation |
| Details | Supporting information | Scroll-linked animation |
| Final CTA | Conversion action | Subtle entrance |

Every scroll effect should support the information being communicated.

Avoid making the user scroll through long decorative animations just to reach important content.

## 4. GSAP ScrollTrigger Fundamentals

GSAP ScrollTrigger is a powerful solution for advanced scroll interactions.

Installation:

```bash
npm install gsap
```

Import and register:

```js
import { gsap } from "gsap";
import { ScrollTrigger } from "gsap/ScrollTrigger";

gsap.registerPlugin(ScrollTrigger);
```

Basic example:

```js
gsap.from(".feature-card", {
  opacity: 0,
  y: 60,
  duration: 0.8,
  scrollTrigger: {
    trigger: ".feature-section",
    start: "top 80%",
    toggleActions: "play none none reverse"
  }
});
```

The animation starts when the trigger reaches the configured viewport position.

### Important ScrollTrigger properties

| Property | Purpose |
|---|---|
| `trigger` | Element controlling the trigger |
| `start` | Start position |
| `end` | End position |
| `scrub` | Connect animation progress to scroll |
| `pin` | Keep an element fixed during a scroll interval |
| `markers` | Visual debugging markers |
| `toggleActions` | Define playback behavior |
| `onEnter` | Callback when entering |
| `onLeave` | Callback when leaving |
| `onUpdate` | Callback during progress changes |
| `invalidateOnRefresh` | Recalculate dynamic values on refresh |

Use markers during development and remove them before production.

## 5. Scroll-Triggered Reveals

Section reveals are among the most common scroll interactions.

```js
gsap.utils.toArray(".reveal").forEach((element) => {
  gsap.from(element, {
    opacity: 0,
    y: 40,
    duration: 0.8,
    ease: "power3.out",
    scrollTrigger: {
      trigger: element,
      start: "top 85%",
      toggleActions: "play none none reverse"
    }
  });
});
```

Useful reveal patterns:

- Fade-up.
- Fade-down.
- Scale-in.
- Image masks.
- Text reveals.
- Staggered cards.
- Section transitions.

### Best practices

- Use consistent timing.
- Keep distances reasonable.
- Avoid hiding important content indefinitely.
- Avoid excessive repetition.
- Test content when JavaScript is unavailable.
- Ensure animations do not interfere with reading.

For critical content, prefer a visible default state and enhance it with animation rather than making visibility depend entirely on successful animation initialization.

## 6. Scrubbed Scroll Animation

Scrubbing connects an animation timeline to scroll progress.

```js
gsap.to(".product", {
  scale: 1.2,
  rotation: 8,
  scrollTrigger: {
    trigger: ".product-section",
    start: "top bottom",
    end: "bottom top",
    scrub: true
  }
});
```

With `scrub: true`, animation progress follows the scroll position.

A numeric scrub value adds smoothing:

```js
scrollTrigger: {
  trigger: ".section",
  start: "top top",
  end: "+=1000",
  scrub: 1
}
```

Use scrubbed animations for:

- Product transformations.
- Image scaling.
- Visual storytelling.
- 3D camera movement.
- Scene transitions.
- Horizontal presentations.

Scrubbing should feel connected to user input rather than delayed or unpredictable.

## 7. Pinned Scroll Sections

Pinning holds an element in place while the page continues scrolling.

```js
gsap.to(".showcase-content", {
  opacity: 1,
  scrollTrigger: {
    trigger: ".showcase-section",
    start: "top top",
    end: "+=1200",
    pin: true,
    scrub: 1
  }
});
```

Pinned sections are useful for:

- Product showcases.
- Feature demonstrations.
- Step-by-step storytelling.
- Interactive diagrams.
- 3D presentations.

### Pinning considerations

- Ensure the section has sufficient scroll distance.
- Avoid unexpectedly changing document flow.
- Check nested scroll containers.
- Test different viewport heights.
- Avoid excessive pinned sections.
- Verify mobile behavior.
- Ensure content remains reachable.

Pinning should be used selectively. Too many pinned sections can make navigation frustrating.

## 8. Horizontal Scroll Experiences

Horizontal scrolling can be implemented using vertical scroll input.

Example:

```js
const panels = gsap.utils.toArray(".panel");

gsap.to(panels, {
  xPercent: -100 * (panels.length - 1),
  ease: "none",
  scrollTrigger: {
    trigger: ".horizontal-section",
    pin: true,
    scrub: 1,
    end: () =>
      `+=${window.innerWidth * (panels.length - 1)}`
  }
});
```

This is a simplified pattern.

Production implementations should account for:

- Actual panel widths.
- Container width.
- Responsive layouts.
- Content overflow.
- Scroll distance.
- Refresh behavior.
- Reduced-motion preferences.
- Touch interactions.

Do not assume every horizontal presentation should behave identically on mobile.

An alternative is to provide a native horizontally scrollable container on smaller screens.

## 9. Parallax Scrolling

Parallax creates a sense of depth by moving visual layers at different speeds.

Common elements include:

- Background images.
- Foreground objects.
- Decorative shapes.
- Typography.
- Product imagery.
- 3D elements.

Example:

```js
gsap.to(".parallax-image", {
  yPercent: -20,
  ease: "none",
  scrollTrigger: {
    trigger: ".parallax-section",
    start: "top bottom",
    end: "bottom top",
    scrub: true
  }
});
```

### Layered parallax

Different layers can use different movement values.

```js
gsap.to(".background-layer", {
  yPercent: -10,
  scrollTrigger: {
    trigger: ".scene",
    scrub: true
  }
});

gsap.to(".foreground-layer", {
  yPercent: -30,
  scrollTrigger: {
    trigger: ".scene",
    scrub: true
  }
});
```

The foreground moves faster, creating a sense of depth.

### Parallax best practices

- Keep movement subtle.
- Avoid excessive screen movement.
- Ensure content remains readable.
- Avoid unnecessary full-screen layers.
- Respect reduced-motion preferences.
- Test on mobile devices.

Parallax should support visual hierarchy rather than distract from the content.

## 10. Text and Typography Storytelling

Scroll-driven text animation can create a structured narrative.

Possible techniques:

- Line-by-line reveals.
- Word-by-word entrances.
- Highlighted text.
- Sequential paragraphs.
- Sticky editorial headings.
- Animated counters.

Example:

```js
gsap.from(".story-heading", {
  opacity: 0,
  y: 50,
  scrollTrigger: {
    trigger: ".story-section",
    start: "top 80%",
    toggleActions: "play none none reverse"
  }
});
```

For more advanced text effects, combine GSAP with an appropriate text-splitting solution.

Preserve accessible text content and avoid making reading dependent on animation completion.

## 11. Image Reveal Effects

Image masks and clipping can produce polished transitions.

Example using CSS clip-path:

```js
gsap.fromTo(
  ".image-reveal",
  {
    clipPath: "inset(0 100% 0 0)"
  },
  {
    clipPath: "inset(0 0% 0 0)",
    duration: 1.2,
    ease: "power3.inOut",
    scrollTrigger: {
      trigger: ".image-section",
      start: "top 80%"
    }
  }
);
```

Possible techniques:

- Horizontal reveals.
- Vertical reveals.
- Circular masks.
- Scale transitions.
- Layered image entrances.
- Background image movement.

Profile expensive effects and test their visual output across target browsers.

## 12. Motion for React Scroll Animations

Motion provides declarative APIs for scroll-triggered and scroll-linked interactions.

Install:

```bash
npm install motion
```

Import:

```jsx
import {
  motion,
  useScroll,
  useTransform
} from "motion/react";
```

### whileInView

Animate an element when it enters the viewport.

```jsx
<motion.section
  initial={{
    opacity: 0,
    y: 40
  }}
  whileInView={{
    opacity: 1,
    y: 0
  }}
  viewport={{
    once: true,
    amount: 0.3
  }}
>
  Section Content
</motion.section>
```

### useScroll

Track page scroll progress.

```jsx
function ProgressBar() {
  const { scrollYProgress } = useScroll();

  return (
    <motion.div
      style={{
        scaleX: scrollYProgress,
        transformOrigin: "0% 50%"
      }}
      className="progress-bar"
    />
  );
}
```

### Element-based progress

```jsx
const { scrollYProgress } = useScroll({
  target: sectionRef,
  offset: ["start end", "end start"]
});
```

### useTransform

Map scroll progress to another value.

```jsx
const y = useTransform(
  scrollYProgress,
  [0, 1],
  [100, -100]
);
```

Apply it to a motion component:

```jsx
<motion.div style={{ y }}>
  Parallax Content
</motion.div>
```

Motion is particularly useful when scroll behavior belongs to React components.

## 13. Scroll-Controlled 3D Experiences

Scroll-controlled 3D experiences connect page movement to a Three.js or React Three Fiber scene.

This technique is especially useful for product presentations and immersive storytelling.

Possible interactions:

- Camera movement.
- Object rotation.
- Model scaling.
- Scene transitions.
- Lighting changes.
- Material changes.
- Environment transitions.
- Sequential product reveals.

### React Three Fiber architecture

A typical structure:

```text
src/
├── components/
│   ├── Experience/
│   │   ├── Experience.jsx
│   │   ├── CameraRig.jsx
│   │   └── ProductModel.jsx
│   └── ScrollSections/
│       ├── Intro.jsx
│       ├── Features.jsx
│       └── FinalSection.jsx
├── hooks/
│   └── useScrollProgress.js
└── pages/
    └── ProductPage.jsx
```

Separate the 3D scene from the DOM storytelling interface.

### Using Drei ScrollControls

Drei provides `ScrollControls` and `useScroll` for scroll-aware R3F experiences.

```jsx
import {
  ScrollControls,
  Scroll,
  useScroll
} from "@react-three/drei";
```

Example:

```jsx
function SceneContent() {
  const scroll = useScroll();

  useFrame((state, delta) => {
    const progress = scroll.offset;

    state.camera.position.z = 5 - progress * 2;
  });

  return <ProductModel />;
}

function Experience() {
  return (
    <Canvas>
      <ScrollControls pages={3} damping={0.2}>
        <SceneContent />

        <Scroll html>
          <section className="intro">
            Product Introduction
          </section>

          <section className="features">
            Product Features
          </section>

          <section className="conclusion">
            Explore More
          </section>
        </Scroll>
      </ScrollControls>
    </Canvas>
  );
}
```

This is an architectural example rather than a complete production implementation.

Important considerations:

- Keep DOM and WebGL responsibilities separate.
- Avoid unnecessary React state updates every frame.
- Use refs for imperative object updates.
- Keep camera movement predictable.
- Optimize models and textures.
- Provide a mobile fallback.
- Respect reduced-motion preferences.
- Test real-device performance.

### Scroll progress and camera movement

For simple linear movement:

```js
camera.position.z = startZ + progress * distance;
```

For more complex motion, use interpolation or a timeline to define key camera states.

Avoid sudden camera jumps.

A camera path should be visually coherent and should preserve important object visibility.

## 14. Combining GSAP with React Three Fiber

GSAP can animate Three.js objects and camera properties.

Example:

```jsx
import { useRef } from "react";
import { useGSAP } from "@gsap/react";
import gsap from "gsap";

function ProductScene() {
  const groupRef = useRef();

  useGSAP(() => {
    gsap.to(groupRef.current.rotation, {
      y: Math.PI * 2,
      duration: 4,
      ease: "none",
      repeat: -1
    });
  }, { scope: groupRef });

  return (
    <group ref={groupRef}>
      <ProductModel />
    </group>
  );
}
```

For scroll-controlled animation, GSAP can target object properties using a ScrollTrigger timeline.

Use the appropriate lifecycle context to manage cleanup.

Avoid having GSAP and `useFrame()` continuously overwrite the same object properties.

Assign clear ownership of animated properties to prevent conflicting updates.

## 15. Smooth Scrolling with Lenis

Lenis is a smooth scrolling library designed for controlled scrolling experiences.

It can be useful for:

- Editorial websites.
- Long-form storytelling.
- Creative portfolios.
- Scroll-driven presentations.
- Smooth visual transitions.

Installation:

```bash
npm install lenis
```

Basic setup:

```js
import Lenis from "lenis";

const lenis = new Lenis();

function raf(time) {
  lenis.raf(time);
  requestAnimationFrame(raf);
}

requestAnimationFrame(raf);
```

This example demonstrates the basic animation-frame integration.

A production application must manage the animation loop lifecycle and avoid creating multiple active Lenis instances.

### React integration

Lenis can be initialized through a React effect or a dedicated provider.

Important practices:

- Initialize once for the intended scrolling context.
- Destroy the instance during cleanup.
- Avoid duplicate animation loops.
- Coordinate with ScrollTrigger when necessary.
- Test browser history and anchor navigation.
- Test touch scrolling.
- Respect reduced-motion preferences.

Official documentation:

[Lenis Documentation](https://github.com/darkroomengineering/lenis)

### Lenis and GSAP integration

Lenis and ScrollTrigger can work together.

Example:

```js
import Lenis from "lenis";
import gsap from "gsap";
import { ScrollTrigger } from "gsap/ScrollTrigger";

gsap.registerPlugin(ScrollTrigger);

const lenis = new Lenis();

lenis.on("scroll", ScrollTrigger.update);

gsap.ticker.add((time) => {
  lenis.raf(time * 1000);
});

gsap.ticker.lagSmoothing(0);
```

This is a common integration pattern.

When using it:

- Ensure there is only one scroll-driving animation loop.
- Remove listeners during cleanup.
- Remove the ticker callback when the integration is destroyed.
- Test pinning and refresh behavior.
- Avoid combining incompatible scroll implementations.

Do not run a second independent `requestAnimationFrame` loop for the same Lenis instance.

## 16. Native CSS Scroll-Driven Animations

Modern CSS includes scroll-driven animation capabilities.

These can be useful when an effect does not require a JavaScript animation library.

Example:

```css
@keyframes reveal {
  from {
    opacity: 0;
    transform: translateY(30px);
  }

  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.reveal {
  animation: reveal linear both;
  animation-timeline: view();
  animation-range: entry 0% entry 80%;
}
```

CSS scroll timelines can reduce JavaScript complexity for suitable effects.

Browser support varies, so verify support for the target browsers.

Provide a sensible static state or fallback when the feature is unavailable.

Official reference:

[MDN: CSS Scroll-Driven Animations](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_scroll-driven_animations)

## 17. Scroll Progress Indicators

A progress indicator can communicate the user's position within a long page.

### GSAP example

```js
gsap.to(".progress-bar", {
  scaleX: 1,
  transformOrigin: "left",
  ease: "none",
  scrollTrigger: {
    trigger: document.documentElement,
    start: "top top",
    end: "bottom bottom",
    scrub: true
  }
});
```

### Motion example

```jsx
function ProgressBar() {
  const { scrollYProgress } = useScroll();

  return (
    <motion.div
      className="progress-bar"
      style={{ scaleX: scrollYProgress }}
    />
  );
}
```

Keep the indicator subtle and ensure it does not obscure page content.

## 18. Responsive Scroll Experiences

Desktop scroll experiences do not automatically translate well to mobile.

Mobile devices have:

- Smaller viewports.
- Touch-driven scrolling.
- Different viewport heights.
- Limited GPU resources.
- Variable performance.
- Different input expectations.

Recommended strategies:

### Desktop

- Use complex pinned presentations when justified.
- Support larger visual scenes.
- Use controlled parallax.
- Use richer 3D camera movement when performance permits.

### Mobile

- Reduce the number of pinned sections.
- Simplify parallax.
- Reduce 3D complexity.
- Prefer shorter transitions.
- Avoid unnecessary scroll hijacking.
- Provide native scrolling alternatives.
- Reduce rendering resolution when needed.

Use responsive breakpoints intentionally.

Do not simply shrink the desktop experience to fit a smaller screen.

## 19. Accessibility and Reduced Motion

Scroll-driven experiences can introduce accessibility problems when they rely too heavily on motion.

Important principles:

- Respect `prefers-reduced-motion`.
- Keep essential content available without animation.
- Preserve normal reading order.
- Avoid forced scrolling.
- Avoid excessive parallax.
- Keep keyboard navigation functional.
- Maintain visible focus indicators.
- Do not hide information behind scroll interactions.
- Avoid disorienting camera movement.
- Provide alternatives for complex 3D presentations.

### Reduced-motion CSS

```css
@media (prefers-reduced-motion: reduce) {
  .parallax-layer {
    transform: none !important;
  }

  .animated-element {
    animation: none !important;
    transition: none !important;
  }
}
```

### Reduced-motion JavaScript

```js
const prefersReducedMotion = window.matchMedia(
  "(prefers-reduced-motion: reduce)"
).matches;
```

When reduced motion is requested:

- Disable nonessential parallax.
- Avoid large camera movements.
- Replace complex transitions with simple state changes.
- Remove unnecessary smooth scrolling.
- Keep content immediately accessible.

Reduced motion should not remove functionality.

## 20. Performance Optimization

Scroll experiences can become expensive because multiple animation systems may update continuously.

### Prefer efficient properties

Use transforms and opacity when appropriate.

Avoid excessive animation of layout-affecting properties.

### Limit simultaneous effects

Avoid combining too many expensive effects:

- Large blur filters.
- Multiple full-screen overlays.
- Heavy post-processing.
- Excessive shadows.
- Large numbers of animated elements.

### Optimize 3D scenes

- Reduce polygon counts.
- Compress textures.
- Reuse geometry and materials.
- Use instancing where appropriate.
- Limit real-time shadows.
- Avoid unnecessary rendering.
- Use adaptive quality.

### Manage event and animation lifecycles

- Clean up ScrollTriggers.
- Destroy Lenis instances.
- Remove event listeners.
- Avoid duplicate animation loops.
- Prevent stale component references.
- Refresh measurements after relevant layout changes.

### Avoid unnecessary scroll handlers

Prefer established APIs such as ScrollTrigger, Motion's scroll hooks, Intersection Observer, or CSS scroll timelines instead of manually performing expensive DOM calculations on every scroll event.

## 21. Debugging Scroll Experiences

### ScrollTrigger starts at the wrong position

Check:

- Trigger element dimensions.
- Start and end values.
- Layout changes.
- Font loading.
- Image loading.
- Pin spacing.
- Scroll container configuration.

Use:

```js
ScrollTrigger.refresh();
```

when significant layout changes require recalculating trigger positions.

### Horizontal scroll overflows

Check:

- Container dimensions.
- Panel widths.
- Translation distance.
- Responsive breakpoints.
- Overflow behavior.

### 3D scene becomes disconnected from scroll

Check:

- Scroll source.
- Animation frame updates.
- Scroll progress calculation.
- Camera references.
- Competing animation systems.
- Canvas and DOM positioning.

### Smooth scrolling behaves incorrectly

Check:

- Duplicate animation loops.
- Multiple Lenis instances.
- ScrollTrigger synchronization.
- Cleanup.
- Browser history.
- Touch behavior.

### Mobile layout breaks

Check:

- Viewport height.
- Pinned section dimensions.
- Horizontal overflow.
- Touch interactions.
- Dynamic browser UI.
- Reduced-motion behavior.

Test actual devices whenever possible.

## 22. AI Coding Agent Workflow

AI coding agents should follow a structured process when implementing immersive scroll experiences.

### Before implementation

- Inspect the existing frontend stack.
- Understand the page content.
- Identify the intended narrative.
- Determine which sections need animation.
- Choose GSAP, Motion, CSS, or a combination.
- Identify whether Lenis is genuinely necessary.
- Identify 3D scene requirements.
- Define mobile behavior.
- Define accessibility requirements.

### During implementation

- Build semantic page structure first.
- Add static content before animation.
- Implement basic interactions.
- Add scroll-triggered effects.
- Add scroll-linked effects where justified.
- Implement pinned or horizontal sections selectively.
- Integrate 3D scenes only when they add value.
- Keep animation lifecycle management explicit.
- Support reduced motion.

### During visual review

- Verify section transitions.
- Check scroll timing.
- Check pinning behavior.
- Review parallax intensity.
- Test horizontal sections.
- Check mobile navigation.
- Validate text readability.
- Inspect 3D camera movement.
- Test keyboard interaction.
- Review reduced-motion behavior.

### Before completion

- Confirm production build succeeds.
- Check console errors.
- Verify ScrollTrigger cleanup.
- Verify Lenis cleanup if used.
- Test responsive behavior.
- Test performance.
- Verify essential content is accessible.
- Document any known limitations.

Never add complex scroll effects simply to imitate a reference without understanding their effect on usability.

## 23. Production Checklist

### Experience planning

- [ ] Scroll behavior supports the content.
- [ ] Section sequence is clearly defined.
- [ ] Animation states are documented.
- [ ] Mobile behavior is planned.
- [ ] Accessibility requirements are defined.

### Implementation

- [ ] Correct animation technology is selected.
- [ ] ScrollTrigger or Motion is configured correctly.
- [ ] Pinning is used selectively.
- [ ] Horizontal scrolling is responsive.
- [ ] Parallax is subtle.
- [ ] 3D scenes are integrated cleanly.
- [ ] Smooth scrolling is added only when justified.

### Performance

- [ ] Animation loops are not duplicated.
- [ ] Event listeners are cleaned up.
- [ ] ScrollTriggers are managed.
- [ ] 3D assets are optimized.
- [ ] Expensive visual effects are limited.
- [ ] Mobile performance is tested.

### Accessibility

- [ ] Reduced-motion preferences are respected.
- [ ] Content remains accessible without animation.
- [ ] Keyboard navigation works.
- [ ] Normal scrolling remains usable.
- [ ] Essential actions are not motion-dependent.

### Validation

- [ ] Desktop experience is tested.
- [ ] Mobile experience is tested.
- [ ] Different viewport heights are tested.
- [ ] Browser console is checked.
- [ ] Scroll behavior is validated.
- [ ] Production build succeeds.

## 24. Further Learning

Official resources:

- [GSAP Documentation](https://gsap.com/docs/v3/)
- [ScrollTrigger Documentation](https://