# GSAP: Professional Web Animation

GSAP (GreenSock Animation Platform) is a powerful JavaScript animation library for building high-performance web animations and interactive experiences.

It provides precise control over animation timing, sequencing, easing, scroll interactions, SVG elements, and complex visual transitions.

GSAP is particularly useful for:

- Premium landing pages.
- Interactive product websites.
- Scroll-driven storytelling.
- Animated navigation systems.
- 3D website interfaces.
- Product presentations.
- SVG illustrations.
- Text and typography animation.
- Micro-interactions.
- Immersive digital experiences.

This guide establishes practical GSAP development standards for frontend developers and AI coding agents.

## 1. Understanding GSAP

GSAP allows developers to animate JavaScript objects and DOM elements using a consistent animation API.

It supports:

- Tweens.
- Timelines.
- Easing functions.
- Delays and staggering.
- ScrollTrigger.
- SVG animation.
- Callback functions.
- Responsive animation logic.
- Animation control.
- Framework integrations.

GSAP can animate CSS properties, transforms, SVG attributes, JavaScript object properties, and more.

Official documentation:

- [GSAP Documentation](https://gsap.com/docs/v3/)
- [GSAP Getting Started](https://gsap.com/resources/get-started/)
- [GSAP GitHub](https://github.com/greensock/GSAP)

## 2. Installation

Install GSAP using npm:

```bash
npm install gsap
```

Import it into a JavaScript or TypeScript project:

```js
import { gsap } from "gsap";
```

For applications using ScrollTrigger:

```js
import { gsap } from "gsap";
import { ScrollTrigger } from "gsap/ScrollTrigger";

gsap.registerPlugin(ScrollTrigger);
```

Register plugins before using them.

Use the official installation documentation when selecting plugins and deployment options because package availability and licensing terms can change.

## 3. Understanding Tweens

A tween animates one or more properties from their current values to specified destination values.

Basic example:

```js
gsap.to(".box", {
  x: 200,
  duration: 1
});
```

This moves an element horizontally by 200 pixels over one second.

### The three primary tween methods

**gsap.to()**

Animates from the current state to the specified destination.

```js
gsap.to(".box", {
  opacity: 1,
  y: 0,
  duration: 1
});
```

**gsap.from()**

Animates from the specified values to the element's current state.

```js
gsap.from(".heading", {
  opacity: 0,
  y: 50,
  duration: 1
});
```

**gsap.fromTo()**

Explicitly defines both the starting and ending states.

```js
gsap.fromTo(
  ".card",
  {
    opacity: 0,
    scale: 0.8
  },
  {
    opacity: 1,
    scale: 1,
    duration: 0.8
  }
);
```

Use `fromTo()` when the initial animation state must be predictable.

## 4. Core Animation Properties

Common GSAP properties include:

| Property | Purpose |
|---|---|
| `x` | Horizontal movement |
| `y` | Vertical movement |
| `rotation` | Rotation in degrees |
| `scale` | Uniform scaling |
| `scaleX` | Horizontal scaling |
| `scaleY` | Vertical scaling |
| `opacity` | Transparency |
| `duration` | Animation duration |
| `delay` | Start delay |
| `ease` | Easing function |
| `repeat` | Number of repetitions |
| `yoyo` | Reverse on alternate repeats |
| `stagger` | Offset between multiple targets |

Example:

```js
gsap.to(".card", {
  y: -20,
  scale: 1.03,
  duration: 0.6,
  ease: "power2.out"
});
```

GSAP supports many additional properties and plugins.

## 5. Easing Functions

Easing determines how an animation progresses over time.

Without easing, movement can appear mechanical.

Popular easing choices include:

- `none`
- `power1.out`
- `power2.out`
- `power3.out`
- `power4.out`
- `back.out(1.7)`
- `elastic.out(1, 0.3)`
- `bounce.out`
- `circ.out`
- `expo.out`
- `sine.inOut`

Example:

```js
gsap.to(".element", {
  x: 300,
  duration: 1,
  ease: "power3.out"
});
```

### Choosing easing intentionally

| Animation | Suggested easing |
|---|---|
| Interface entrance | `power2.out` |
| Gentle movement | `sine.out` |
| Strong entrance | `power3.out` |
| Overshoot interaction | `back.out(1.7)` |
| Continuous looping | `none` |
| Smooth transition | `power2.inOut` |

Choose easing according to the purpose of the interaction.

Avoid applying dramatic bounce or elastic effects to every interface element.

## 6. Animation Timelines

Timelines are one of GSAP's most important features.

They allow multiple animations to be coordinated in a single sequence.

```js
const tl = gsap.timeline();

tl.from(".logo", {
  opacity: 0,
  y: -20,
  duration: 0.5
});

tl.from(".heading", {
  opacity: 0,
  y: 40,
  duration: 0.8
});

tl.from(".description", {
  opacity: 0,
  y: 20,
  duration: 0.6
});
```

Animations run sequentially by default.

### Timeline positioning

GSAP supports precise positioning.

```js
const tl = gsap.timeline();

tl.from(".heading", {
  opacity: 0,
  y: 40,
  duration: 0.8
});

tl.from(".description", {
  opacity: 0,
  y: 20,
  duration: 0.6
}, "-=0.4");

tl.from(".button", {
  opacity: 0,
  scale: 0.9,
  duration: 0.5
}, "<");
```

Useful position values:

| Position | Meaning |
|---|---|
| `"<"` | Start with the previous animation |
| `">"` | Start at the end of the previous animation |
| `"-=0.3"` | Start 0.3 seconds before the previous animation ends |
| `"+=0.3"` | Start 0.3 seconds after the previous animation ends |
| `1.5` | Start at timeline time 1.5 seconds |

Timelines make complex page transitions easier to maintain.

## 7. Stagger Animations

Staggering creates a sequence across multiple elements.

```js
gsap.from(".card", {
  opacity: 0,
  y: 40,
  duration: 0.7,
  stagger: 0.15,
  ease: "power2.out"
});
```

Cards enter one after another.

Stagger can also use configuration objects:

```js
gsap.from(".item", {
  opacity: 0,
  y: 30,
  duration: 0.6,
  stagger: {
    each: 0.1,
    from: "center"
  }
});
```

Useful stagger patterns:

- `start`
- `end`
- `center`
- `edges`
- `random`

Use stagger to create visual rhythm without making content unnecessarily slow to access.

## 8. Animation Control

GSAP provides methods to control animation playback.

Common methods:

```js
timeline.play();
timeline.pause();
timeline.resume();
timeline.reverse();
timeline.restart();
timeline.seek(1);
timeline.progress(0.5);
timeline.timeScale(1.5);
timeline.kill();
```

These are useful for:

- Interactive navigation.
- Modal transitions.
- Product demonstrations.
- Playable sequences.
- Scroll-linked experiences.
- User-controlled animations.

### Example: Interactive animation

```js
const tl = gsap.timeline({ paused: true });

tl.to(".menu-panel", {
  x: 0,
  duration: 0.5,
  ease: "power3.out"
});

openButton.addEventListener("click", () => {
  tl.play();
});

closeButton.addEventListener("click", () => {
  tl.reverse();
});
```

Remember to remove event listeners when the owning component is destroyed.

## 9. ScrollTrigger

ScrollTrigger connects animations to the page's scroll position.

It is especially useful for immersive storytelling and premium landing pages.

Import and register:

```js
import { gsap } from "gsap";
import { ScrollTrigger } from "gsap/ScrollTrigger";

gsap.registerPlugin(ScrollTrigger);
```

Basic example:

```js
gsap.from(".section-title", {
  opacity: 0,
  y: 60,
  duration: 1,
  scrollTrigger: {
    trigger: ".section",
    start: "top 80%",
    toggleActions: "play none none reverse"
  }
});
```

The animation starts when the section reaches the configured scroll position.

### Important ScrollTrigger properties

| Property | Purpose |
|---|---|
| `trigger` | Element controlling the trigger |
| `start` | Start position |
| `end` | End position |
| `scrub` | Link animation progress to scroll |
| `pin` | Pin an element during scrolling |
| `markers` | Display debugging markers |
| `toggleActions` | Control playback on trigger events |
| `onEnter` | Callback when entering |
| `onLeave` | Callback when leaving |
| `onUpdate` | Callback during progress updates |

### Toggle actions

The four positions in `toggleActions` represent:

1. Enter.
2. Leave.
3. Enter back.
4. Leave back.

Common actions:

- `play`
- `pause`
- `resume`
- `reset`
- `restart`
- `reverse`
- `complete`
- `none`

Example:

```js
scrollTrigger: {
  trigger: ".section",
  start: "top 80%",
  toggleActions: "play none none reverse"
}
```

Use `markers: true` during development to understand trigger positions. Disable them in production.

## 10. Scrubbed Animations

Scrubbing ties animation progress directly to scrolling.

```js
gsap.to(".image", {
  scale: 1.3,
  rotation: 5,
  scrollTrigger: {
    trigger: ".image-section",
    start: "top bottom",
    end: "bottom top",
    scrub: true
  }
});
```

The animation progresses as the user scrolls.

A numeric scrub value adds smoothing:

```js
scrollTrigger: {
  trigger: ".section",
  start: "top top",
  end: "+=1000",
  scrub: 1
}
```

Scrubbed animation is useful for:

- Product reveals.
- Image transformations.
- 3D scene progression.
- Visual storytelling.
- Horizontal transitions.
- Long-form landing pages.

Keep scroll-driven effects understandable and avoid making ordinary navigation dependent on precise scrolling.

## 11. Pinning Sections

ScrollTrigger can pin an element while the user continues scrolling.

```js
gsap.to(".product", {
  rotation: 360,
  scrollTrigger: {
    trigger: ".product-section",
    start: "top top",
    end: "+=1200",
    scrub: 1,
    pin: true
  }
});
```

Pinning is useful for:

- Product showcases.
- Feature walkthroughs.
- Interactive storytelling.
- Sticky visual sections.
- Multi-stage product presentations.

Use pinning carefully because it changes normal document flow and can affect mobile scrolling.

Always test pinned layouts at different viewport heights and device sizes.

## 12. Horizontal Scroll Experiences

Horizontal scroll sections can create immersive presentation layouts.

```js
const panels = gsap.utils.toArray(".panel");

gsap.to(panels, {
  xPercent: -100 * (panels.length - 1),
  ease: "none",
  scrollTrigger: {
    trigger: ".horizontal-section",
    pin: true,
    scrub: 1,
    end: () => `+=${window.innerWidth * (panels.length - 1)}`
  }
});
```

This is a simplified example.

Production implementations should account for:

- Panel widths.
- Responsive layout.
- Content overflow.
- Scroll distance.
- Refresh behavior.
- Mobile alternatives.
- Reduced-motion preferences.

Do not force horizontal scrolling on devices where it harms usability.

## 13. SVG Animation

GSAP can animate SVG attributes and properties.

Example:

```js
gsap.to(".circle", {
  attr: {
    cx: 150,
    cy: 150,
    r: 60
  },
  duration: 1
});
```

SVG animation can be used for:

- Logo reveals.
- Illustrations.
- Animated diagrams.
- Icons.
- Decorative shapes.
- Path-based interactions.

### SVG path drawing

GSAP's DrawSVGPlugin supports animating SVG stroke drawing.

Example:

```js
gsap.from(".line", {
  drawSVG: "0%",
  duration: 2,
  ease: "power2.inOut"
});
```

DrawSVGPlugin is a premium plugin. Verify current licensing and availability before including it in a project.

For simple path drawing, native SVG stroke properties can also be used without a paid plugin.

## 14. Text Animation

Typography is often central to premium web experiences.

Common techniques include:

- Fade-in text.
- Character reveals.
- Word-by-word transitions.
- Line-by-line entrances.
- Split text transitions.
- Text masking.
- Animated counters.

Basic text entrance:

```js
gsap.from(".headline", {
  opacity: 0,
  y: 50,
  duration: 1,
  ease: "power3.out"
});
```

### SplitText

GSAP's SplitText plugin provides advanced character, word, and line splitting.

Example:

```js
const split = new SplitText(".headline", {
  type: "words,lines"
});

gsap.from(split.lines, {
  opacity: 0,
  y: 40,
  stagger: 0.1,
  duration: 0.8
});
```

SplitText is a premium GSAP plugin. Check current licensing and package instructions.

When using text-splitting techniques:

- Preserve readable source content.
- Avoid damaging screen-reader output.
- Revert split structures when appropriate.
- Recalculate after relevant layout changes.
- Test dynamic font loading.
- Avoid excessive DOM nodes.

Do not split text simply because an animation looks impressive.

## 15. React Integration

GSAP can be used with React, but animation lifecycle management is important.

Avoid creating uncontrolled animations during every render.

Use refs to target elements and `useGSAP()` to manage animation lifecycle.

### Recommended integration

Install the React integration:

```bash
npm install @gsap/react
```

Example:

```jsx
import { useRef } from "react";
import gsap from "gsap";
import { useGSAP } from "@gsap/react";

gsap.registerPlugin(useGSAP);

function Hero() {
  const container = useRef(null);

  useGSAP(() => {
    gsap.from(".hero-title", {
      opacity: 0,
      y: 50,
      duration: 1,
      ease: "power3.out"
    });
  }, { scope: container });

  return (
    <section ref={container}>
      <h1 className="hero-title">
        Build Something Extraordinary
      </h1>
    </section>
  );
}

export default Hero;
```

The `scope` limits selector targeting to the component container.

`useGSAP()` also helps manage cleanup through GSAP context.

### Event-driven animations

When creating animations inside event handlers, use the context-safe facilities provided by `useGSAP()` where appropriate.

This ensures animations created later can participate in the component's cleanup lifecycle.

### React best practices

- Use refs for DOM elements.
- Scope selectors to components.
- Keep animations out of render logic.
- Clean up event listeners.
- Avoid unnecessary React state updates.
- Avoid multiple competing animations on the same properties.
- Revert or clean up animations when components unmount.
- Keep animation code organized by component responsibility.

Official React integration:

[GSAP React Documentation](https://gsap.com/resources/React/)

## 16. Responsive Animations

Animations should adapt to different screen sizes and interaction environments.

GSAP provides `matchMedia()` for responsive animation setups.

```js
const mm = gsap.matchMedia();

mm.add("(min-width: 768px)", () => {
  gsap.from(".desktop-heading", {
    x: 100,
    opacity: 0,
    duration: 1
  });
});

mm.add("(max-width: 767px)", () => {
  gsap.from(".mobile-heading", {
    y: 30,
    opacity: 0,
    duration: 0.7
  });
});
```

The match-media context can revert animations when the matching condition stops applying.

In React, prefer integrating responsive animation setup with the component's GSAP context lifecycle.

Do not assume that desktop animation distances, pinned sections, or scroll effects will work correctly on mobile.

## 17. Reduced Motion and Accessibility

Respect users who prefer reduced motion.

Use the operating system preference:

```js
const prefersReducedMotion = window.matchMedia(
  "(prefers-reduced-motion: reduce)"
).matches;
```

Example:

```js
if (prefersReducedMotion) {
  gsap.set(".animated-element", {
    opacity: 1,
    y: 0
  });
} else {
  gsap.from(".animated-element", {
    opacity: 0,
    y: 40,
    duration: 0.8
  });
}
```

For responsive and more advanced setups, `gsap.matchMedia()` can also match the reduced-motion media query.

Accessibility requirements:

- Preserve readable content.
- Avoid essential information appearing only during animation.
- Avoid excessive flashing.
- Avoid disorienting motion.
- Provide keyboard-accessible controls.
- Preserve meaningful focus order.
- Do not make essential interactions depend on hover.
- Provide a usable reduced-motion experience.

Reduced motion should simplify or remove nonessential movement without hiding important information.

## 18. Performance Optimization

GSAP is designed for efficient animation, but poor animation design can still cause performance problems.

### Prefer transform and opacity

Generally prefer:

- `transform`
- `opacity`

Be careful with frequently animating:

- `width`
- `height`
- `top`
- `left`
- `margin`
- `padding`

These properties may trigger layout or painting work.

The browser's rendering pipeline determines the actual cost, so profile complex animations.

### Avoid unnecessary animation loops

Do not continuously animate elements that do not need movement.

Pause or stop animations when they are no longer useful.

### Use will-change carefully

CSS `will-change` can help the browser prepare for certain changes, but excessive use can consume memory.

Do not apply it to every element by default.

### Avoid excessive simultaneous animations

Large numbers of complex animations can compete for rendering resources.

Use staggering and intentional sequencing to control workload.

### Clean up ScrollTriggers

When components are removed, their associated triggers should be cleaned up through the animation context or explicit cleanup.

Avoid leaving stale ScrollTriggers after route changes.

### Profile real behavior

Use browser performance tools to identify:

- Layout recalculations.
- Paint activity.
- Long JavaScript tasks.
- Dropped frames.
- Excessive compositing layers.

Do not assume an animation is performant simply because it uses GSAP.

## 19. GSAP with Three.js and React Three Fiber

GSAP can coordinate DOM elements with Three.js objects.

This is useful for immersive experiences where interface elements and 3D scenes need synchronized transitions.

Example:

```js
const tl = gsap.timeline();

tl.to(camera.position, {
  z: 4,
  duration: 2,
  ease: "power2.inOut"
});

tl.to(model.rotation, {
  y: Math.PI * 2,
  duration: 2,
  ease: "none"
}, "<");

tl.to(".overlay", {
  opacity: 0,
  duration: 0.8
}, "<");
```

Possible use cases:

- Camera transitions.
- Product rotation.
- Scroll-driven scene changes.
- Synchronized text and model animation.
- Scene introductions.
- Interactive product storytelling.

When using GSAP with React Three Fiber:

- Keep references to Three.js objects.
- Avoid recreating timelines unnecessarily.
- Manage animation lifecycle.
- Avoid conflicting `useFrame` updates.
- Ensure ScrollTriggers are cleaned up.
- Test frame performance.
- Keep DOM and 3D animation responsibilities clear.

Use GSAP for coordinated sequences and R3F's frame loop for suitable continuous real-time updates.

## 20. Custom Animation Utilities

GSAP provides utility functions that help build reusable animation logic.

Examples include:

```js
gsap.utils.toArray(".card");
gsap.utils.clamp(0, 100, value);
gsap.utils.mapRange(0, 100, 0, 1, value);
gsap.utils.interpolate(0, 100, 0.5);
```

Utilities can simplify:

- Element selection.
- Value mapping.
- Clamping.
- Interpolation.
- Responsive calculations.
- Reusable animation systems.

Create helper functions when several components share the same animation behavior.

Avoid building an abstraction for every single tween.

## 21. Debugging GSAP

Common issues include:

### Animation does not run

Check:

- Correct element selectors.
- Element existence.
- Plugin registration.
- Component mounting.
- Timeline paused state.
- Conflicting CSS.
- Animation lifecycle.

### ScrollTrigger starts at the wrong position

Check:

- Trigger element dimensions.
- Start and end values.
- Layout changes.
- Image and font loading.
- Pin spacing.
- Scroll container configuration.

Call `ScrollTrigger.refresh()` after significant layout changes when required.

Avoid calling it repeatedly without a clear reason.

### React animation repeats unexpectedly

Check:

- Component rerenders.
- Effect dependencies.
- Missing cleanup.
- Strict Mode behavior during development.
- Multiple timeline creation.

Prefer `useGSAP()` and appropriate context management.

### Elements disappear after animation

Check:

- `from()` initial values.
- `immediateRender` behavior where relevant.
- Overlapping animations.
- Timeline control.
- Inline styles left behind.

Use browser developer tools to inspect actual computed styles.

## 22. Production Architecture

Organize animation code according to application responsibilities.

Example:

```text
src/
├── components/
│   ├── Hero/
│   │   ├── Hero.jsx
│   │   └── hero.animations.js
│   ├── Navigation/
│   │   ├── Navigation.jsx
│   │   └── navigation.animations.js
│   └── ProductShowcase/
│       ├── ProductShowcase.jsx
│       └── product.animations.js
├── hooks/
│   └── useReducedMotion.js
├── animations/
│   ├── presets.js
│   ├── transitions.js
│   └── scroll.js
└── styles/
    └── animations.css
```

This is an example structure, not a mandatory convention.

Keep small component-specific animations close to their components.

Centralize genuinely shared animation presets and utilities.

Avoid creating a large global animation system that makes individual interactions difficult to understand.

## 23. AI Coding Agent Workflow

AI coding agents should follow a consistent animation implementation process.

### Before implementation

- Inspect the existing frontend framework.
- Identify component boundaries.
- Understand the page structure.
- Identify interactive elements.
- Review the design reference.
- Determine the intended animation behavior.
- Identify reduced-motion requirements.
- Check existing animation libraries.

### During implementation

- Use GSAP for animations that benefit from timeline control.
- Use timelines for coordinated sequences.
- Use ScrollTrigger for scroll-based interactions.
- Scope animations to component containers.
- Use `useGSAP()` in React applications where appropriate.
- Avoid unnecessary state updates.
- Manage animation cleanup.
- Preserve semantic HTML.
- Keep mobile behavior intentional.

### During visual review

- Check animation timing.
- Check easing consistency.
- Check transition overlap.
- Verify content remains readable.
- Test scroll behavior.
- Test mobile layouts.
- Test keyboard interactions.
- Test reduced motion.
- Check console errors.
- Profile expensive animations.

### Before completion

- Confirm animations work after route transitions.
- Confirm no stale triggers remain.
- Confirm components clean up correctly.
- Confirm essential content remains accessible.
- Confirm production build succeeds.
- Document any known limitations.

## 24. Production Checklist

### Implementation

- [ ] GSAP is installed correctly.
- [ ] Required plugins are registered.
- [ ] Timelines are organized.
- [ ] Animation selectors are scoped.
- [ ] Responsive behavior is considered.
- [ ] React lifecycle is handled correctly.

### Visual quality

- [ ] Easing feels intentional.
- [ ] Animation durations are appropriate.
- [ ] Staggering improves visual rhythm.
- [ ] Transitions do not conflict.
- [ ] Content remains readable.
- [ ] Motion supports the design.

### Performance

- [ ] Unnecessary animations are removed.
- [ ] Layout-heavy animation is minimized.
- [ ] ScrollTriggers are managed.
- [ ] Animation cleanup is implemented.
- [ ] Browser performance is checked.
- [ ] Mobile performance is tested.

### Accessibility

- [ ] Reduced motion is supported.
- [ ] Essential content does not depend on animation.
- [ ]