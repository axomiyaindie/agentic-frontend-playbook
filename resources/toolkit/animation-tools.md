# Animation and Interaction Tools

A curated collection of animation libraries and tools for building expressive interfaces, interactive experiences, and scroll-driven websites.

## Animation Libraries

### GSAP
- **Website:** https://gsap.com/
- **GitHub:** https://github.com/greensock/GSAP
- **Purpose:** Professional JavaScript animation platform with timeline control.
- **Use cases:** Complex sequences, scroll animations, SVG motion, and interactive storytelling.
- **Getting started:** https://gsap.com/docs/v3/Installation/

### Motion for React
- **Website:** https://motion.dev/
- **GitHub:** https://github.com/motiondivision/motion
- **Purpose:** Animation library for React interfaces.
- **Use cases:** Page transitions, gestures, layout animations, and component interactions.
- **Getting started:** `npm install motion`

### Anime.js
- **Website:** https://animejs.com/
- **GitHub:** https://github.com/juliangarnier/anime
- **Purpose:** JavaScript animation engine for CSS, SVG, DOM attributes, and JavaScript values.
- **Use cases:** Interactive UI effects and custom motion graphics.
- **Getting started:** https://animejs.com/documentation/

### AutoAnimate
- **Website:** https://auto-animate.formkit.com/
- **GitHub:** https://github.com/formkit/auto-animate
- **Purpose:** Automatically adds transitions when elements are added, removed, or moved.
- **Use cases:** Lists, expanding sections, and simple interface transitions.
- **Getting started:** `npm install @formkit/auto-animate`

### Lenis
- **Website:** https://lenis.darkroom.engineering/
- **GitHub:** https://github.com/darkroomengineering/lenis
- **Purpose:** Smooth scrolling library.
- **Use cases:** Scroll-driven visual experiences and custom scrolling behavior.
- **Getting started:** https://github.com/darkroomengineering/lenis

## Interactive Animation Tools

### Rive
- **Website:** https://rive.app/
- **Purpose:** Design and runtime platform for interactive, state-driven vector animations.
- **Use cases:** Interactive icons, onboarding, animated interfaces, and state-machine-driven motion.
- **Getting started:** https://rive.app/docs

### Lottie
- **Website:** https://lottiefiles.com/
- **GitHub:** https://github.com/airbnb/lottie-web
- **Purpose:** Runtime for compatible JSON-based vector animations.
- **Use cases:** Loading animations, illustrations, and interface motion.
- **Getting started:** https://github.com/airbnb/lottie-web

### Theatre.js
- **Website:** https://www.theatrejs.com/
- **GitHub:** https://github.com/theatre-js/theatre
- **Purpose:** Visual timeline authoring for web and 3D animations.
- **Use cases:** Camera movement, product scenes, and synchronized animation sequences.
- **Getting started:** https://www.theatrejs.com/docs/latest

## Choosing the Right Tool

- Use CSS for simple hover, focus, and transition effects.
- Use Motion for common React interface animations.
- Use GSAP for complex timelines and scroll-driven sequences.
- Use Rive for interactive state-driven vector animation.
- Use Lottie for compatible exported vector animation playback.
- Use Theatre.js for timeline-based control across 3D and web elements.

## Accessibility and Performance

- Respect the `prefers-reduced-motion` preference.
- Keep essential functionality available without animation.
- Avoid excessive motion that interferes with reading or navigation.
- Prefer transform and opacity animations when appropriate.
- Test animation performance on lower-powered mobile devices.
- Avoid taking control of scrolling away from the user.