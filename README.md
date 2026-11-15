# Agentic Frontend & 3D Web Playbook

![Agentic Frontend & 3D Web Playbook](assets/brand/logo.svg)

**An open-source engineering knowledge base and skill collection for AI-assisted frontend development, immersive 3D websites, and interactive web experiences.**

[Documentation](#documentation) · [Developer Toolkit](#developer-toolkit) · [AI Agent Skills](#ai-agent-skills) · [How to Use](#how-to-use-this-repository) · [Project Blueprints](#project-blueprints) · [Contributing](CONTRIBUTING.md)

---

## What Is This?

The **Agentic Frontend & 3D Web Playbook** is an open-source resource for developers who use AI coding agents to design, build, improve, and maintain frontend applications.

It provides structured engineering knowledge, practical implementation guidance, reusable AI agent skills, curated developer resources, and project blueprints that help AI agents work more systematically.

Instead of asking an AI agent to build an entire website from a vague prompt, developers can provide relevant engineering instructions, technical references, design principles, and specialized skills.

The goal is to improve the quality of AI-generated frontend work through better planning, architecture, implementation, visual review, accessibility, testing, and performance optimization.

This repository is designed to work alongside AI coding tools such as Claude Code, Cursor, GitHub Copilot, OpenAI Codex, Gemini CLI, and other compatible AI development agents.

Exact instruction and skill-loading capabilities depend on the coding agent being used.

## Why Does It Exist?

AI coding agents can generate code, but good frontend engineering requires more than code generation.

Developers frequently encounter problems such as:

- Generic website designs that lack visual identity.
- Poor component architecture and inconsistent design systems.
- Incorrect use of frontend frameworks and libraries.
- Broken responsive layouts and mobile experiences.
- Unnecessary animations and poor interaction design.
- Inefficient Three.js and WebGL implementations.
- Excessive rendering costs and GPU performance problems.
- Inaccessible interfaces and incomplete interaction states.
- Insufficient testing and visual quality assurance.
- AI agents modifying existing code without understanding the project.

This playbook provides reusable guidance to address these challenges.

It encourages AI agents to inspect, plan, implement, test, review, and optimize instead of immediately generating large amounts of code.

## Who Should Use This Repository?

### Developers Using AI Coding Agents

Use the documentation and skills to give coding agents better engineering instructions when building applications.

### Frontend Developers

Use the guides as practical references for React, Next.js, TypeScript, responsive design, component architecture, and modern frontend engineering.

### Creative Developers

Explore the 3D web, shader, animation, and interaction documentation when building immersive websites and interactive browser experiences.

### Design Engineers

Use the design system, typography, color, component, and visual review guidance to translate design ideas into high-quality interfaces.

### AI Agent Skill Authors

Explore existing skills as examples and contribute additional reusable instructions for specialized frontend development tasks.

## What Can You Do With It?

| Your task | What to use |
|---|---|
| Build a SaaS website | Frontend fundamentals, design systems, premium landing page skill |
| Create a 3D portfolio | Three.js, React Three Fiber, 3D scene builder skill |
| Build an interactive product page | 3D web guides, animation guides, product showcase blueprint |
| Improve an existing frontend | Frontend architecture, implementation workflow |
| Fix responsive problems | Responsive design guide, frontend visual audit skill |
| Improve website animations | GSAP, Motion, scroll experiences |
| Review website design quality | Visual review workflow, frontend visual audit skill |
| Optimize a 3D website | Three.js optimization, shaders, performance guidance |
| Create reusable components | Design systems and component documentation |
| Discover development tools | Developer Toolkit |
| Plan a frontend project | Planning workflow and relevant project blueprint |

---

## How to Use This Repository

You do not need to install a package or run an application to use this repository. It is primarily a documentation and AI agent instruction resource.

There are several ways to use it.

### Method 1: Use It as a Development Reference

If you are developing a frontend application yourself:

1. Clone or browse the repository.
2. Identify the engineering problem you are solving.
3. Open the relevant documentation.
4. Apply the recommendations to your project.
5. Use the examples as implementation references.
6. Validate the result through testing and visual inspection.

For example, if you are building a Three.js website, start with the Three.js guide, then review React Three Fiber, optimization, and the 3D scene builder skill.

### Method 2: Use It With an AI Coding Agent

This is one of the primary intended use cases.

Clone the repository:

```bash
git clone https://github.com/axomiyaindie/agentic-frontend-playbook.git

cd agentic-frontend-playbook
```

Your application should remain in its own project directory. You can keep this playbook as a separate reference repository or include relevant documentation in your development workspace.

Give your AI coding agent access to:

- `AGENTS.md` for general engineering instructions.
- Relevant documentation for the technology or task.
- The appropriate `SKILL.md` for specialized instructions.
- An example blueprint when starting a similar project.
- Developer Toolkit references when selecting tools and libraries.

The agent should use these materials as engineering guidance rather than blindly copying every recommendation.

#### Example: Building a Premium 3D Portfolio

Give your coding agent a task like this:

```text
I want to build a premium 3D portfolio website.

Use the Agentic Frontend & 3D Web Playbook as an
engineering reference.

Before implementation:

1. Inspect my existing project and dependencies.
2. Read the general AGENTS.md instructions.
3. Review the 3D portfolio project blueprint.
4. Read the premium-landing-page skill.
5. Read the 3d-scene-builder skill.
6. Review the relevant Three.js and React Three Fiber guides.
7. Create a clear implementation plan.

During implementation:

- Follow the existing project architecture.
- Build reusable components.
- Establish a consistent design system.
- Make the experience responsive.
- Implement meaningful interactions and animations.
- Optimize the 3D scene for performance.
- Include accessible fallbacks.

After implementation:

- Run available checks and tests.
- Review responsive behavior.
- Inspect the rendered interface when browser
  or screenshot tools are available.
- Identify and fix visual and performance issues.

Do not claim that something has been visually tested
unless you have actually inspected the rendered result.
```

### Method 3: Use Individual AI Agent Skills

You can use the skills independently for specialized tasks.

For example:

- Before building a landing page, load `skills/premium-landing-page/SKILL.md`.
- Before implementing a 3D scene, load `skills/3d-scene-builder/SKILL.md`.
- When reviewing an existing interface, load `skills/frontend-visual-audit/SKILL.md`.

If your coding agent supports the Agent Skills format, configure the skills using its documented skill-discovery mechanism. Otherwise, provide the `SKILL.md` content as a reference or instruction file.

You do not need to use all three skills for every project.

### Method 4: Use the Project Blueprints

The `examples/` documentation contains detailed blueprints for common frontend projects.

These blueprints help you define:

- Product requirements.
- Visual direction.
- Page structure.
- Technology choices.
- Component architecture.
- Interactions and animations.
- Responsive behavior.
- Performance requirements.
- Accessibility requirements.
- Implementation milestones.
- Completion criteria.

You can use a blueprint to start a new project or adapt its ideas to an existing application.

The blueprints describe proposed implementations. They are not prebuilt, production-ready applications.

---

## AI Agent Skills

Skills are reusable instructions that give an AI coding agent a focused workflow for a particular development task.

This repository currently includes three skills.

### 1. 3D Scene Builder

[Read the 3D Scene Builder Skill](skills/3d-scene-builder/SKILL.md)

**Purpose:** Help AI agents design and implement interactive 3D scenes for web applications.

Use it when:

- Creating a Three.js scene.
- Building with React Three Fiber.
- Planning cameras, geometry, materials, and lighting.
- Implementing 3D interactions.
- Optimizing rendering and GPU performance.
- Adding mobile-friendly fallbacks.

### 2. Premium Landing Page

[Read the Premium Landing Page Skill](skills/premium-landing-page/SKILL.md)

**Purpose:** Guide AI agents through the design and implementation of high-quality marketing websites and landing pages.

Use it when:

- Building a SaaS landing page.
- Creating a product marketing website.
- Developing a premium portfolio.
- Establishing typography and visual hierarchy.
- Designing responsive sections.
- Implementing purposeful animations.
- Reviewing the overall website experience.

### 3. Frontend Visual Audit

[Read the Frontend Visual Audit Skill](skills/frontend-visual-audit/SKILL.md)

**Purpose:** Help AI agents evaluate frontend interfaces and identify visual, usability, and responsive problems.

Use it when:

- Reviewing an existing website.
- Finding layout and spacing inconsistencies.
- Checking typography and color usage.
- Inspecting responsive behavior.
- Identifying accessibility problems.
- Prioritizing visual improvements.
- Reviewing a completed implementation.

Skills follow the general [Agent Skills specification](https://agentskills.io/specification).

---

## Documentation

The documentation is organized around the engineering areas involved in building modern frontend and 3D web experiences.

### Fundamentals

Start here when working on the foundations of a frontend application.

- [Design Principles](fundamentals/design-principles.md) — usability, visual hierarchy, consistency, accessibility, and design quality.
- [Frontend Architecture](fundamentals/frontend-architecture.md) — application structure, components, state management, routing, and maintainability.
- [Responsive Design](fundamentals/responsive-design.md) — mobile-first development, adaptive layouts, breakpoints, and responsive interfaces.

### 3D Web Development

Use these guides when building browser-based 3D experiences.

- [Three.js](3d-web/threejs.md) — scenes, cameras, geometry, materials, lights, and rendering.
- [React Three Fiber](3d-web/react-three-fiber.md) — declarative 3D development with React and Drei.
- [Shaders](3d-web/shaders.md) — GLSL, GPU programming, shader materials, and visual effects.
- [3D Optimization](3d-web/optimization.md) — rendering performance, draw calls, textures, geometry, and mobile optimization.

### Animation and Interaction

Use these guides to create meaningful movement and interactive experiences.

- [GSAP](animation/gsap.md) — timelines, tweens, easing, stagger effects, and ScrollTrigger.
- [Motion](animation/motion.md) — React animations, gestures, transitions, layout animations, and orchestration.
- [Scroll Experiences](animation/scroll-experiences.md) — scroll-triggered animations, parallax, pinned sections, and 3D scroll experiences.

### Design Systems

Use these resources to establish visual consistency and reusable interface patterns.

- [Colors](design-systems/colors.md) — color theory, palettes, semantic tokens, gradients, and dark mode.
- [Typography](design-systems/typography.md) — type scales, font pairing, responsive typography, and multilingual text.
- [Components](design-systems/components.md) — component architecture, variants, states, composition, and accessibility.

### Agentic Development Workflows

Use these workflows to guide AI agents through the development lifecycle.

- [Planning](agent-workflows/planning.md) — understand requirements, inspect projects, plan architecture, and define acceptance criteria.
- [Implementation](agent-workflows/implementation.md) — implement frontend features systematically while preserving existing architecture.
- [Visual Review](agent-workflows/visual-review.md) — inspect rendered interfaces, identify issues, and validate visual quality.
- [Optimization](agent-workflows/optimization.md) — profile performance and improve frontend and 3D rendering efficiency.

### Resources

Discover tools, libraries, references, and inspiration.

- [Libraries and Tools](resources/libraries.md) — frontend frameworks, styling systems, UI libraries, 3D tools, animation libraries, and development utilities.
- [Design Inspiration](resources/inspiration.md) — website galleries, design references, creative studios, 3D showcases, and visual inspiration.
- [Developer Toolkit](resources/toolkit/README.md) — curated websites, open-source repositories, AI development tools, frontend utilities, design resources, and more.

---

## Developer Toolkit

The Developer Toolkit is a curated collection of useful websites, developer tools, open-source projects, libraries, and resources for modern frontend and creative web development.

Each resource includes a short explanation of what it does and how it can help developers.

Explore the categories:

| Category | Description |
|---|---|
| [Frontend Tools](resources/toolkit/frontend-tools.md) | Frontend frameworks, UI libraries, component systems, state management, and testing tools. |
| [3D Web Tools](resources/toolkit/3d-web-tools.md) | Three.js ecosystem, 3D frameworks, asset pipelines, model viewers, and 3D asset libraries. |
| [Animation Tools](resources/toolkit/animation-tools.md) | Animation libraries, motion systems, scroll tools, and interactive animation platforms. |
| [AI Development](resources/toolkit/ai-development.md) | AI coding agents, developer assistants, agent frameworks, and AI development infrastructure. |
| [Design Resources](resources/toolkit/design-resources.md) | Design tools, icon libraries, typography, color resources, and visual inspiration. |
| [Utilities](resources/toolkit/utilities.md) | Performance, accessibility, testing, optimization, image processing, and developer utilities. |

The toolkit is intended to be an evolving resource. Contributions that improve accuracy, usefulness, and discoverability are welcome.

---

## Project Blueprints

These are detailed project references designed to help developers and AI agents plan and build specific types of applications.

### 3D Portfolio

[Explore the 3D Portfolio Blueprint](examples/3d-portfolio/README.md)

A creative portfolio concept featuring interactive 3D scenes, personal branding, project showcases, responsive layouts, and immersive interactions.

### SaaS Landing Page

[Explore the SaaS Landing Page Blueprint](examples/saas-landing-page/README.md)

A complete marketing website concept covering product positioning, landing page structure, features, pricing, design systems, responsiveness, SEO, and conversion considerations.

The blueprint uses a fictional product named Flowbase.

### 3D Product Showcase

[Explore the Product Showcase Blueprint](examples/product-showcase/README.md)

An interactive product presentation concept featuring 3D product visualization, lighting, materials, product hotspots, variants, and performance optimization.

The blueprint uses a fictional product named AURORA ONE.

---

## Recommended Development Workflow

The playbook encourages a structured development process.

A typical AI-assisted frontend project can follow this sequence:

1. **Understand:** Define the product, users, requirements, and constraints.
2. **Inspect:** Examine the existing project, dependencies, architecture, and conventions.
3. **Plan:** Choose the implementation approach, design direction, and technology.
4. **Design:** Establish the visual system, page structure, components, and interactions.
5. **Implement:** Build in focused, reviewable steps.
6. **Validate:** Run tests, check accessibility, and inspect responsive behavior.
7. **Review:** Compare the rendered result with the intended design.
8. **Optimize:** Improve performance, loading, rendering, and maintainability.

Not every project needs every specialized guide or skill. Select the material relevant to the actual task.

---

## Technology Coverage

The repository covers and references technologies across the frontend and creative development ecosystem.

| Area | Technologies |
|---|---|
| Frontend | React, Next.js, TypeScript |
| Styling | CSS, Tailwind CSS, modern CSS |
| 3D Web | Three.js, React Three Fiber, Drei, WebGL |
| Shaders | GLSL, ShaderMaterial |
| Animation | GSAP, Motion |
| Design Systems | Design tokens, CSS variables, reusable components |
| Testing | Playwright, Vitest, accessibility tools |
| Performance | Lighthouse, browser profiling, Core Web Vitals |
| AI Development | Agent instructions, reusable skills, structured workflows |

The repository is technology-aware but not tied to a single framework or mandatory stack.

---

## Contributing

This project is open source and welcomes contributions from developers, designers, creative coders, and AI tooling enthusiasts.

You can contribute by:

- Writing new frontend engineering guides.
- Improving existing technical documentation.
- Creating additional AI agent skills.
- Adding practical project blueprints.
- Improving 3D web and WebGL guidance.
- Updating library and tool references.
- Reporting inaccurate information and broken links.
- Improving accessibility, testing, and performance guidance.

Read [CONTRIBUTING.md](CONTRIBUTING.md) for contribution instructions.

---

## Roadmap

### Completed

- [x] Establish the repository and documentation structure.
- [x] Create frontend engineering fundamentals.
- [x] Add Three.js and React Three Fiber documentation.
- [x] Add shader and 3D optimization guidance.
- [x] Add GSAP, Motion, and scroll experience guides.
- [x] Create design system documentation.
- [x] Document AI agent development workflows.
- [x] Create initial reusable AI agent skills.
- [x] Add three detailed project blueprints.
- [x] Publish curated libraries and inspiration resources.
- [x] Add a categorized Developer Toolkit.

### Planned

- [ ] Expand the reusable AI agent skill collection.
- [ ] Add more implementation-ready examples.
- [ ] Introduce automated documentation and skill validation.
- [ ] Improve continuous integration and quality checks.
- [ ] Expand visual testing and accessibility resources.
- [ ] Add more practical frontend and 3D implementation patterns.

---

## License

This project is licensed under the [MIT License](LICENSE).

You are free to use, modify, distribute, and adapt the materials under the terms of the license.

---

Contributions, suggestions, and feedback are welcome.

**Build better interfaces. Create immersive experiences. Engineer with AI.**