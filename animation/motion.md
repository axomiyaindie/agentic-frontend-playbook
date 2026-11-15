# Motion for React: Declarative UI Animation

Motion is a modern animation library for JavaScript and React applications.

Previously known as Framer Motion, Motion provides a declarative API for animating interface elements, managing transitions, handling gestures, and creating interactive experiences.

It is particularly useful for:

- Modern React applications.
- Premium landing pages.
- SaaS dashboards.
- Interactive navigation.
- Animated component systems.
- Modal and dialog transitions.
- Page transitions.
- Drag-and-drop interfaces.
- Scroll-triggered animations.
- Responsive micro-interactions.

This guide establishes practical implementation standards for developers and AI coding agents building modern animated frontend applications.

## 1. Understanding Motion

Motion provides animation primitives that integrate naturally with React.

Its capabilities include:

- Declarative animations.
- Initial and target states.
- Variants.
- Animation orchestration.
- Hover and tap gestures.
- Drag interactions.
- Layout animations.
- Shared layout transitions.
- Exit animations.
- Scroll-triggered animations.
- Scroll-linked animations.
- SVG animation.
- Spring physics.
- Reduced-motion support.

Official documentation:

- [Motion Documentation](https://motion.dev/docs)
- [Motion for React](https://motion.dev/docs/react)
- [Motion Examples](https://motion.dev/examples)

## 2. Installation

Install Motion for React:

```bash
npm install motion
```

Import components from `motion/react`:

```jsx
import { motion } from "motion/react";
```

For example:

```jsx
function App() {
  return (
    <motion.div
      initial={{ opacity: 0, y: 30 }}
      animate={{ opacity: 1, y: 0 }}
      transition={{ duration: 0.6 }}
    >
      Hello Motion
    </motion.div>
  );
}
```

Motion also provides APIs for framework-independent JavaScript animation.

Use the React package entry point when working with React components.

## 3. Motion Components

Motion components are enhanced versions of standard HTML and SVG elements.

Examples:

```jsx
<motion.div />
<motion.section />
<motion.button />
<motion.img />
<motion.svg />
<motion.path />
```

They support animation-related properties while preserving familiar component structures.

Example:

```jsx
<motion.button
  animate={{
    scale: 1.05,
    backgroundColor: "#2563eb"
  }}
>
  Get Started
</motion.button>
```

Use motion components when an element needs animation or gesture behavior.

Avoid converting every HTML element into a motion component without a reason.

## 4. Initial, Animate and Exit States

Motion supports declarative animation states.

### Initial

Defines the starting state.

### Animate

Defines the target state.

### Exit

Defines the state used when an element is removed from the React tree through `AnimatePresence`.

Example:

```jsx
<motion.div
  initial={{ opacity: 0, y: 40 }}
  animate={{ opacity: 1, y: 0 }}
  transition={{ duration: 0.7 }}
>
  Welcome
</motion.div>
```

A typical entrance animation moves an element from an initial state to its target state.

### Disable initial animation

For situations where an initial entrance is not desirable:

```jsx
<motion.div
  initial={false}
  animate={{ opacity: 1 }}
>
  Content
</motion.div>
```

Use initial states intentionally to avoid unnecessary movement during hydration or route rendering.

## 5. Transition Configuration

Transitions control how Motion interpolates between animation states.

Example:

```jsx
<motion.div
  animate={{ x: 100 }}
  transition={{
    duration: 0.8,
    ease: "easeOut"
  }}
/>
```

Important transition properties:

| Property | Purpose |
|---|---|
| `duration` | Animation duration |
| `delay` | Delay before starting |
| `ease` | Easing function |
| `type` | Transition type |
| `stiffness` | Spring stiffness |
| `damping` | Spring damping |
| `mass` | Spring mass |
| `repeat` | Repetition count |
| `repeatType` | Repetition behavior |
| `repeatDelay` | Delay between repetitions |

### Tween transitions

Use tween transitions for predictable time-based animations.

```jsx
<motion.div
  animate={{ opacity: 1 }}
  transition={{
    type: "tween",
    duration: 0.5,
    ease: "easeOut"
  }}
/>
```

### Spring transitions

Spring animations can create natural, physical movement.

```jsx
<motion.div
  animate={{ scale: 1 }}
  transition={{
    type: "spring",
    stiffness: 200,
    damping: 20
  }}
/>
```

Spring behavior is useful for:

- Buttons.
- Cards.
- Drag interactions.
- Modal entrances.
- Interactive navigation.
- Layout transitions.

Choose spring settings according to the intended visual character.

## 6. Variants

Variants allow multiple components to share named animation states.

They are especially useful for reusable and coordinated animation systems.

```jsx
const variants = {
  hidden: {
    opacity: 0,
    y: 30
  },
  visible: {
    opacity: 1,
    y: 0
  }
};

function Hero() {
  return (
    <motion.section
      variants={variants}
      initial="hidden"
      animate="visible"
      transition={{ duration: 0.8 }}
    >
      <h1>Build Better Experiences</h1>
    </motion.section>
  );
}
```

Variants can also be defined for individual elements.

```jsx
const containerVariants = {
  hidden: {},
  visible: {
    transition: {
      staggerChildren: 0.15
    }
  }
};

const itemVariants = {
  hidden: {
    opacity: 0,
    y: 20
  },
  visible: {
    opacity: 1,
    y: 0
  }
};
```

Usage:

```jsx
<motion.div
  variants={containerVariants}
  initial="hidden"
  animate="visible"
>
  {items.map((item) => (
    <motion.div
      key={item.id}
      variants={itemVariants}
    >
      {item.label}
    </motion.div>
  ))}
</motion.div>
```

Variants help organize animation behavior across component hierarchies.

## 7. Animation Orchestration

Motion supports coordinating animations across parent and child components.

Useful orchestration options include:

- `staggerChildren`
- `delayChildren`
- `when`

Example:

```jsx
const container = {
  hidden: {},
  visible: {
    transition: {
      delayChildren: 0.2,
      staggerChildren: 0.12
    }
  }
};
```

Children inherit the parent animation state when using matching variant labels.

Orchestration is useful for:

- Navigation menus.
- Feature lists.
- Card grids.
- Hero sections.
- Dashboard content.
- Multi-element entrances.

Avoid excessive staggering that delays access to important content.

## 8. Hover and Tap Gestures

Motion supports interactive gesture animations.

### Hover

```jsx
<motion.button
  whileHover={{ scale: 1.05 }}
>
  Explore
</motion.button>
```

### Tap

```jsx
<motion.button
  whileTap={{ scale: 0.96 }}
>
  Submit
</motion.button>
```

### Combined interaction

```jsx
<motion.button
  whileHover={{
    scale: 1.04,
    y: -2
  }}
  whileTap={{
    scale: 0.97
  }}
  transition={{
    type: "spring",
    stiffness: 400,
    damping: 20
  }}
>
  Get Started
</motion.button>
```

Use gesture animations to provide feedback without changing the meaning or usability of the interface.

Important considerations:

- Hover is not available on every device.
- Essential actions must not depend on hover.
- Touch targets should remain accessible.
- Focus styles should remain visible.
- Gesture animations should not interfere with keyboard interaction.

## 9. Drag Interactions

Motion supports draggable components.

```jsx
<motion.div
  drag
  dragConstraints={{
    left: -100,
    right: 100,
    top: -50,
    bottom: 50
  }}
>
  Drag Me
</motion.div>
```

Useful properties include:

- `drag`
- `dragConstraints`
- `dragElastic`
- `dragMomentum`
- `dragDirectionLock`
- `whileDrag`

### Drag direction

```jsx
<motion.div
  drag="x"
  dragConstraints={{
    left: -150,
    right: 150
  }}
>
  Horizontal Drag
</motion.div>
```

### Drag interactions in applications

Useful for:

- Carousels.
- Interactive cards.
- Kanban boards.
- Sliders.
- Reorderable lists.
- Product showcases.

Do not implement drag as the only method of completing an important action.

Provide appropriate buttons, keyboard alternatives, or other accessible controls.

## 10. AnimatePresence and Exit Animations

React normally removes components from the DOM immediately when they are no longer rendered.

`AnimatePresence` allows Motion to animate their exit before removal.

Import:

```jsx
import {
  motion,
  AnimatePresence
} from "motion/react";
```

Example:

```jsx
function Modal({ open }) {
  return (
    <AnimatePresence>
      {open && (
        <motion.div
          key="modal"
          initial={{
            opacity: 0,
            scale: 0.95
          }}
          animate={{
            opacity: 1,
            scale: 1
          }}
          exit={{
            opacity: 0,
            scale: 0.95
          }}
          transition={{
            duration: 0.2
          }}
        >
          Modal Content
        </motion.div>
      )}
    </AnimatePresence>
  );
}
```

### Important practices

- Give conditional children stable keys.
- Keep exit animations short.
- Manage focus when opening and closing dialogs.
- Prevent background interaction when a modal is active.
- Ensure exiting elements do not obstruct important interactions.
- Test route transitions and rapid state changes.

`AnimatePresence` is useful for:

- Dialogs.
- Dropdowns.
- Navigation panels.
- Notifications.
- Tabs.
- Conditional content.
- Page transitions.

## 11. Layout Animations

Motion can animate layout changes when an element's dimensions or position change.

Use the `layout` prop:

```jsx
<motion.div layout>
  Content
</motion.div>
```

Motion can animate layout changes caused by React rendering.

Example:

```jsx
function ExpandableCard({ expanded }) {
  return (
    <motion.div
      layout
      className="card"
    >
      <h2>Product</h2>

      {expanded && (
        <motion.p>
          Additional product details.
        </motion.p>
      )}
    </motion.div>
  );
}
```

Layout animations are useful for:

- Expandable cards.
- Responsive navigation.
- Reorderable lists.
- Tab transitions.
- Grid transformations.
- Dashboard panels.
- Dynamic content.

Use layout animations when the layout itself changes, rather than manually calculating every positional transition.

## 12. Shared Layout Transitions

The `layoutId` property allows elements with matching identifiers to animate between different locations in the React tree.

Example:

```jsx
function Tabs({ activeTab, setActiveTab }) {
  const tabs = ["Overview", "Features", "Pricing"];

  return (
    <div className="tabs">
      {tabs.map((tab) => (
        <button
          key={tab}
          onClick={() => setActiveTab(tab)}
        >
          {tab}

          {activeTab === tab && (
            <motion.div
              layoutId="active-tab"
              className="active-indicator"
            />
          )}
        </button>
      ))}
    </div>
  );
}
```

This allows the active indicator to move between tabs.

Shared layout transitions are useful for:

- Active navigation indicators.
- Gallery transitions.
- Product cards.
- Tab indicators.
- Shared image transitions.
- Expanding interface elements.

Keep `layoutId` values unique within the relevant layout context.

## 13. Scroll-Triggered Animations

Motion provides `whileInView` for animations triggered when elements enter the viewport.

Example:

```jsx
<motion.section
  initial={{
    opacity: 0,
    y: 50
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

Important viewport options:

| Property | Purpose |
|---|---|
| `once` | Trigger only once |
| `amount` | Required visible proportion |
| `margin` | Adjust viewport detection margin |
| `root` | Custom scroll root |

Use scroll-triggered animation for:

- Section reveals.
- Feature lists.
- Editorial layouts.
- Image entrances.
- Testimonials.
- Product showcases.

Do not animate every section by default. Prioritize meaningful visual transitions.

## 14. Scroll-Linked Animations

Scroll-triggered animations start when an element enters the viewport.

Scroll-linked animations continuously map animation progress to scroll position.

Motion provides `useScroll()` for this purpose.

```jsx
import {
  motion,
  useScroll
} from "motion/react";

function ScrollProgress() {
  const { scrollYProgress } = useScroll();

  return (
    <motion.div
      className="progress-bar"
      style={{
        scaleX: scrollYProgress,
        transformOrigin: "0% 50%"
      }}
    />
  );
}
```

The progress value typically ranges from 0 to 1.

### Element-based scroll progress

```jsx
const { scrollYProgress } = useScroll({
  target: containerRef,
  offset: ["start end", "end start"]
});
```

This tracks the target element relative to the viewport.

Useful applications:

- Reading progress.
- Scroll indicators.
- Image transformations.
- Parallax effects.
- Product presentations.
- Editorial storytelling.

Use scroll-linked animation carefully because large numbers of animated properties can affect rendering performance.

## 15. Motion Values

Motion values represent values that can update independently of React's normal rendering cycle.

Useful hooks include:

- `useMotionValue()`
- `useTransform()`
- `useSpring()`
- `useVelocity()`
- `useMotionValueEvent()`

### useMotionValue

```jsx
import {
  motion,
  useMotionValue
} from "motion/react";

function Example() {
  const x = useMotionValue(0);

  return (
    <motion.div
      style={{ x }}
      drag="x"
    >
      Drag Me
    </motion.div>
  );
}
```

### useTransform

Map one motion value into another.

```jsx
import {
  useScroll,
  useTransform,
  motion
} from "motion/react";

function Parallax() {
  const { scrollYProgress } = useScroll();

  const y = useTransform(
    scrollYProgress,
    [0, 1],
    [0, -200]
  );

  return (
    <motion.div style={{ y }}>
      Parallax Content
    </motion.div>
  );
}
```

### useSpring

Create spring-based motion from another motion value.

```jsx
import {
  useSpring,
  useMotionValue
} from "motion/react";

const x = useMotionValue(0);

const smoothX = useSpring(x, {
  stiffness: 100,
  damping: 20
});
```

Motion values are useful for pointer tracking, scroll effects, drag interactions, and other continuously changing values.

## 16. SVG Animation

Motion supports SVG animation through motion components.

Example:

```jsx
<motion.circle
  cx="50"
  cy="50"
  r="40"
  initial={{
    pathLength: 0
  }}
  animate={{
    pathLength: 1
  }}
  transition={{
    duration: 2
  }}
/>
```

Useful applications:

- Animated icons.
- Logo reveals.
- Progress indicators.
- Illustrations.
- Decorative graphics.
- Interface feedback.

Use SVG animation when vector-based graphics are appropriate.

## 17. Page Transitions

Motion can animate route-related UI changes when integrated with the application's routing system.

Example:

```jsx
import {
  motion,
  AnimatePresence
} from "motion/react";

function Page({ children }) {
  return (
    <motion.main
      initial={{
        opacity: 0,
        y: 12
      }}
      animate={{
        opacity: 1,
        y: 0
      }}
      exit={{
        opacity: 0,
        y: -12
      }}
      transition={{
        duration: 0.25
      }}
    >
      {children}
    </motion.main>
  );
}
```

A complete route transition implementation also needs the routing layer to preserve exiting content long enough for the exit animation to finish.

Account for:

- Route changes.
- Stable route keys.
- Scroll restoration.
- Focus management.
- Browser history.
- Loading states.
- Reduced motion.
- Deep links.

Do not introduce page transitions that make navigation feel slower or interfere with browser behavior.

## 18. Component Architecture

Keep animation behavior organized and reusable.

Example project structure:

```text
src/
├── components/
│   ├── AnimatedButton/
│   │   └── AnimatedButton.jsx
│   ├── Modal/
│   │   └── Modal.jsx
│   └── AnimatedCard/
│       └── AnimatedCard.jsx
├── animations/
│   ├── variants.js
│   ├── transitions.js
│   └── presets.js
├── hooks/
│   └── useReducedMotion.js
└── pages/
    └── Home.jsx
```

Example reusable variants:

```js
export const fadeUp = {
  hidden: {
    opacity: 0,
    y: 24
  },
  visible: {
    opacity: 1,
    y: 0
  }
};
```

Example reusable transition:

```js
export const smoothTransition = {
  duration: 0.6,
  ease: [0.22, 1, 0.36, 1]
};
```

Keep abstractions small and meaningful.

Do not create a large animation framework for a small application.

## 19. Performance Optimization

Motion supports efficient animation, but the application still needs good performance engineering.

### Prefer suitable animated properties

Transforms and opacity are often efficient choices:

- `x`
- `y`
- `scale`
- `rotate`
- `opacity`

Animating layout-affecting properties can cause additional layout work.

Profile complex animations rather than assuming every property has the same rendering cost.

### Avoid unnecessary React updates

Use Motion values for continuously changing values where appropriate instead of storing every animation frame in React state.

### Reduce excessive animation

Avoid:

- Too many simultaneous animated elements.
- Unnecessary infinite loops.
- Excessive blur and filter animations.
- Large numbers of expensive layout transitions.
- Continuous animation of invisible elements.

### Use lazy loading where appropriate

Load animation-heavy sections and optional dependencies only when they are needed.

### Consider Motion's optimized APIs

Motion also provides `LazyMotion` and `m` components for reducing the amount of animation functionality loaded initially.

Example:

```jsx
import {
  LazyMotion,
  domAnimation,
  m
} from "motion/react";

function App() {
  return (
    <LazyMotion features={domAnimation}>
      <m.div
        initial={{ opacity: 0 }}
        animate={{ opacity: 1 }}
      >
        Optimized Motion Component
      </m.div>
    </LazyMotion>
  );
}
```

Choose the feature bundle that supports the APIs used by the application.

Consult the current Motion documentation before configuring custom feature bundles.

## 20. Accessibility and Reduced Motion

Animation should enhance usability rather than create barriers.

Motion provides `useReducedMotion()` to detect whether the user prefers reduced motion.

Example:

```jsx
import {
  motion,
  useReducedMotion
} from "motion/react";

function AnimatedCard() {
  const shouldReduceMotion = useReducedMotion();

  return (
    <motion.div
      initial={{
        opacity: 0,
        y: shouldReduceMotion ? 0 : 30
      }}
      animate={{
        opacity: 1,
        y: 0
      }}
      transition={{
        duration: shouldReduceMotion ? 0.01 : 0.6
      }}
    >
      Accessible Content
    </motion.div>
  );
}
```

Accessibility principles:

- Respect reduced-motion preferences.
- Avoid excessive movement.
- Avoid flashing effects.
- Keep content readable during animation.
- Preserve keyboard navigation.
- Maintain visible focus indicators.
- Do not rely exclusively on hover.
- Keep interaction feedback understandable.
- Avoid delaying access to essential content.

Reduced motion should preserve functionality while minimizing unnecessary movement.

## 21. Motion vs GSAP

Motion and GSAP both provide powerful animation capabilities, but they solve different problems particularly well.

| Capability | Motion | GSAP |
|---|---|---|
| React integration | Native declarative API | React integration through `@gsap/react` |
| Component animations | Excellent | Excellent |
| Hover and tap gestures | Built-in | Custom implementation |
| Drag interactions | Built-in | Custom implementation |
| Layout transitions | Built-in | Requires additional logic |
| Exit animations | AnimatePresence | Timeline and lifecycle management |
| Complex timelines | Less timeline-centric | Excellent |
| Scroll-driven animation | Built-in hooks and viewport APIs | ScrollTrigger |
| SVG animation | Supported | Extensive capabilities |
| DOM and object animation | Supported | Extensive capabilities |
| Complex coordinated sequences | Good | Excellent |

### Choose Motion when:

- Building React interfaces.
- Animating component states.
- Creating hover and tap feedback.
- Implementing drag interactions.
- Building layout transitions.
- Animating dialogs and menus.
- Creating reusable component animation patterns.

### Choose GSAP when:

- Building complex animation timelines.
- Creating advanced scroll storytelling.
- Coordinating many different animation targets.
- Animating DOM, SVG, and JavaScript objects together.
- Creating complex product presentations.
- Synchronizing 3D scenes with interface animations.

### Using both libraries

A project can use both libraries when their responsibilities are clearly separated.

For example:

- Motion handles component-level interaction.
- GSAP handles complex scroll-driven storytelling.

Avoid using both libraries to control the same properties on the same elements simultaneously.

Choose the smallest toolset that satisfies the product requirements.

## 22. Debugging Common Problems

### Animation does not appear

Check:

- Initial and target values.
- Component mounting.
- Conditional rendering.
- CSS overrides.
- Motion component imports.
- Animation state changes.

### Exit animation does not run

Check:

- Whether `AnimatePresence` wraps the conditional content.
- Whether the child has a stable key.
- Whether the component is removed through React rendering.
- Whether the exit property is defined.

### Layout animation behaves unexpectedly

Check:

- Parent layout.
- Element dimensions.
- Positioning rules.
- Overflow.
- Nested layout components.
- Stable component identity.

### Drag behavior conflicts with scrolling

Check:

- Drag direction.
- Touch-action behavior.
- Gesture constraints.
- Scrollable parent elements.
- Mobile browser behavior.

### Performance problems

Check:

- Excessive component rendering.
- Large numbers of animated elements.
- Layout-heavy animations.
- Expensive visual filters.
- Unnecessary continuous updates.

Use browser developer tools to inspect actual rendering behavior.

## 23. AI Coding Agent Workflow

AI coding agents should follow a structured process when implementing Motion.

### Before implementation

- Inspect the frontend framework.
- Identify component boundaries.
- Understand interaction requirements.
- Review the visual design.
- Identify repeated animation patterns.
- Determine accessibility requirements.
- Check whether GSAP already exists in the project.

### During implementation

- Use declarative motion components.
- Define reusable variants when appropriate.
- Use transitions intentionally.
- Use AnimatePresence for exit animations.
- Use layout animations for layout changes.
- Use gesture APIs for interactions.
- Keep animation logic close to components.
- Avoid unnecessary state updates.
- Support reduced motion.

### During visual review

- Verify animation timing.
- Check easing consistency.
- Test hover and tap behavior.
- Test drag interactions.
- Verify layout transitions.
- Test mobile behavior.
- Test keyboard interactions.
- Check exit animations.
- Review reduced-motion behavior.

### Before completion

- Confirm the production build succeeds.
- Check browser console errors.
- Verify route transitions.
- Check component cleanup.
- Validate accessibility.
- Review performance.
- Document limitations.

Do not add animations merely to make an interface appear more sophisticated. Every animation should serve a clear interaction or communication purpose.

## 24. Production Checklist

### Implementation

- [ ] Motion is installed correctly.
- [ ] Motion components are used appropriately.
- [ ] Variants are reusable where useful.
- [ ] Transition settings are intentional.
- [ ] Component lifecycle is handled.
- [ ] Conditional elements have stable keys.
- [ ] Exit animations work correctly.

### Interaction

- [ ] Hover states work.
- [ ] Tap feedback works.
- [ ] Drag behavior is predictable.
- [ ] Layout transitions are smooth.
- [ ] Scroll animations behave correctly.
- [ ] Keyboard interactions remain available.

### Performance

- [ ] Unnecessary animation is removed.
- [ ] React updates are controlled.
- [ ] Expensive layout animation is minimized.
- [ ] Large animated lists are considered carefully.
- [ ] Optional animation features are loaded appropriately.
- [ ] Mobile performance is tested.

### Accessibility

- [ ] Reduced-motion preferences are respected.
- [ ] Focus indicators remain visible.
- [ ] Content remains accessible.
- [ ] Hover is not the only interaction method.
- [ ] Motion does not block essential actions.

### Validation

- [ ] Production build succeeds.
- [ ] Console errors are checked.
- [ ] Different viewport sizes are tested.
- [ ] Exit animations are validated.
- [ ] Route transitions are tested.
- [ ] Visual quality is reviewed.

## 25. Further Learning

Official resources:

- [Motion Documentation](https://motion.dev/docs)
- [Motion for React](https://motion.dev/docs/react)
- [Motion Components](https://motion.dev/docs/react-motion-component)
- [Motion Transitions](https://motion.dev/docs/react-transitions)
- [Motion Gestures](https://motion.dev/docs/react-gestures)
- [Motion Layout Animations](https://motion.dev/docs/react-layout-animations)
- [Motion AnimatePresence](https://motion.dev/docs/react-animate-presence)
- [Motion Scroll Animations](https://motion.dev/docs/react-scroll-animations)
- [Motion Examples](https://motion.dev/examples)

---

## 26. Animation & Interaction Documentation

This guide establishes Motion as the foundation for declarative React animations, gestures, layout transitions, and component-level interactions.

Related guides:

1. [GSAP](./gsap.md)
2. [Motion](./motion.md)
3. [Scroll Experiences](./scroll-experiences.md)

Together, these documents will provide a practical foundation for professional web animation and immersive interface experiences.