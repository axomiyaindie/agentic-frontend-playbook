# AI Agent Implementation Workflow

A successful AI coding agent must do more than generate code.

It must understand the existing application, follow established conventions, implement requirements carefully, preserve working functionality, and verify that its changes behave as expected.

This guide defines a structured implementation workflow for AI coding agents building modern frontend applications, interactive websites, reusable component systems, and immersive 3D web experiences.

## 1. Implementation Principles

Every implementation should follow these principles.

### Understand before changing

Inspect the relevant code before modifying it.

### Respect existing architecture

Follow the project's framework, conventions, folder structure, and established patterns.

### Reuse before rebuilding

Reuse existing components, hooks, utilities, design tokens, and dependencies where appropriate.

### Prefer maintainable solutions

Write understandable code with clear responsibilities rather than clever or unnecessarily complex implementations.

### Implement complete behavior

A visible interface is not complete if its interactions, loading states, errors, or responsive behavior are missing.

### Validate continuously

Test important changes throughout implementation instead of waiting until the end.

### Avoid unrelated changes

Keep modifications focused on the requested scope.

## 2. Prepare the Development Environment

Before implementation, understand the project's environment.

Inspect:

- `package.json`.
- Package lockfile.
- Framework configuration.
- TypeScript configuration.
- Build scripts.
- Existing environment variables.
- Development commands.
- Testing configuration.
- Linting and formatting rules.

Identify the package manager from the existing lockfile.

Common examples:

| Lockfile | Package manager |
|---|---|
| `package-lock.json` | npm |
| `pnpm-lock.yaml` | pnpm |
| `yarn.lock` | Yarn |
| `bun.lock` or `bun.lockb` | Bun |

Do not introduce a different package manager without a reason.

### Verify the starting state

Before modifying files:

1. Check the current Git status.
2. Identify existing uncommitted changes.
3. Avoid overwriting user modifications.
4. Confirm the application can be inspected or started.
5. Identify any existing build or test failures.

Do not assume that every failure was introduced by the current task.

## 3. Follow the Approved Plan

Translate the implementation plan into concrete tasks.

Example:

```text
Task 1: Create shared design tokens
Task 2: Build reusable navigation
Task 3: Implement responsive hero
Task 4: Add product interaction
Task 5: Implement remaining sections
Task 6: Validate accessibility
Task 7: Test production build
```

Implement tasks in dependency order.

For each task:

1. Understand the expected outcome.
2. Identify affected files.
3. Inspect related implementation.
4. Make the smallest coherent change.
5. Verify behavior.
6. Record remaining issues.

Avoid implementing unrelated enhancements simply because they seem interesting.

## 4. Work with Existing Code

An AI agent should treat the existing repository as the source of truth.

Before adding a new implementation:

- Search for an existing component.
- Inspect related utility functions.
- Review the project's design tokens.
- Check existing hooks.
- Review similar pages.
- Inspect current dependencies.
- Understand existing state and data flows.

Prefer extending an existing component when the new behavior belongs naturally to it.

Create a separate component when responsibilities are genuinely different.

Do not replace an established architecture just to match a preferred coding style.

## 5. Organize Frontend Code

Use clear separation of responsibilities.

Example React structure:

```text
src/
├── app/
├── components/
│   ├── ui/
│   └── layout/
├── features/
│   ├── dashboard/
│   └── products/
├── hooks/
├── lib/
├── services/
├── styles/
└── types/
```

The structure should reflect application complexity.

Small applications may need fewer folders. Large applications may benefit from feature-based organization.

### Component responsibilities

A good component should have a clear purpose.

Avoid components that simultaneously:

- Fetch unrelated data.
- Manage global application state.
- Contain extensive business logic.
- Render multiple unrelated page sections.
- Handle unrelated animations.
- Implement complex form validation.

Separate responsibilities when doing so improves clarity and testing.

## 6. Write Maintainable Components

Prefer explicit component interfaces.

Example:

```tsx
type FeatureCardProps = {
  title: string;
  description: string;
  icon?: React.ReactNode;
};

export function FeatureCard({
  title,
  description,
  icon
}: FeatureCardProps) {
  return (
    <article className="feature-card">
      {icon && (
        <div className="feature-card-icon">
          {icon}
        </div>
      )}

      <h3>{title}</h3>
      <p>{description}</p>
    </article>
  );
}
```

### Good component practices

- Use meaningful names.
- Define clear prop types.
- Prefer composition.
- Keep conditional rendering understandable.
- Avoid unnecessary abstraction.
- Keep side effects controlled.
- Handle optional values safely.
- Use semantic HTML.
- Avoid duplicated logic.

### Avoid

- Extremely large components.
- Unclear variable names.
- Deeply nested conditional expressions.
- Unnecessary state.
- Repeated hardcoded design values.
- Uncontrolled DOM manipulation.
- Broad `any` types when meaningful types are possible.

## 7. Manage State Correctly

Choose state management according to the actual problem.

### Local component state

Use for isolated interface behavior.

Examples:

- Dialog visibility.
- Selected tab.
- Expanded accordion.
- Input state.

### Shared application state

Use when multiple unrelated components genuinely need access to the same client-side state.

Possible approaches include:

- React Context.
- Zustand.
- Redux Toolkit.
- Other established project solutions.

### Server state

Treat remote data differently from local UI state.

Consider:

- Loading.
- Error.
- Empty results.
- Caching.
- Refetching.
- Mutations.
- Stale data.
- Optimistic updates where appropriate.

Libraries such as TanStack Query can help manage server state when the project requires them.

Do not introduce global state management for a small local interaction.

## 8. Build Complete Interface States

Every interactive interface should account for its relevant states.

For data-driven interfaces:

1. Loading.
2. Success.
3. Empty.
4. Error.
5. Refreshing.
6. Disabled, where appropriate.

For forms:

1. Initial.
2. Focused.
3. Filled.
4. Invalid.
5. Submitting.
6. Submitted.
7. Server error.

For buttons:

1. Default.
2. Hover.
3. Focus-visible.
4. Active.
5. Disabled.
6. Loading.

Do not create a visually polished default state while leaving important interaction states unfinished.

## 9. Implement Design Systems Consistently

Use the project's existing design tokens and component conventions.

Examples:

- Colors.
- Typography.
- Spacing.
- Border radius.
- Shadows.
- Breakpoints.
- Motion durations.
- Component variants.

Prefer:

```css
.card {
  background: var(--color-surface);
  color: var(--color-text-primary);
  border-radius: var(--radius-lg);
  padding: var(--spacing-4);
}
```

Instead of repeatedly introducing unrelated hardcoded values.

When a design value genuinely differs, establish whether it should become a reusable token.

Do not create new tokens for every individual pixel adjustment.

## 10. Implement Responsive Layouts

Responsive behavior is part of implementation, not a later optional improvement.

Consider:

- Navigation.
- Grid columns.
- Flex wrapping.
- Typography scaling.
- Image dimensions.
- Content width.
- Touch targets.
- Horizontal overflow.
- Dialog sizing.
- Fixed and sticky elements.

Example:

```css
.feature-grid {
  display: grid;
  grid-template-columns: repeat(3, minmax(0, 1fr));
  gap: 1.5rem;
}

@media (max-width: 900px) {
  .feature-grid {
    grid-template-columns: repeat(2, minmax(0, 1fr));
  }
}

@media (max-width: 600px) {
  .feature-grid {
    grid-template-columns: 1fr;
  }
}
```

Use breakpoints that reflect actual content behavior and the existing design system.

Validate more than one mobile width. A layout that works at one viewport may still break at another.

## 11. Implement Accessible Interactions

Use semantic elements whenever possible.

Examples:

- `<button>` for actions.
- `<a>` for navigation.
- `<nav>` for navigation regions.
- `<main>` for primary content.
- `<form>` for form submissions.
- `<label>` for form fields.
- Appropriate headings for document structure.

Ensure:

- Keyboard access.
- Visible focus.
- Accessible names.
- Useful validation messages.
- Appropriate focus management.
- Correct heading hierarchy.
- Meaningful alternative text.
- Sufficient contrast.

Do not add ARIA attributes without understanding their purpose.

Native HTML semantics should be the starting point.

For complex interactions, use established accessibility primitives rather than creating incomplete custom behavior.

## 12. Implement Animation Carefully

Animation should improve feedback, hierarchy, or storytelling.

Before adding animation:

1. Identify its purpose.
2. Identify the trigger.
3. Define its duration.
4. Select an appropriate easing curve.
5. Consider interruption and cleanup.
6. Consider reduced motion.
7. Check performance.
8. Test on mobile.

### Motion implementation

Use the animation technology already selected during planning.

Possible options:

- CSS transitions for simple interface feedback.
- Motion for React-oriented interactions.
- GSAP for timelines and advanced scroll experiences.

Avoid introducing several animation libraries for overlapping use cases.

### Reduced motion

Respect the user's operating-system preference.

Example:

```css
@media (prefers-reduced-motion: reduce) {
  *,
  *::before,
  *::after {
    scroll-behavior: auto !important;
    animation-duration: 0.01ms !important;
    animation-iteration-count: 1 !important;
    transition-duration: 0.01ms !important;
  }
}
```

This is a broad CSS example. Complex experiences may need more deliberate reduced-motion alternatives rather than simply removing all motion.

## 13. Implement 3D Web Experiences

3D implementation requires additional attention to rendering, resources, and device capabilities.

### Three.js

Use Three.js directly when the project needs lower-level control over the rendering pipeline or scene lifecycle.

### React Three Fiber

Use React Three Fiber when a declarative React approach fits the application.

### Drei

Use Drei helpers where they reduce implementation complexity without hiding important behavior.

### Scene implementation sequence

1. Initialize the renderer.
2. Configure the camera.
3. Create scene geometry.
4. Add materials.
5. Configure lighting.
6. Load required assets.
7. Add interaction.
8. Implement animation.
9. Add responsive behavior.
10. Add fallbacks.
11. Profile performance.
12. Clean up resources.

### Asset handling

Prefer optimized assets.

Consider:

- GLTF or GLB for 3D models.
- Appropriate texture compression.
- Geometry optimization.
- Efficient environment maps.
- Appropriate image dimensions.
- Lazy loading when useful.

Do not load large 3D assets before they are needed.

### Resource cleanup

Dispose of resources that are no longer needed.

Consider:

- Geometries.
- Materials.
- Textures.
- Render targets.
- Event listeners.
- Animation loops.
- Controls.
- Observers.

In React Three Fiber, follow the ownership and disposal behavior of the renderer and scene graph. Avoid manually disposing shared resources that are still in use.

### Performance

Monitor:

- Frame rate.
- Draw calls.
- GPU memory.
- Texture memory.
- Shadow costs.
- Post-processing overhead.
- Scene complexity.

Do not optimize blindly. Profile the experience and address measurable bottlenecks.

## 14. Manage Assets and External Dependencies

Before introducing assets or packages:

- Check whether an equivalent already exists.
- Confirm framework compatibility.
- Review package versions.
- Check the package's maintenance status.
- Review its license.
- Understand its bundle impact.
- Verify that the asset can legally be used.

Do not download random assets or use copyrighted content without appropriate permission.

### Dependency discipline

Add dependencies only when they provide meaningful value.

Avoid:

- Multiple packages solving the same problem.
- Abandoned packages without justification.
- Unnecessary runtime dependencies.
- Unpinned or unexpected version changes.
- Replacing the package manager without a reason.

After dependency changes, inspect the lockfile and validate the application.

## 15. Implement Data Integrations Safely

When connecting APIs:

- Follow the documented API contract.
- Validate input and output.
- Handle errors.
- Handle network failures.
- Handle loading and empty states.
- Keep credentials out of client-side code.
- Avoid logging secrets.
- Avoid exposing sensitive information.
- Respect authorization boundaries.

Use environment variables for configuration.

Remember that frontend environment variables may be exposed to the browser when the framework explicitly publishes them.

Never place private API keys in client-side bundles.

## 16. Protect Existing Functionality

Implementation should preserve behavior outside the requested scope.

Before changing a shared component or utility:

1. Search for its usages.
2. Understand existing behavior.
3. Identify possible breaking changes.
4. Consider backward compatibility.
5. Update affected tests.
6. Validate dependent pages.

Do not rewrite entire files when a small focused modification is sufficient.

Do not delete existing functionality without confirming that it is obsolete or explicitly requested for removal.

## 17. Keep Code Changes Focused

A good implementation should have a clear relationship between the task and modified files.

Prefer:

- Small coherent changes.
- Clear naming.
- Limited scope.
- Reusable solutions.
- Understandable diffs.

Avoid:

- Unrelated refactoring.
- Formatting entire directories unnecessarily.
- Replacing configuration without a reason.
- Adding speculative features.
- Changing unrelated dependencies.
- Silently removing existing content.

When the scope changes, update the implementation plan.

## 18. Validate During Implementation

Validation should happen continuously.

After meaningful changes:

1. Inspect the changed files.
2. Run relevant tests.
3. Check TypeScript.
4. Check linting.
5. Start the application where possible.
6. Inspect browser behavior when tools are available.
7. Review responsive layouts.
8. Check console errors.

Use the project's actual scripts rather than assuming command names.

Example:

```powershell
npm run
```

This lists available npm scripts.

Then run the appropriate commands defined by the project, for example:

```powershell
npm run lint
npm run typecheck
npm run build
```

Only run commands that actually exist in `package.json`.

Do not claim a test passed if it was not executed.

## 19. Handle Implementation Failures

When something fails:

1. Read the complete error.
2. Identify the affected file or dependency.
3. Determine whether the failure existed before the change.
4. Reproduce the problem where possible.
5. Identify the root cause.
6. Make a focused correction.
7. Rerun the relevant validation.

Avoid random edits until the error disappears.

If a failure depends on missing credentials, external services, or unavailable infrastructure, report the limitation honestly.

Do not hide unresolved failures.

## 20. Visual Verification

For frontend work, functional correctness alone is insufficient.

Inspect the actual rendered interface when browser or screenshot tools are available.

Review:

- Layout.
- Alignment.
- Spacing.
- Typography.
- Color.
- Component consistency.
- Images.
- Responsive behavior.
- Interaction feedback.
- Motion.
- Overflow.

Compare the result with supplied references when available.

If browser access or screenshots are unavailable, distinguish code inspection from actual visual verification.

Never claim that a page has been visually tested without viewing its rendered output.

Related guide: [Frontend Visual Audit Skill](../skills/frontend-visual-audit/SKILL.md).

## 21. Security and Code Quality

Follow secure development practices.

Examples:

- Validate untrusted input.
- Avoid unsafe HTML injection.
- Do not expose credentials.
- Check authorization on the server.
- Avoid leaking sensitive data.
- Use safe URL handling.
- Keep dependencies maintained.
- Avoid unnecessary permissions.
- Follow secure authentication patterns.

For React applications, avoid using `dangerouslySetInnerHTML` unless the content is trusted or properly sanitized.

Frontend checks do not replace server-side security validation.

## 22. Document Implementation Decisions

When implementation introduces meaningful architectural decisions, document them.

Examples:

- Why a particular rendering approach was selected.
- Why a new dependency was introduced.
- How shared state is managed.
- How 3D resources are loaded.
- How responsive fallbacks work.
- How an API integration is structured.

Keep documentation proportional to complexity.

Do not document every obvious implementation detail.

## 23. Implementation Completion Report

When implementation is finished, provide a concise report.

Recommended format:

```md
# Implementation Summary

## Completed
- Feature or component one
- Feature or component two

## Files Changed
- path/to/file-one
- path/to/file-two

## Technical Decisions
- Important implementation decision

## Validation
- Tests executed
- Build result
- Responsive checks
- Accessibility checks

## Known Limitations
- Remaining issue, if any

## Next Steps
- Recommended follow-up work
```

Distinguish completed work from planned work.

Clearly identify checks that could not be performed.

## 24. AI Agent Implementation Checklist

### Before coding

- [ ] Repository inspected.
- [ ] Existing changes identified.
- [ ] Dependencies reviewed.
- [ ] Requirements understood.
- [ ] Implementation plan available.
- [ ] Reusable components identified.

### During coding

- [ ] Existing architecture respected.
- [ ] Components have clear responsibilities.
- [ ] TypeScript types are meaningful.
- [ ] Design tokens are reused.
- [ ] Responsive behavior is implemented.
- [ ] Accessible interactions are implemented.
- [ ] Errors and loading states are handled.
- [ ] Dependencies are justified.
- [ ] Unrelated changes are avoided.

### For animation and 3D

- [ ] Animation serves a purpose.
- [ ] Reduced motion is considered.
- [ ] Assets are optimized.
- [ ] Resource cleanup is addressed.
- [ ] Mobile performance is considered.
- [ ] Fallback behavior exists where necessary.

### Before completion

- [ ] Relevant tests executed.
- [ ] Type checks completed where available.
- [ ] Lint checks completed where available.
- [ ] Production build checked.
- [ ] Visual output reviewed where possible.
- [ ] Remaining limitations documented.
- [ ] Implementation summary prepared.

## 25. Definition of Done

An implementation is complete when:

1. The requested functionality is implemented.
2. Existing architecture and conventions are respected.
3. Relevant responsive behavior works.
4. Accessibility requirements are addressed.
5. Loading, error, and interaction states are handled where applicable.
6. Performance considerations are addressed.
7. Relevant tests and build checks are executed.
8. No known critical regression remains.
9. Changes are documented appropriately.
10. Remaining limitations are communicated honestly.

A successful implementation is not simply code that compiles. It is a verified, maintainable result that satisfies the user's actual requirements.

---

## Related Guides

- [AI Agent Planning Workflow](./planning.md)
- [AI Agent Visual Review Workflow](./visual-review.md)
- [AI Agent Optimization Workflow](./optimization.md)
- [Frontend Architecture](../fundamentals/frontend-architecture.md)
- [Component Architecture](../design-systems/components.md)
- [3D Web Optimization](../3d-web/optimization.md)
- [Frontend Visual Audit Skill](../skills/frontend-visual-audit/SKILL.md)
- [3D Scene Builder Skill](../skills/3d-scene-builder/SKILL.md)