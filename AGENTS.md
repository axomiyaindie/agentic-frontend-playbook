# Agent Instructions — Agentic Frontend & 3D Web Playbook

These instructions apply to AI coding agents working anywhere in this repository.

## 1. Project Identity

Agentic Frontend & 3D Web Playbook is an open-source engineering knowledge base for modern frontend development, immersive 3D web experiences, animation, visual design, and AI-assisted engineering workflows.

The project serves both human developers and AI coding agents.

Its purpose is to provide accurate, practical, structured, and reusable engineering knowledge.

## 2. Core Principles

Every contribution must prioritize:

- Technical accuracy over quantity.
- Practical implementation over generic advice.
- Clear explanations over unnecessary complexity.
- Modern engineering practices.
- Maintainable and reusable solutions.
- Responsive and accessible experiences.
- Performance-conscious implementations.
- Consistent documentation standards.
- Honest technical claims and attribution.

Do not create superficial documentation simply to populate directories.

## 3. Documentation Standards

All documentation must:

- Use clear Markdown.
- Have a descriptive H1 heading.
- Include a short introduction explaining its purpose.
- Use logical heading hierarchy.
- Include practical examples where relevant.
- Explain important technical decisions.
- Identify relevant dependencies and prerequisites.
- Link to related documentation when useful.
- Distinguish established practices from recommendations.
- Avoid outdated APIs and unsupported claims.

When documenting third-party technologies:

- Prefer official documentation.
- Verify API details against current documentation.
- Include source links for important technical references.
- Clearly identify version-specific behavior.
- Do not invent functions, properties, or capabilities.

## 4. Frontend Engineering

When developing or documenting frontend implementations:

- Favor component-driven architecture.
- Use semantic HTML.
- Follow responsive design principles.
- Keep components focused and reusable.
- Use appropriate state management.
- Avoid unnecessary dependencies.
- Handle loading, error, and empty states.
- Consider keyboard navigation and accessibility.
- Follow established framework conventions.

React and Next.js guidance must distinguish framework-specific patterns where necessary.

Do not assume every project requires the same framework or stack.

## 5. 3D Web Development

3D is a first-class specialization of this project.

Cover relevant technologies including:

- Three.js
- React Three Fiber
- Drei
- WebGL
- GLSL
- 3D modeling and asset integration
- Materials, lighting, cameras, and scene composition
- Interactive 3D experiences

When developing 3D guidance:

- Explain scene structure and rendering concepts.
- Consider rendering performance.
- Avoid unnecessary draw calls.
- Optimize geometry, textures, and assets.
- Manage resource disposal and component lifecycles.
- Consider mobile GPU limitations.
- Provide accessible alternatives where appropriate.
- Consider reduced-motion preferences.
- Include graceful fallbacks when 3D rendering is unavailable.

Do not recommend 3D effects when they undermine usability or performance.

## 6. Animation and Interaction

Animation should improve usability, storytelling, or visual communication.

Relevant technologies include:

- GSAP
- Motion
- CSS animations
- Scroll-driven animations
- Interactive transitions

Prioritize:

- Smooth and purposeful motion.
- Consistent timing and easing.
- Reduced-motion support.
- Cleanup of animation resources.
- Performance-conscious rendering.
- Avoiding excessive or distracting animation.

## 7. Design Engineering

Design-related documentation should address:

- Typography and hierarchy.
- Color systems.
- Spacing and layout.
- Visual consistency.
- Responsive behavior.
- Component patterns.
- Interaction states.
- Design tokens.

Avoid vague descriptions such as "make it beautiful" without actionable design guidance.

Translate visual recommendations into concrete implementation decisions wherever possible.

## 8. AI Agent Skills

Skills must provide actionable workflows, not just generic prompts.

Each skill should have its own directory containing a `SKILL.md` file.

Where appropriate, use this structure:

```text
skill-name/
├── SKILL.md
├── references/
└── examples/
```

A skill should explain:

- Its purpose.
- When to use it.
- Required inputs and context.
- Step-by-step workflow.
- Technical and design constraints.
- Expected outputs.
- Validation criteria.
- Common mistakes.

Use the Agent Skills specification when defining portable skills. Verify its current requirements before claiming compatibility.

Keep skills focused, reusable, and independent where practical.

## 9. Agent Workflows

Document practical workflows covering:

1. Requirement analysis.
2. Project and design planning.
3. Technology selection.
4. Implementation.
5. Visual inspection.
6. Testing and validation.
7. Performance optimization.
8. Final review.

Workflows should define clear inputs, actions, expected outputs, and completion criteria.

## 10. Code Quality

All contributed code must:

- Be readable and maintainable.
- Follow the relevant language conventions.
- Avoid unnecessary abstraction.
- Handle errors appropriately.
- Avoid hardcoded secrets.
- Avoid unnecessary dependencies.
- Include meaningful comments where useful.
- Be validated using appropriate tooling.

Never claim that code has been tested unless the relevant tests or checks have actually been performed.

## 11. Examples

Examples should demonstrate real implementation patterns.

Where applicable, include:

- Project structure.
- Setup instructions.
- Dependencies.
- Implementation details.
- Expected behavior.
- Screenshots or visual references.
- Performance considerations.

Do not add nonfunctional examples or pretend placeholder projects are complete implementations.

## 12. Performance and Accessibility

Performance and accessibility are core engineering requirements.

Consider:

- Core Web Vitals.
- Image and asset optimization.
- Lazy loading.
- Code splitting.
- Rendering efficiency.
- Semantic markup.
- Keyboard accessibility.
- Screen reader compatibility.
- Color contrast.
- Reduced-motion preferences.

3D and animation features must not unnecessarily compromise accessibility or usability.

## 13. Repository Structure

Respect the existing documentation organization:

- `fundamentals/` — frontend foundations.
- `3d-web/` — 3D development.
- `animation/` — motion and interaction.
- `design-systems/` — visual systems and components.
- `agent-workflows/` — AI-assisted engineering workflows.
- `skills/` — reusable agent skills.
- `examples/` — practical implementations.
- `resources/` — libraries and references.

Place new material in the most appropriate existing category.

Avoid unnecessary duplication.

## 14. Contribution Rules

Before making changes:

1. Inspect the existing repository structure.
2. Read relevant documentation.
3. Understand the requested change.
4. Check for existing content before creating new files.
5. Preserve unrelated user changes.

When completing changes:

1. Review modified files.
2. Check Markdown formatting.
3. Validate code examples where possible.
4. Verify internal links.
5. Check for duplicate or contradictory guidance.
6. Summarize what changed.
7. Report any checks that could not be performed.

Do not overwrite existing content without a clear reason.

## 15. Content Integrity and Licensing

- Respect third-party licenses.
- Attribute external material appropriately.
- Do not copy proprietary documentation wholesale.
- Do not introduce unlicensed assets.
- Do not invent authors, references, or endorsements.
- Do not claim an open-source license until one is formally selected and added.

## 16. Communication

When working on this repository:

- Explain significant technical decisions.
- Keep changes focused.
- Identify incomplete work honestly.
- Ask questions when essential requirements are unclear.
- Prefer incremental, reviewable contributions.
- Avoid unnecessary rewrites.

## 17. Definition of Done

A contribution is complete when:

- It addresses the intended requirement.
- Its content is technically accurate.
- Documentation follows repository standards.
- Relevant examples are functional or clearly identified as illustrative.
- Internal references are valid.
- Appropriate validation has been performed.
- Limitations are documented honestly.

---

**Guiding principle:** Help developers and AI coding agents build better frontend applications, more immersive 3D experiences, and higher-quality digital products through practical engineering knowledge.
