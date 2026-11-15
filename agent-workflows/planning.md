# AI Agent Planning Workflow

A reliable AI coding agent should plan before implementing.

Whether building a modern frontend application, an immersive 3D website, an interactive product experience, or a reusable component system, a structured planning process reduces unnecessary rework and improves implementation quality.

This guide defines a practical planning workflow for AI coding agents working on frontend engineering and 3D web development projects.

## 1. Why Planning Matters

Without planning, coding agents can:

- Modify the wrong files.
- Duplicate existing functionality.
- Introduce unnecessary dependencies.
- Ignore existing architecture.
- Build components that do not match the design system.
- Miss responsive requirements.
- Overlook accessibility.
- Introduce performance problems.
- Implement only part of the requested functionality.
- Make assumptions that conflict with project requirements.

Planning helps agents understand what needs to be built, why it is needed, how it should fit into the existing application, and how success will be verified.

The goal is not to create lengthy plans for every small change.

The goal is to use enough planning to make implementation predictable.

## 2. Planning Principles

Every planning workflow should follow these principles.

### Understand before modifying

Inspect the request and existing project before changing files.

### Reuse before rebuilding

Identify existing components, utilities, design tokens, and architectural patterns before introducing new ones.

### Prefer simplicity

Choose the simplest architecture that satisfies the requirements.

### Make assumptions explicit

Identify missing information and distinguish confirmed requirements from assumptions.

### Plan for quality

Consider accessibility, responsiveness, performance, maintainability, and testing from the beginning.

### Keep plans actionable

A useful plan identifies concrete implementation steps and expected outcomes.

### Adapt planning depth

A small bug fix does not need the same planning process as a complete application.

## 3. Understand the Request

The first task is to understand what the user actually wants.

Extract the following information:

| Category | Questions |
|---|---|
| Objective | What problem should be solved? |
| Users | Who will use the experience? |
| Platform | Web, mobile web, desktop, or another target? |
| Framework | Which technology stack is required? |
| Features | What functionality must exist? |
| Design | What visual direction is expected? |
| Interactions | What should happen when users interact? |
| Constraints | Are there technical or business restrictions? |
| Quality | What performance and accessibility standards matter? |
| Delivery | What should be completed and verified? |

### Separate requirements by priority

Organize requirements into three groups:

**Must have**

Essential requirements without which the task is incomplete.

**Should have**

Important improvements that contribute to quality.

**Could have**

Optional enhancements that can be implemented if time and scope permit.

Do not silently turn optional ideas into mandatory project requirements.

## 4. Clarify Ambiguity

Before implementation, identify important missing information.

Examples:

- The requested page has no defined content.
- The design reference is unavailable.
- The expected interaction is unclear.
- The project framework is unknown.
- A backend integration has no defined API contract.
- A 3D experience has no defined mobile fallback.

Ask concise questions when missing information materially affects the implementation.

Do not ask questions whose answers can be reliably discovered by inspecting the repository.

When a reasonable assumption is sufficient, document it and proceed if the task allows.

Avoid inventing product requirements, API behavior, business logic, or visual references.

## 5. Inspect the Existing Repository

For existing projects, repository inspection should happen before architecture decisions.

### Inspect project structure

Identify:

- Application entry points.
- Routing structure.
- Shared components.
- Feature directories.
- Styling architecture.
- Static assets.
- Configuration files.
- Existing tests.
- Build and deployment configuration.

### Inspect project dependencies

Review:

- `package.json`.
- Lockfiles.
- Framework versions.
- Installed UI libraries.
- Animation libraries.
- 3D libraries.
- Testing tools.
- Existing utility packages.

Do not assume that a dependency is installed because it is commonly used.

### Inspect existing conventions

Look for:

- Naming conventions.
- Component patterns.
- Import aliases.
- CSS organization.
- TypeScript conventions.
- Error handling.
- State management.
- API communication.
- Test organization.

### Identify reusable functionality

Before building a new component, search for existing equivalents.

Examples:

- Button.
- Modal.
- Navigation.
- Form field.
- Card.
- Loading indicator.
- Animation utility.
- 3D scene wrapper.

Avoid creating duplicate systems without a justified reason.

## 6. Analyze Technical Constraints

Identify the project's technical boundaries.

Common constraints include:

- Framework compatibility.
- Existing package versions.
- Browser support.
- Mobile device limitations.
- Hosting environment.
- API availability.
- Authentication requirements.
- Asset formats.
- Bundle size.
- Rendering requirements.
- Accessibility expectations.

For 3D projects, also consider:

- WebGL or WebGPU support requirements.
- GPU capabilities.
- Scene complexity.
- Texture memory.
- Model size.
- Draw calls.
- Shader complexity.
- Mobile thermal and battery limitations.

A plan should account for actual project constraints instead of assuming ideal hardware or infrastructure.

## 7. Define the Architecture

Choose an architecture that fits the project rather than forcing a preferred stack into every application.

Consider the following layers:

### Application layer

Responsible for routing, page composition, and application-level configuration.

### Feature layer

Contains functionality specific to product domains or application features.

### Component layer

Contains reusable UI elements and composed interface patterns.

### Utility layer

Contains shared helpers, formatting functions, and common logic.

### Data layer

Contains API clients, data fetching, caching, and data transformation.

### Styling layer

Contains design tokens, themes, global styles, and component styles.

A possible structure:

```text
src/
├── app/
├── components/
│   ├── ui/
│   └── layout/
├── features/
│   ├── dashboard/
│   └── authentication/
├── hooks/
├── lib/
├── services/
├── styles/
└── types/
```

This is an example, not a mandatory structure.

Respect the architecture already established by the repository.

## 8. Plan the Visual Experience

Frontend planning should include visual requirements, not just functional requirements.

Identify:

- Overall visual direction.
- Layout structure.
- Page hierarchy.
- Typography system.
- Color palette.
- Spacing scale.
- Component patterns.
- Imagery.
- Icons.
- Motion.
- Responsive behavior.

### Establish visual references

When references are supplied:

1. Inspect the reference carefully.
2. Identify its layout structure.
3. Identify typography and color relationships.
4. Study spacing and alignment.
5. Identify component patterns.
6. Understand interaction behavior.
7. Separate essential design characteristics from decorative details.

Do not claim pixel-perfect accuracy without comparing the implementation against the reference.

### Define visual priorities

Examples:

- Strong first-screen hierarchy.
- Consistent spacing.
- Clear calls to action.
- Readable content.
- Balanced negative space.
- Appropriate image proportions.
- Consistent component styling.

Avoid treating visual polish as a final decoration step.

## 9. Plan Responsive Behavior

Responsive behavior should be considered before implementation.

Identify:

- Target screen sizes.
- Navigation changes.
- Grid behavior.
- Column stacking.
- Typography scaling.
- Image cropping.
- Content overflow.
- Touch interactions.
- Mobile-specific layout changes.

Example planning table:

| Element | Desktop | Tablet | Mobile |
|---|---|---|---|
| Navigation | Full navigation | Compact navigation | Mobile menu |
| Hero | Two columns | Reduced spacing | Stacked |
| Cards | Three columns | Two columns | One column |
| Typography | Large | Medium | Responsive |
| Sidebar | Expanded | Collapsed | Drawer |

These are illustrative decisions. Actual behavior depends on the product.

Do not assume that every responsive design requires the same breakpoints.

## 10. Plan Animation and Interaction

Identify all meaningful interactions before implementation.

Examples:

- Navigation transitions.
- Hover feedback.
- Button interactions.
- Dialog behavior.
- Form validation.
- Scroll-triggered animations.
- Page transitions.
- Drag interactions.
- 3D camera movement.
- Interactive product previews.

For each interaction, define:

1. Trigger.
2. Expected behavior.
3. Visual feedback.
4. Duration and easing, if animated.
5. Keyboard behavior.
6. Reduced-motion behavior.
7. Mobile behavior.
8. Error or fallback behavior.

Avoid adding animation simply because a library is available.

Motion should communicate hierarchy, provide feedback, or support the experience.

## 11. Plan 3D Web Experiences

3D projects need additional planning because rendering introduces significant technical and usability considerations.

### Scene requirements

Define:

- Scene purpose.
- Camera type.
- Camera position.
- Lighting.
- Geometry.
- Materials.
- Environment.
- Assets.
- Interactions.
- Animation.
- Rendering approach.

### Technology selection

Choose based on project requirements.

| Requirement | Possible technology |
|---|---|
| Low-level 3D control | Three.js |
| React-based 3D scenes | React Three Fiber |
| Common 3D helpers | Drei |
| Custom visual effects | GLSL shaders |
| Timeline animation | GSAP |
| React animation | Motion |
| Scroll-controlled scenes | GSAP ScrollTrigger or R3F ScrollControls |

Do not use every library in every project.

### Performance planning

Estimate:

- Model complexity.
- Texture dimensions.
- Draw calls.
- Shadow requirements.
- Post-processing costs.
- Mobile performance.
- Asset loading strategy.

### Fallback planning

Consider what happens when:

- WebGL is unavailable.
- The device cannot handle the scene.
- A model fails to load.
- Network connectivity is poor.
- Reduced motion is enabled.

A 3D experience should not make essential content inaccessible.

## 12. Define Data and Integration Requirements

For applications that depend on external data, identify:

- Data sources.
- API endpoints.
- Request methods.
- Authentication requirements.
- Response structures.
- Loading states.
- Error states.
- Empty states.
- Caching requirements.
- Retry behavior.

Do not invent API endpoints or response fields.

If the API contract is missing, identify the dependency and ask for the required information or use a clearly documented mock when permitted.

Plan how data flows through the application.

Avoid unnecessary duplication of server state in local component state.

## 13. Create an Implementation Breakdown

Convert the project into small, verifiable tasks.

A practical sequence:

1. Inspect the repository.
2. Confirm requirements and constraints.
3. Identify reusable components and utilities.
4. Define architecture.
5. Establish design tokens.
6. Plan page and component structure.
7. Implement core functionality.
8. Implement responsive behavior.
9. Add interaction and animation.
10. Integrate data and assets.
11. Validate accessibility.
12. Optimize performance.
13. Test and review.
14. Document changes.

Adjust the sequence based on dependencies.

For example, API integration may need to happen before implementing data-dependent UI.

## 14. Identify Dependencies and Risks

A good plan identifies work that depends on other work.

Example:

```text
Design tokens
     |
     v
Component system
     |
     v
Page implementation
     |
     v
Interaction and animation
     |
     v
Visual and accessibility review
```

Identify potential risks:

| Risk | Possible mitigation |
|---|---|
| Missing API contract | Confirm contract before integration |
| Large 3D assets | Compress and optimize assets |
| Mobile rendering issues | Test on representative devices |
| Inaccessible dialog | Use a tested dialog primitive |
| Dependency conflicts | Inspect installed versions first |
| Design inconsistency | Use shared design tokens |

Prioritize risks according to likelihood and impact.

## 15. Define Acceptance Criteria

Every task should have a clear definition of done.

Acceptance criteria should be specific and verifiable.

Weak:

- Make the page look good.
- Improve performance.
- Make it responsive.

Better:

- The page renders without runtime errors.
- The navigation works using keyboard and pointer input.
- The layout does not overflow at supported viewport sizes.
- Form validation displays useful error messages.
- Interactive elements have visible focus states.
- The 3D scene has a usable non-WebGL fallback.
- The production build completes successfully.

Not every criterion applies to every task.

Only include relevant requirements.

## 16. Estimate Scope and Prioritize Work

Break work into manageable priorities.

### P0 — Essential

Required for the task to function.

### P1 — Important

Required for a complete and polished result.

### P2 — Enhancement

Optional improvements that can be added after core requirements are satisfied.

For larger projects, also identify:

- High-risk tasks.
- External dependencies.
- Unknowns requiring investigation.
- Work that can happen independently.
- Tasks that should be validated early.

Do not create false precision in time estimates when there is insufficient evidence.

## 17. Plan Testing from the Beginning

Testing should not be an afterthought.

Identify which validation methods are appropriate.

| Test type | Purpose |
|---|---|
| Unit tests | Validate isolated logic |
| Component tests | Validate component behavior |
| Integration tests | Validate connected features |
| End-to-end tests | Validate complete user flows |
| Visual regression | Detect unintended visual changes |
| Accessibility tests | Detect accessibility issues |
| Performance tests | Identify rendering and loading problems |

For frontend projects, consider:

- Navigation.
- Forms.
- Dialogs.
- Responsive layouts.
- Keyboard interaction.
- Error handling.
- Loading states.

For 3D projects, consider:

- Scene initialization.
- Asset loading.
- Rendering fallback.
- Resource cleanup.
- Frame rate.
- Mobile behavior.

Use the tools already available in the project before adding new testing dependencies.

## 18. Write the Plan Before Implementation

For complex tasks, create a short implementation plan.

Recommended format:

```md
# Implementation Plan

## Objective

Describe the requested outcome.

## Existing Architecture

Summarize relevant repository structure and conventions.

## Requirements

### Must have
- Requirement one
- Requirement two

### Should have
- Improvement one

### Could have
- Optional enhancement

## Technical Approach

Explain the selected implementation approach.

## Components and Files

List the expected files and responsibilities.

## Dependencies

List existing or required dependencies.

## Risks and Assumptions

Document unknowns and potential issues.

## Implementation Steps

1. First task
2. Second task
3. Third task

## Validation

- [ ] Functional behavior
- [ ] Responsive behavior
- [ ] Accessibility
- [ ] Performance
- [ ] Build and tests

## Acceptance Criteria

Define measurable completion conditions.
```

For small changes, use a concise checklist rather than generating an unnecessary planning document.

## 19. Example: Planning a Premium 3D Landing Page

Suppose the request is:

"Build a premium landing page for a modern technology product with an interactive 3D hero."

A useful plan might look like this.

### Objective

Create a responsive product landing page with an interactive 3D hero and clear conversion-focused content.

### Requirements

**Must have**

- Responsive navigation.
- Hero section.
- Product messaging.
- Primary call to action.
- 3D visual.
- Feature sections.
- Footer.

**Should have**

- Scroll-based animation.
- Interactive 3D camera movement.
- Responsive image or scene fallback.
- Consistent design tokens.

**Could have**

- Additional product interactions.
- Advanced shader effects.
- Optional transition effects.

### Technical approach

- Inspect existing framework and dependencies.
- Reuse the existing component system.
- Use React Three Fiber if the application uses React and the scene benefits from its declarative model.
- Use Drei for appropriate scene helpers.
- Use Motion or GSAP according to the animation requirements.
- Keep content and essential calls to action available without 3D rendering.

### Implementation steps

1. Inspect project structure.
2. Define visual direction and tokens.
3. Implement navigation and hero layout.
4. Build the 3D scene.
5. Add interaction and animation.
6. Implement remaining sections.
7. Adapt layouts for mobile.
8. Validate accessibility and performance.
9. Run production checks.

### Acceptance criteria

- The landing page renders successfully.
- The primary call to action works.
- The 3D scene loads with a fallback.
- Content remains accessible on mobile.
- Reduced-motion preferences are respected.
- No critical console errors occur.
- The production build succeeds.

This plan is specific enough to guide implementation without prematurely deciding every visual detail.

## 20. AI Agent Planning Checklist

Before implementing a significant frontend task:

### Understanding

- [ ] The objective is clear.
- [ ] User requirements are identified.
- [ ] Important ambiguity is resolved.
- [ ] Assumptions are documented.
- [ ] Scope is understood.

### Repository inspection

- [ ] Existing architecture is inspected.
- [ ] Dependencies are reviewed.
- [ ] Reusable components are identified.
- [ ] Existing conventions are understood.
- [ ] Relevant tests are located.

### Architecture

- [ ] The technical approach is justified.
- [ ] Component responsibilities are clear.
- [ ] Data requirements are understood.
- [ ] Dependencies are identified.
- [ ] Technical risks are considered.

### Experience

- [ ] Visual direction is understood.
- [ ] Responsive behavior is planned.
- [ ] Interaction requirements are defined.
- [ ] Accessibility is considered.
- [ ] Performance constraints are considered.

### Execution

- [ ] Work is divided into actionable steps.
- [ ] Priorities are established.
- [ ] Acceptance criteria are measurable.
- [ ] Validation methods are selected.

## 21. Definition of Done

Planning is complete when the agent can explain:

1. What needs to be built.
2. Why it needs to be built.
3. How it fits into the existing architecture.
4. Which files or components are likely to change.
5. Which dependencies are required.
6. Which risks and assumptions exist.
7. How responsive behavior will work.
8. How accessibility and performance will be addressed.
9. How implementation will be validated.
10. What conditions define successful completion.

A plan should reduce uncertainty and guide implementation.

It should not become an excuse to delay implementation indefinitely.

---

## Related Guides

- [Frontend Architecture](../fundamentals/frontend-architecture.md)
- [Design Principles](../fundamentals/design-principles.md)
- [Responsive Design](../fundamentals/responsive-design.md)
- [Component Architecture](../design-systems/components.md)
- [3D Web Optimization](../3d-web/optimization.md)
- [3D Scene Builder Skill](../skills/3d-scene-builder/SKILL.md)
- [Premium Landing Page Skill](../skills/premium-landing-page/SKILL.md)