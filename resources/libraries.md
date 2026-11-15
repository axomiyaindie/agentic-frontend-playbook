# Frontend, 3D Web & Development Libraries

A curated directory of tools, libraries, frameworks, and developer resources for building modern frontend applications, immersive 3D websites, interactive interfaces, and high-quality digital experiences.

This directory helps developers and AI coding agents discover appropriate technologies, understand their purpose, and make informed implementation decisions.

The emphasis is on official documentation, actively maintained projects, practical engineering tools, and well-established ecosystems.

> This is a curated discovery directory, not an endorsement of every listed dependency. Always evaluate compatibility, maintenance, licensing, security, and project requirements before adoption.

## 1. How to Choose a Library

Before introducing a dependency, an AI coding agent should:

1. Understand the actual implementation requirement.
2. Inspect the existing project architecture.
3. Check whether the framework already provides the functionality.
4. Evaluate native browser APIs and CSS alternatives.
5. Review official documentation.
6. Check compatibility with the installed framework and runtime.
7. Inspect maintenance activity and known issues.
8. Evaluate bundle size and runtime impact.
9. Review licensing and security considerations.
10. Explain why the dependency is necessary.

Prefer the smallest appropriate solution that satisfies the requirements.

Do not introduce multiple libraries that solve essentially the same problem without a clear architectural reason.

---

## 2. Frontend Frameworks and Build Tools

### Application frameworks

| Technology | Purpose | Official resource |
|---|---|---|
| React | Component-based UI library | [react.dev](https://react.dev/) |
| Next.js | React framework for full-stack web applications | [nextjs.org](https://nextjs.org/docs) |
| Vue | Progressive JavaScript framework | [vuejs.org](https://vuejs.org/) |
| Nuxt | Full-stack Vue framework | [nuxt.com](https://nuxt.com/) |
| Svelte | Component-oriented UI framework | [svelte.dev](https://svelte.dev/) |
| SvelteKit | Full-stack Svelte framework | [svelte.dev/docs/kit](https://svelte.dev/docs/kit) |
| Astro | Content-focused web framework | [astro.build](https://astro.build/) |
| Angular | Application development platform | [angular.dev](https://angular.dev/) |

### Build tools and development environments

| Technology | Purpose | Official resource |
|---|---|---|
| Vite | Frontend development and build tooling | [vite.dev](https://vite.dev/) |
| Turbopack | Incremental bundler | [turbopack.dev](https://turbopack.dev/) |
| Rspack | High-performance JavaScript bundler | [rspack.dev](https://rspack.dev/) |
| esbuild | Fast JavaScript bundler and transformer | [esbuild.github.io](https://esbuild.github.io/) |
| Rollup | JavaScript module bundler | [rollupjs.org](https://rollupjs.org/) |
| TypeScript | Static type checking for JavaScript | [typescriptlang.org](https://www.typescriptlang.org/) |
| Bun | JavaScript runtime and development toolkit | [bun.sh](https://bun.sh/) |
| pnpm | Efficient package manager | [pnpm.io](https://pnpm.io/) |

**Selection guidance**

- Choose React when building component-driven interfaces and React-based products.
- Consider Next.js when routing, server rendering, server-side functionality, or full-stack React features are needed.
- Choose Vite for lightweight frontend applications and development environments.
- Consider Astro for content-heavy websites where minimal client-side JavaScript is desirable.
- Use TypeScript when stronger type safety and maintainability are valuable.
- Use the package manager already established by the repository unless migration is justified.

---

## 3. Styling and CSS Systems

| Technology | Purpose | Official resource |
|---|---|---|
| Tailwind CSS | Utility-first CSS framework | [tailwindcss.com](https://tailwindcss.com/) |
| Sass | CSS preprocessor | [sass-lang.com](https://sass-lang.com/) |
| CSS Modules | Locally scoped CSS | [github.com/css-modules](https://github.com/css-modules/css-modules) |
| PostCSS | CSS transformation tooling | [postcss.org](https://postcss.org/) |
| Panda CSS | CSS-in-JS styling system | [panda-css.com](https://panda-css.com/) |
| Vanilla Extract | Type-safe CSS authoring | [vanilla-extract.style](https://vanilla-extract.style/) |
| Open Props | CSS custom property design tokens | [open-props.style](https://open-props.style/) |

**Selection guidance**

- Prefer CSS variables and design tokens for reusable visual systems.
- Use Tailwind when utility-based styling fits the project.
- Use CSS Modules when component-scoped styles are preferred.
- Use native CSS capabilities before introducing a styling dependency.
- Avoid mixing multiple styling systems without a clear reason.

---

## 4. UI Component Libraries

### React UI libraries

| Library | Purpose | Official resource |
|---|---|---|
| shadcn/ui | Customizable, source-owned UI components | [ui.shadcn.com](https://ui.shadcn.com/) |
| Radix UI | Accessible unstyled UI primitives | [radix-ui.com](https://www.radix-ui.com/) |
| Base UI | Unstyled accessible React components | [base-ui.com](https://base-ui.com/) |
| Material UI | Material Design React components | [mui.com](https://mui.com/) |
| Chakra UI | Component-based React UI system | [chakra-ui.com](https://www.chakra-ui.com/) |
| Mantine | React components and hooks | [mantine.dev](https://mantine.dev/) |
| Ant Design | Enterprise-oriented React components | [ant.design](https://ant.design/) |
| DaisyUI | Tailwind CSS component classes | [daisyui.com](https://daisyui.com/) |
| Headless UI | Unstyled accessible UI components | [headlessui.com](https://headlessui.com/) |
| NextUI / HeroUI | React component system | [heroui.com](https://www.heroui.com/) |

### Icon libraries

| Library | Purpose | Official resource |
|---|---|---|
| Lucide | Consistent open-source icons | [lucide.dev](https://lucide.dev/) |
| Phosphor Icons | Flexible icon family | [phosphoricons.com](https://phosphoricons.com/) |
| Iconify | Unified icon collection | [iconify.design](https://iconify.design/) |
| Tabler Icons | Open-source SVG icons | [tabler.io/icons](https://tabler.io/icons) |
| Heroicons | Interface icon collection | [heroicons.com](https://heroicons.com/) |
| Material Symbols | Google's icon system | [fonts.google.com/icons](https://fonts.google.com/icons) |

### Component development and documentation

| Library | Purpose | Official resource |
|---|---|---|
| Storybook | Component development and documentation | [storybook.js.org](https://storybook.js.org/) |
| Ladle | Lightweight component development environment | [ladle.dev](https://ladle.dev/) |

**Selection guidance**

- Choose one primary component system for consistency.
- Prefer accessible primitives for custom visual designs.
- Use shadcn/ui when source-owned, editable components fit the project.
- Use Radix UI or Base UI when unstyled interaction primitives are needed.
- Use Storybook when isolated component development and documentation provide value.

Remember that shadcn/ui components are added to the project as source code rather than functioning as a conventional hosted component package.

---

## 5. 3D Web and WebGL

### Core 3D technologies

| Technology | Purpose | Official resource |
|---|---|---|
| Three.js | 3D graphics using JavaScript | [threejs.org](https://threejs.org/) |
| React Three Fiber | React renderer for Three.js | [r3f.docs.pmnd.rs](https://r3f.docs.pmnd.rs/) |
| Babylon.js | Real-time 3D engine | [babylonjs.com](https://www.babylonjs.com/) |
| PlayCanvas | Web-based 3D engine | [playcanvas.com](https://playcanvas.com/) |
| A-Frame | Web framework for VR experiences | [aframe.io](https://aframe.io/) |
| WebGPU | Modern browser graphics and compute API | [developer.mozilla.org](https://developer.mozilla.org/en-US/docs/Web/API/WebGPU_API) |
| WebGL | Browser graphics API | [developer.mozilla.org](https://developer.mozilla.org/en-US/docs/Web/API/WebGL_API) |

### React Three Fiber ecosystem

| Library | Purpose | Official resource |
|---|---|---|
| Drei | Helpers and abstractions for R3F | [github.com/pmndrs/drei](https://github.com/pmndrs/drei) |
| React Three Rapier | Physics integration | [github.com/pmndrs/react-three-rapier](https://github.com/pmndrs/react-three-rapier) |
| React Three Postprocessing | Post-processing effects | [github.com/pmndrs/react-postprocessing](https://github.com/pmndrs/react-postprocessing) |
| GLTFJSX | Convert GLTF assets into JSX components | [github.com/pmndrs/gltfjsx](https://github.com/pmndrs/gltfjsx) |
| Leva | Interactive development controls | [github.com/pmndrs/leva](https://github.com/pmndrs/leva) |
| Maath | Mathematical utilities for 3D development | [github.com/pmndrs/maath](https://github.com/pmndrs/maath) |
| React Three XR | XR support for R3F | [github.com/pmndrs/react-xr](https://github.com/pmndrs/react-xr) |

The React Three Fiber ecosystem provides helpers for asset loading, physics, post-processing, scene interaction, and development tooling. Consult its ecosystem documentation when selecting compatible packages.

[React Three Fiber ecosystem](https://r3f.docs.pmnd.rs/getting-started/introduction).

### 3D asset and model tools

| Tool | Purpose | Official resource |
|---|---|---|
| Blender | 3D modeling, animation and rendering | [blender.org](https://www.blender.org/) |
| glTF Transform | glTF optimization and processing | [gltf-transform.dev](https://gltf-transform.dev/) |
| Khronos glTF | 3D asset format specification | [khronos.org/gltf](https://www.khronos.org/gltf/) |
| Meshopt | Geometry and animation compression | [meshoptimizer.org](https://meshoptimizer.org/) |
| Draco | 3D geometry compression | [google.github.io/draco](https://google.github.io/draco/) |
| Sketchfab | 3D model discovery and hosting | [sketchfab.com](https://sketchfab.com/) |
| Poly Haven | Public-domain 3D assets, HDRIs and textures | [polyhaven.com](https://polyhaven.com/) |

**Selection guidance**

- Use Three.js when direct control over the rendering architecture is desirable.
- Use React Three Fiber when the application is already built around React.
- Use Drei to avoid repeatedly implementing common 3D helpers.
- Use Rapier when realistic physics simulation is required.
- Use GLTF/GLB for interoperable 3D asset delivery.
- Optimize 3D assets before shipping them to production.

Do not add a physics engine or post-processing library simply because it is available.

---

## 6. Animation and Motion

### Animation libraries

| Library | Purpose | Official resource |
|---|---|---|
| GSAP | Advanced timeline and interaction animation | [gsap.com](https://gsap.com/) |
| Motion | Animation for React and JavaScript | [motion.dev](https://motion.dev/) |
| React Spring | Physics-based animation | [react-spring.dev](https://www.react-spring.dev/) |
| Anime.js | JavaScript animation engine | [animejs.com](https://animejs.com/) |
| Lottie | Animation playback | [lottiefiles.com](https://lottiefiles.com/) |
| Rive | Interactive real-time animation | [rive.app](https://rive.app/) |
| Theatre.js | Visual animation authoring and sequencing | [theatrejs.com](https://www.theatrejs.com/) |
| Lenis | Smooth scrolling library | [github.com/darkroomengineering/lenis](https://github.com/darkroomengineering/lenis) |

### Selection guidance

- Use CSS transitions for simple hover and state changes.
- Use Motion for declarative React animations and layout transitions.
- Use GSAP for complex timelines, scroll-driven sequences, and detailed control.
- Use Rive for interactive state-driven vector animations.
- Use Lottie when an existing Lottie animation needs playback.
- Use Theatre.js when visual authoring and precise 3D animation sequencing are useful.
- Use Lenis only when the project benefits from its scrolling behavior.

Do not combine multiple animation engines without understanding how their animation loops, scroll systems, and lifecycle management interact.

Always respect reduced-motion preferences.

---

## 7. State Management and Data Fetching

### State management

| Library | Purpose | Official resource |
|---|---|---|
| Zustand | Lightweight state management | [zustand.docs.pmnd.rs](https://zustand.docs.pmnd.rs/) |
| Redux Toolkit | Structured application state management | [redux-toolkit.js.org](https://redux-toolkit.js.org/) |
| Jotai | Atomic state management | [jotai.org](https://jotai.org/) |
| Valtio | Proxy-based state management | [valtio.dev](https://valtio.dev/) |
| XState | State machines and statecharts | [stately.ai](https://stately.ai/) |
| TanStack Store | Reactive state management | [tanstack.com/store](https://tanstack.com/store/latest) |

### Server state and data fetching

| Library | Purpose | Official resource |
|---|---|---|
| TanStack Query | Server-state management | [tanstack.com/query](https://tanstack.com/query/latest) |
| SWR | React data fetching | [swr.vercel.app](https://swr.vercel.app/) |
| Apollo Client | GraphQL data management | [apollographql.com](https://www.apollographql.com/docs/react/) |
| urql | GraphQL client | [urql.dev](https://urql.dev/) |
| tRPC | End-to-end typesafe APIs | [trpc.io](https://trpc.io/) |

**Selection guidance**

- Start with framework-native state where possible.
- Use Zustand for straightforward shared client state.
- Use Redux Toolkit for applications that benefit from its structured state and tooling.
- Use TanStack Query for server-state fetching, caching, and synchronization.
- Use SWR when its data-fetching model fits the application.
- Keep client state and server state conceptually separate.

---

## 8. Forms and Validation

| Library | Purpose | Official resource |
|---|---|---|
| React Hook Form | Form state and validation integration | [react-hook-form.com](https://react-hook-form.com/) |
| TanStack Form | Type-safe form state management | [tanstack.com/form](https://tanstack.com/form/latest) |
| Formik | React form management | [formik.org](https://formik.org/) |
| Zod | TypeScript-first schema validation | [zod.dev](https://zod.dev/) |
| Valibot | Modular schema validation | [valibot.dev](https://valibot.dev/) |
| Yup | JavaScript schema validation | [github.com/jquense/yup](https://github.com/jquense/yup) |

**Selection guidance**

- Use React Hook Form for efficient form state management.
- Consider TanStack Form for type-safe, composable form architectures.
- Use Zod or another compatible schema library for structured validation.
- Validate important data on the server even when client-side validation exists.
- Keep error messages accessible and understandable.

---

## 9. Testing and Quality Assurance

### Testing frameworks

| Tool | Purpose | Official resource |
|---|---|---|
| Vitest | Unit and integration testing | [vitest.dev](https://vitest.dev/) |
| Jest | JavaScript testing framework | [jestjs.io](https://jestjs.io/) |
| Playwright | Browser automation and end-to-end testing | [playwright.dev](https://playwright.dev/) |
| Cypress | End-to-end and component testing | [cypress.io](https://www.cypress.io/) |
| Testing Library | User-oriented component testing | [testing-library.com](https://testing-library.com/) |
| Storybook Test | Component interaction and visual testing workflows | [storybook.js.org](https://storybook.js.org/) |

### Accessibility testing

| Tool | Purpose | Official resource |
|---|---|---|
| axe-core | Automated accessibility testing engine | [github.com/dequelabs/axe-core](https://github.com/dequelabs/axe-core) |
| Lighthouse | Accessibility and performance auditing | [developer.chrome.com/docs/lighthouse](https://developer.chrome.com/docs/lighthouse/) |
| WAVE | Web accessibility evaluation | [wave.webaim.org](https://wave.webaim.org/) |

### Code quality

| Tool | Purpose | Official resource |
|---|---|---|
| ESLint | JavaScript and TypeScript linting | [eslint.org](https://eslint.org/) |
| Prettier | Code formatting | [prettier.io](https://prettier.io/) |
| Biome | Formatting and linting tools | [biomejs.dev](https://biomejs.dev/) |
| Stylelint | CSS linting | [stylelint.io](https://stylelint.io/) |
| Husky | Git hooks | [typicode.github.io/husky](https://typicode.github.io/husky/) |

**Selection guidance**

Use a testing stack appropriate to the existing project.

A practical React project may use:

- Vitest for unit tests.
- Testing Library for component behavior.
- Playwright for end-to-end testing.
- axe-core for automated accessibility checks.
- ESLint and Prettier for code quality.

Automated testing does not replace manual visual and accessibility review.

---

## 10. Design Systems and Color Tools

| Tool | Purpose | Official resource |
|---|---|---|
| Figma | Interface design and collaboration | [figma.com](https://www.figma.com/) |
| Penpot | Open-source design and prototyping | [penpot.app](https://penpot.app/) |
| Storybook | Component documentation and development | [storybook.js.org](https://storybook.js.org/) |
| Style Dictionary | Design token transformation | [styledictionary.com](https://styledictionary.com/) |
| Tokens Studio | Design token workflows | [tokens.studio](https://tokens.studio/) |
| Coolors | Color palette exploration | [coolors.co](https://coolors.co/) |
| Adobe Color | Color exploration | [color.adobe.com](https://color.adobe.com/) |
| Realtime Colors | Website color visualization | [realtimecolors.com](https://www.realtimecolors.com/) |
| WebAIM Contrast Checker | Contrast evaluation | [webaim.org](https://webaim.org/resources/contrastchecker/) |

### Typography resources

| Resource | Purpose | Official resource |
|---|---|---|
| Google Fonts | Open font discovery | [fonts.google.com](https://fonts.google.com/) |
| Fontsource | Self-hostable web fonts | [fontsource.org](https://fontsource.org/) |
| Font Squirrel | Font discovery and tools | [fontsquirrel.com](https://www.fontsquirrel.com/) |

For multilingual interfaces, verify glyph coverage for all required writing systems, including Assamese, Bengali, and other Indic scripts where applicable.

Do not assume that every font supports every language.

---

## 11. Image, Icon and Asset Resources

### Image resources

| Resource | Purpose | Official resource |
|---|---|---|
| Unsplash | Photography | [unsplash.com](https://unsplash.com/) |
| Pexels | Stock photography and video | [pexels.com](https://www.pexels.com/) |
| Pixabay | Images, illustrations and media | [pixabay.com](https://pixabay.com/) |
| Openverse | Search for openly licensed media | [openverse.org](https://openverse.org/) |
| SVG Repo | SVG icon and illustration discovery | [svgrepo.com](https://www.svgrepo.com/) |

### 3D and material assets

| Resource | Purpose | Official resource |
|---|---|---|
| Poly Haven | HDRIs, textures and 3D assets | [polyhaven.com](https://polyhaven.com/) |
| Sketchfab | 3D model discovery | [sketchfab.com](https://sketchfab.com/) |
| ambientCG | PBR materials and textures | [ambientcg.com](https://ambientcg.com/) |
| Kenney | Game assets and models | [kenney.nl](https://kenney.nl/) |
| Quaternius | 3D models and game assets | [quaternius.com](https://quaternius.com/) |

**Important:** Never assume that an asset is free for every use merely because it can be downloaded without payment.

Check the individual asset's license, attribution requirements, redistribution conditions, and commercial-use permissions before including it in a project.

---

## 12. Performance and Optimization Tools

| Tool | Purpose | Official resource |
|---|---|---|
| Lighthouse | Website performance auditing | [developer.chrome.com/docs/lighthouse](https://developer.chrome.com/docs/lighthouse/) |
| PageSpeed Insights | Web performance reports | [pagespeed.web.dev](https://pagespeed.web.dev/) |
| WebPageTest | Detailed performance testing | [webpagetest.org](https://www.webpagetest.org/) |
| Chrome DevTools | Browser performance profiling | [developer.chrome.com/docs/devtools](https://developer.chrome.com/docs/devtools/) |
| Bundle Analyzer | Build bundle inspection | [github.com/webpack-contrib/webpack-bundle-analyzer](https://github.com/webpack-contrib/webpack-bundle-analyzer) |
| Squoosh | Image compression | [squoosh.app](https://squoosh.app/) |
| Sharp | Image processing | [sharp.pixelplumbing.com](https://sharp.pixelplumbing.com/) |
| Vercel Speed Insights | Real-user performance monitoring | [vercel.com/docs/speed-insights](https://vercel.com/docs/speed-insights) |

Use performance tools to establish baselines, identify bottlenecks, and verify improvements.

Avoid optimizing based only on assumptions or development-mode measurements.

---

## 13. Backend and API Integration

Modern frontend applications often depend on backend services.

| Technology | Purpose | Official resource |
|---|---|---|
| Supabase | Backend platform with database and authentication | [supabase.com](https://supabase.com/docs) |
| Firebase | Application development platform | [firebase.google.com](https://firebase.google.com/docs) |
| Appwrite | Open-source backend platform | [appwrite.io](https://appwrite.io/docs) |
| Convex | Reactive backend platform | [convex.dev](https://docs.convex.dev/) |
| Hono | Lightweight web framework | [hono.dev](https://hono.dev/) |
| Fastify | High-performance Node.js framework | [fastify.dev](https://fastify.dev/) |
| Express | Node.js web framework | [expressjs.com](https://expressjs.com/) |
| Prisma | Database ORM | [prisma.io](https://www.prisma.io/docs) |
| Drizzle ORM | TypeScript ORM | [orm.drizzle.team](https://orm.drizzle.team/) |

Choose backend technologies based on product requirements, infrastructure, data model, security, and operational constraints.

Never expose private API keys or server credentials in browser-delivered code.

---

## 14. Hosting and Deployment

| Platform | Purpose | Official resource |
|---|---|---|
| Vercel | Frontend deployment platform | [vercel.com](https://vercel.com/docs) |
| Netlify | Web application hosting | [netlify.com](https://docs.netlify.com/) |
| Cloudflare Pages | Frontend deployment | [developers.cloudflare.com/pages](https://developers.cloudflare.com/pages/) |
| Cloudflare Workers | Serverless application runtime | [developers.cloudflare.com/workers](https://developers.cloudflare.com/workers/) |
| Railway | Application infrastructure platform | [docs.railway.com](https://docs.railway.com/) |
| Render | Application hosting | [render.com](https://render.com/docs) |
| Fly.io | Application deployment platform | [fly.io](https://fly.io/docs/) |
| GitHub Actions | CI/CD automation | [docs.github.com/actions](https://docs.github.com/en/actions) |

Select deployment infrastructure based on application architecture, resource requirements, geographic needs, cost, and operational constraints.

---

## 15. Developer Experience and Utilities

| Tool | Purpose | Official resource |
|---|---|---|
| VS Code | Code editor | [code.visualstudio.com](https://code.visualstudio.com/) |
| Git | Version control | [git-scm.com](https://git-scm.com/) |
| GitHub | Source hosting and collaboration | [github.com](https://github.com/) |
| npm | JavaScript package management | [npmjs.com](https://www.npmjs.com/) |
| Changesets | Versioning and changelog management | [github.com/changesets/changesets](https://github.com/changesets/changesets) |
| Dev Containers | Reproducible development environments | [containers.dev](https://containers.dev/) |
| Storybook | Component development environment | [storybook.js.org](https://storybook.js.org/) |
| Figma | Interface design and collaboration | [figma.com](https://www.figma.com/) |

---

## 16. Learning and Reference Resources

### Frontend engineering

- [MDN Web Docs](https://developer.mozilla.org/) — Web platform documentation.
- [web.dev](https://web.dev/) — Web development and performance guidance.
- [React Documentation](https://react.dev/learn) — React fundamentals.
- [Next.js Learn](https://nextjs.org/learn) — Next.js learning materials.
- [TypeScript Handbook](https://www.typescriptlang.org/docs/handbook/intro.html) — TypeScript reference.

### 3D web development

- [Three.js Documentation](https://threejs.org/docs/) — Three.js API reference.
- [Three.js Examples](https://threejs.org/examples/) — Demonstrations and techniques.
- [React Three Fiber Documentation](https://r3f.docs.pmnd.rs/) — React-based 3D development.
- [Discover Three.js](https://discoverthreejs.com/) — Three.js learning resource.
- [The Book of Shaders](https://thebookofshaders.com/) — GLSL and shader fundamentals.
- [Khronos glTF](https://www.khronos.org/gltf/) — 3D asset format documentation.

### Design and accessibility

- [WCAG](https://www.w3.org/WAI/standards-guidelines/wcag/) — Accessibility guidelines.
- [WAI-ARIA Authoring Practices](https://www.w3.org/WAI/ARIA/apg/) — Accessible interaction patterns.
- [A11Y Project](https://www.a11yproject.com/) — Accessibility knowledge base.
- [Nielsen Norman Group](https://www.nngroup.com/) — UX research and usability guidance.

---

## 17. Recommended Technology Combinations

These combinations are starting points, not mandatory stacks.

### Modern SaaS application

| Layer | Suggested technology |
|---|---|
| Framework | Next.js |
| Language | TypeScript |
| Styling | Tailwind CSS |
| UI components | shadcn/ui |
| Icons | Lucide |
| Forms | React Hook Form |
| Validation | Zod |
| Server state | TanStack Query where needed |
| Testing | Vitest and Playwright |
| Deployment | Vercel or another suitable platform |

### Immersive 3D landing page

| Layer | Suggested technology |
|---|---|
| Framework | React or Next.js |
| Language | TypeScript |
| Styling | Tailwind CSS or CSS Modules |
| 3D engine | Three.js |
| React 3D renderer | React Three Fiber |
| 3D helpers | Drei |
| Animation | GSAP or Motion |
| Scroll | Native scrolling or Lenis when justified |
| 3D assets | GLTF/GLB |
| Optimization | glTF Transform and browser profiling |

### Interactive product showcase

| Layer | Suggested technology |
|---|---|
| Framework | React |
| Styling | CSS or Tailwind CSS |
| UI components | Radix UI or shadcn/ui |
| 3D rendering | Three.js or React Three Fiber |
| Animation | Motion or GSAP |
| State | Local React state or Zustand |
| Asset format | GLB |
| Testing | Playwright |
| Performance | Chrome DevTools and Lighthouse |

### Content-focused website

| Layer | Suggested technology |
|---|---|
| Framework | Astro |
| Styling | CSS or Tailwind CSS |
| Content | Markdown or MDX |
| Interactivity | Selective client-side components |
| Typography | Optimized web fonts |
| Deployment | Static hosting or a suitable edge platform |

---

## 18. AI Coding Agent Library Selection Workflow

When implementing a feature, follow this process.

### Step 1: Identify the requirement

Example:

The project requires a responsive product gallery with image transitions and a 3D product preview.

### Step 2: Inspect existing dependencies

Check:

- Framework.
- Existing UI library.
- Animation system.
- 3D rendering system.
- State management.
- Available asset formats.

### Step 3: Identify the smallest suitable solution

Possible choices:

- CSS for basic transitions.
- Motion for React animation.
- Three.js for custom 3D rendering.
- React Three Fiber for React-based 3D scenes.

### Step 4: Verify compatibility

Check the official documentation for:

- Installation.
- Supported framework versions.
- Runtime requirements.
- Integration instructions.
- Known limitations.

### Step 5: Evaluate trade-offs

Consider:

- Bundle size.
- Runtime performance.
- Maintenance.
- Licensing.
- Accessibility.
- Developer experience.
- Long-term complexity.

### Step 6: Implement and validate

- Follow official documentation.
- Reuse existing project conventions.
- Avoid duplicate functionality.
- Test the integration.
- Review responsive behavior.
- Measure performance when relevant.

### Step 7: Document the decision

Record significant technology choices and why they were made.

---

## 19. Library Maintenance and Contribution Guidelines

This directory should remain useful as the ecosystem evolves.

Contributors should:

- Prefer official project websites and documentation.
- Provide working links.
- Use accurate descriptions.
- Avoid duplicate entries.
- Remove abandoned or irrelevant projects when appropriate.
- Identify deprecated technologies.
- Distinguish frameworks from libraries and tools.
- Mention important compatibility considerations.
- Check license and redistribution terms.
- Keep descriptions concise and practical.

A library should not be presented as actively maintained without reasonable evidence.

Do not add technologies solely because they are popular or frequently mentioned in online discussions.

## 20. Disclaimer

This resource directory is provided for educational and development purposes.

Technology availability, documentation, maintenance status, licensing, pricing, and compatibility may change.

Always consult official documentation and current project information before adopting a dependency.

The inclusion of a project does not imply endorsement, affiliation, sponsorship, or ownership by AxomiyaIndie.

---

**Maintained by [AxomiyaIndie](https://github.com/axomiyaindie)**

[Back to the repository](../README.md)