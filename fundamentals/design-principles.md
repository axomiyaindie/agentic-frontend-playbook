# Frontend Design Principles

Good frontend engineering is not only about making interfaces work. It is about creating experiences that are clear, consistent, accessible, responsive, performant, and maintainable.

This guide establishes the design principles that developers and AI coding agents should follow when building modern frontend applications.

## 1. User Experience First

Every interface should solve a real user problem.

- Make the primary purpose immediately understandable.
- Prioritize important actions and information.
- Keep navigation predictable.
- Reduce unnecessary interactions.
- Provide clear feedback for user actions.
- Design useful empty, loading, success, and error states.

Avoid adding visual effects or interactions that make the experience harder to understand.

## 2. Visual Hierarchy

Visual hierarchy helps users understand what matters.

Use:

- Typography to distinguish headings, descriptions, and supporting information.
- Spacing to establish relationships between elements.
- Contrast to emphasize important content.
- Alignment to create visual consistency.
- Size and weight to communicate importance.

A page should have a clear reading order and a recognizable primary action.

## 3. Consistency

Consistency makes interfaces easier to learn and maintain.

Establish reusable decisions for:

- Typography
- Colors
- Spacing
- Border radii
- Shadows
- Buttons
- Form elements
- Navigation
- Interaction states

Use shared design tokens and components instead of repeatedly introducing slightly different styles.

## 4. Simplicity and Clarity

Prefer simple solutions that communicate effectively.

- Remove unnecessary interface elements.
- Avoid excessive decoration.
- Use familiar interaction patterns.
- Keep content concise.
- Avoid unnecessary animation.
- Introduce complexity only when it improves the experience.

Minimal design does not mean removing useful functionality.

## 5. Responsive Design

Interfaces must work across different screen sizes and input methods.

Consider:

- Mobile-first layout decisions.
- Flexible grids and containers.
- Appropriate typography scaling.
- Touch-friendly interaction targets.
- Navigation on small screens.
- Responsive imagery and media.
- Horizontal overflow and content wrapping.

Do not treat desktop layouts as the only intended experience.

## 6. Accessibility

Accessibility should be considered from the beginning.

Follow these practices:

- Use semantic HTML.
- Provide labels for form controls.
- Include meaningful alternative text for informative images.
- Maintain sufficient color contrast.
- Support keyboard navigation.
- Provide visible focus indicators.
- Respect reduced-motion preferences.
- Do not communicate meaning through color alone.

Use WCAG guidance when evaluating accessibility.

Reference: https://www.w3.org/WAI/standards-guidelines/wcag/

## 7. Motion and Interaction

Animation should communicate, guide, or enhance an interaction.

Use