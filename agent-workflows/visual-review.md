# AI Agent Visual Review Workflow

Visual quality is a critical part of modern frontend engineering.

An application can compile successfully, pass its tests, and still look unfinished. Layout inconsistencies, poor typography, incorrect spacing, broken responsive behavior, and incomplete interactions can significantly reduce the quality of the experience.

AI coding agents should therefore review the actual rendered interface, identify visual and interaction problems, and verify that corrections improve the result.

This guide defines a systematic visual review workflow for modern frontend applications, landing pages, interactive websites, and immersive 3D experiences.

## 1. Purpose of Visual Review

Visual review evaluates whether an implementation delivers the intended user experience.

It examines:

- Layout and composition.
- Visual hierarchy.
- Typography.
- Color consistency.
- Spacing and alignment.
- Component styling.
- Images and assets.
- Responsive behavior.
- Animation and interaction.
- Accessibility.
- 3D rendering quality.

Visual review should happen throughout development, not only before release.

## 2. Core Review Principles

### Review the rendered interface

Source code inspection cannot prove that the final interface looks correct.

Use browser previews, screenshots, or other visual inspection tools when available.

### Compare against requirements

Review the implementation against the original request, design reference, and acceptance criteria.

### Prioritize user-visible problems

A broken navigation menu is more important than a minor decorative discrepancy.

### Inspect multiple viewport sizes

A desktop screenshot cannot establish mobile quality.

### Fix root causes

Correct underlying layout or component problems rather than adding repeated CSS overrides.

### Verify every correction

After changing the implementation, inspect the affected interface again.

### Report limitations honestly

Never claim visual verification if the rendered interface was not actually inspected.

## 3. Prepare for Visual Review

Before reviewing an application, establish what should be evaluated.

Collect:

- Original requirements.
- Approved implementation plan.
- Design references.
- Existing screenshots.
- Expected page routes.
- Supported viewport sizes.
- Important user interactions.
- Accessibility requirements.
- Performance expectations.

Identify which parts of the implementation are in scope.

For an existing application, distinguish newly introduced problems from issues that already existed.

## 4. Inspect the Actual Application

When browser access is available:

1. Start the development server using the project's documented command.
2. Open the relevant page.
3. Wait for the interface to render.
4. Check for runtime errors.
5. Inspect the initial viewport.
6. Scroll through the entire page.
7. Test important interactions.
8. Resize the viewport.
9. Capture screenshots where useful.

Do not review only the first screen of a long page.

Inspect the complete experience, including footer sections, dialogs, navigation, and interactive elements.

### Browser inspection

Check:

- Whether the page loads.
- Whether fonts load correctly.
- Whether images load.
- Whether assets are missing.
- Whether content overflows.
- Whether components render as expected.
- Whether navigation works.
- Whether interactive states are correct.

Use browser developer tools when necessary.

## 5. Review Against Design References

When a reference image, screenshot, or design file is provided, use it as the visual source of truth.

Compare:

- Overall composition.
- Section order.
- Container dimensions.
- Column proportions.
- Alignment.
- Typography.
- Color relationships.
- Spacing.
- Image placement.
- Component proportions.
- Visual density.
- Decorative details.

### Reference comparison process

1. Identify the reference viewport.
2. Capture the implementation at the same viewport.
3. Compare major layout regions.
4. Identify the largest discrepancies.
5. Rank issues by severity.
6. Fix the highest-impact problems first.
7. Capture a new screenshot.
8. Repeat until the acceptance criteria are satisfied.

Do not claim pixel-perfect matching based only on visual memory.

Where possible, compare screenshots at equivalent dimensions.

## 6. Review Layout and Composition

Layout is the foundation of visual quality.

Check:

- Main content width.
- Section spacing.
- Container alignment.
- Grid proportions.
- Column balance.
- Element positioning.
- Consistent margins.
- Content density.
- Vertical rhythm.

### Common layout problems

- Sections have inconsistent horizontal padding.
- Content is too wide or too narrow.
- Elements are misaligned.
- Cards have inconsistent heights.
- Columns do not align.
- Hero sections lack visual balance.
- Fixed elements overlap content.
- Large empty spaces appear unintentionally.

### Review container consistency

Related sections should generally use a consistent content width and alignment system.

Example:

```css
.container {
  width: min(100% - 2rem, 1200px);
  margin-inline: auto;
}
```

The exact maximum width should follow the design requirements.

Avoid solving alignment problems with arbitrary margins on individual elements.

## 7. Review Visual Hierarchy

Visual hierarchy determines what users notice first.

Inspect:

- Main heading prominence.
- Supporting text.
- Primary actions.
- Secondary actions.
- Section headings.
- Content groupings.
- Important information.
- Decorative elements.

Ask:

1. Is the main message immediately understandable?
2. Is the primary action easy to identify?
3. Are secondary elements visually subordinate?
4. Does the page guide attention naturally?
5. Are important elements competing for attention?

If everything is visually prominent, nothing is prominent.

## 8. Review Typography

Typography directly affects readability and perceived quality.

Check:

- Font family.
- Font weight.
- Font size.
- Line height.
- Letter spacing.
- Text width.
- Heading hierarchy.
- Paragraph readability.
- Text wrapping.
- Font loading.

### Common typography issues

- Headlines wrap awkwardly.
- Body text is too small.
- Paragraphs have excessive line length.
- Heading weights are inconsistent.
- Font combinations feel unrelated.
- Line height is too tight.
- Navigation labels are difficult to read.

### Review text wrapping

Inspect headings and buttons at multiple viewport widths.

Avoid forcing unnatural line breaks unless the design specifically requires them.

Use responsive typography where appropriate.

Example:

```css
.hero-title {
  font-size: clamp(2.5rem, 6vw, 5.5rem);
  line-height: 1.05;
  letter-spacing: -0.04em;
}
```

## 9. Review Colors and Contrast

Check whether the interface uses a consistent color system.

Inspect:

- Background colors.
- Primary and secondary colors.
- Text colors.
- Borders.
- Surface colors.
- Interactive states.
- Semantic colors.
- Gradients.

### Contrast

Text should remain readable against its background.

Use WCAG contrast guidance as an evaluation reference:

- Normal text generally requires at least 4.5:1 contrast for WCAG AA.
- Large text generally requires at least 3:1 contrast for WCAG AA.
- Relevant non-text interface components generally require 3:1 contrast against adjacent colors under applicable WCAG requirements.

Use an actual contrast checker rather than estimating contrast visually.

Do not rely on color alone to communicate errors, success, or other important states.

## 10. Review Spacing and Alignment

Inspect consistency across:

- Section padding.
- Card padding.
- Element gaps.
- Button spacing.
- Form spacing.
- Heading margins.
- Navigation spacing.
- Grid gaps.

Use the design system's spacing tokens whenever possible.

Example:

```css
:root {
  --space-1: 0.25rem;
  --space-2: 0.5rem;
  --space-3: 0.75rem;
  --space-4: 1rem;
  --space-6: 1.5rem;
  --space-8: 2rem;
}
```

Do not introduce arbitrary values for every component without a reason.

## 11. Review Components

Check whether repeated interface elements look and behave consistently.

Inspect:

- Buttons.
- Inputs.
- Cards.
- Navigation.
- Badges.
- Dialogs.
- Dropdowns.
- Tabs.
- Tables.
- Alerts.
- Footers.

Review each component's:

- Dimensions.
- Padding.
- Typography.
- Radius.
- Border.
- Shadow.
- Icon placement.
- Hover state.
- Focus state.
- Disabled state.
- Loading state.

### Consistency checks

- Similar buttons should have consistent heights.
- Repeated cards should use consistent spacing.
- Form fields should have consistent labels and error treatment.
- Navigation items should align correctly.
- Icons should have appropriate size and alignment.

Related guide: [Component Architecture](../design-systems/components.md).

## 12. Review Images and Assets

Visual assets strongly influence perceived quality.

Inspect:

- Image resolution.
- Aspect ratio.
- Cropping.
- Object positioning.
- Sharpness.
- Loading behavior.
- Consistency.
- Relevance.
- Alt text.

### Common problems

- Images are stretched.
- Subjects are cropped incorrectly.
- Placeholder assets remain in production.
- Different image styles clash.
- Low-resolution images appear blurry.
- Decorative images are announced unnecessarily by screen readers.
- Important content is embedded only in images.

For image components, consider:

```css
.product-image {
  width: 100%;
  aspect-ratio: 4 / 3;
  object-fit: cover;
}
```

Use `object-position` when a particular subject position matters.

Do not use generic image placeholders when the project requires actual product or brand imagery.

## 13. Review Responsive Behavior

Responsive review must include multiple viewport sizes.

Example review matrix:

| Device category | Example viewport |
|---|---|
| Large desktop | 1440 × 900 |
| Laptop | 1280 × 800 |
| Tablet | 768 × 1024 |
| Mobile | 390 × 844 |
| Small mobile | 320 × 700 |

These are representative test sizes, not mandatory universal breakpoints.

Check:

- Navigation transformation.
- Grid stacking.
- Text wrapping.
- Image cropping.
- Container width.
- Button width.
- Form layout.
- Dialog sizing.
- Horizontal overflow.
- Fixed element positioning.
- Touch interaction.

### Mobile-specific review

Pay special attention to:

- Small text.
- Narrow buttons.
- Tiny touch targets.
- Overlapping elements.
- Off-screen content.
- Unusable dropdowns.
- Oversized hero graphics.
- Excessive vertical spacing.

Do not simply shrink the desktop layout.

Mobile should have an intentional composition.

## 14. Review Interactions

Visual review should include interaction behavior.

Test:

- Navigation links.
- Buttons.
- Dropdowns.
- Tabs.
- Accordions.
- Dialogs.
- Forms.
- Search.
- Filters.
- Pagination.
- Interactive cards.
- Hover effects.
- Keyboard navigation.

For each interaction, verify:

1. Initial state.
2. Activation behavior.
3. Visible feedback.
4. Resulting state.
5. Keyboard behavior.
6. Error handling where applicable.

A button that looks clickable but does nothing is a functional defect.

Do not mistake hover styling for complete interaction support.

## 15. Review Motion and Animation

Inspect animation for both visual quality and usability.

Check:

- Timing.
- Easing.
- Duration.
- Stagger.
- Direction.
- Scroll behavior.
- Layout stability.
- Interruption.
- Cleanup.
- Reduced-motion behavior.

### Common animation problems

- Animations are too slow.
- Motion feels inconsistent.
- Scroll interactions interfere with navigation.
- Elements move unexpectedly.
- Large sections cause jarring transitions.
- Animations run when the page is hidden.
- Content becomes inaccessible during animation.
- Reduced-motion preferences are ignored.

Motion should support the content rather than distract from it.

## 16. Review 3D Web Experiences

3D experiences require a separate visual and technical review.

Inspect:

### Scene composition

- Camera position.
- Object framing.
- Subject visibility.
- Scene balance.
- Lighting.
- Background.
- Depth.
- Materials.

### Rendering quality

- Texture quality.
- Geometry.
- Aliasing.
- Shadows.
- Reflections.
- Post-processing.
- Color accuracy.

### Interaction

- Camera controls.
- Pointer interaction.
- Touch behavior.
- Scroll interaction.
- Hover behavior.
- Input responsiveness.

### Performance

- Loading time.
- Frame rate.
- Draw calls.
- Texture memory.
- Shader cost.
- GPU usage where measurable.

### Fallback behavior

Verify that essential information remains available when:

- WebGL is unavailable.
- The device cannot render the scene adequately.
- Assets fail to load.
- Reduced motion is enabled.
- Network conditions are poor.

A beautiful 3D scene is not successful if it makes the page unusable.

Related guides:

- [Three.js](../3d-web/threejs.md)
- [React Three Fiber](../3d-web/react-three-fiber.md)
- [Shaders](../3d-web/shaders.md)
- [3D Optimization](../3d-web/optimization.md)

## 17. Review Accessibility

Visual and accessibility reviews should complement each other.

Check:

- Keyboard navigation.
- Visible focus.
- Accessible names.
- Heading hierarchy.
- Form labels.
- Error messages.
- Color contrast.
- Text resizing.
- Reduced motion.
- Image alternatives.
- Dialog focus management.

Test important flows without relying exclusively on a mouse.

Use accessibility tools where available, but do not treat automated results as a complete accessibility audit.

Useful references:

- [WCAG](https://www.w3.org/WAI/standards-guidelines/wcag/)
- [WAI-ARIA Authoring Practices](https://www.w3.org/WAI/ARIA/apg/)
- [WebAIM Contrast Checker](https://webaim.org/resources/contrastchecker/)

## 18. Review Performance-Related Visual Problems

Performance issues often affect perceived quality.

Inspect:

- Layout shifts.
- Delayed font rendering.
- Missing images.
- Large image downloads.
- Slow initial rendering.
- Long-running animations.
- Heavy 3D scenes.
- Excessive JavaScript.
- Unnecessary re-rendering.

Consider Core Web Vitals:

- Largest Contentful Paint (LCP).
- Interaction to Next Paint (INP).
- Cumulative Layout Shift (CLS).

Use browser performance tools and appropriate measurement tools to investigate.

Do not infer actual performance scores from source code alone.

## 19. Prioritize Visual Defects

Not all visual problems have equal impact.

Use severity levels.

### Critical

Issues that prevent essential use or significantly break the experience.

Examples:

- Page does not render.
- Main navigation is unusable.
- Primary action is inaccessible.
- Important content is completely hidden.

### High

Major visual or functional defects.

Examples:

- Mobile layout is broken.
- Hero content overlaps.
- Important text is unreadable.
- Main product image is missing.

### Medium

Noticeable inconsistencies that reduce quality.

Examples:

- Inconsistent spacing.
- Incorrect card proportions.
- Awkward heading wrapping.
- Misaligned icons.

### Low

Minor polish issues.

Examples:

- Small decorative alignment differences.
- Slightly inconsistent shadows.
- Minor border-radius differences.

Prioritize based on user impact, not the number of defects.

## 20. Create a Visual Review Report

Record findings in a structured format.

Example:

```md
# Visual Review Report

## Scope
Landing page and navigation.

## Environment
Desktop: 1440 × 900
Mobile: 390 × 844

## Findings

### Critical
- None identified.

### High
- Mobile navigation overlaps the hero heading.

### Medium
- Feature cards have inconsistent vertical spacing.

### Low
- Icon alignment differs slightly between buttons.

## Recommended Fixes
1. Correct mobile navigation positioning.
2. Standardize feature card spacing.
3. Align button icons.

## Validation
- Desktop screenshot reviewed.
- Mobile screenshot reviewed.
- Navigation interaction tested.

## Limitations
- Actual device testing not performed.
```

Include screenshots or visual references when useful and available.

Do not report findings that were not actually observed.

## 21. Fix and Re-Review Workflow

A review is incomplete until important issues are addressed and rechecked.

Use this cycle:

```text
Inspect
   |
   v
Identify defects
   |
   v
Prioritize
   |
   v
Implement fixes
   |
   v
Capture new screenshots
   |
   v
Compare results
   |
   v
Validate behavior
   |
   v
Repeat if necessary
```

After a correction:

1. Inspect the changed component.
2. Check nearby layout elements.
3. Test responsive behavior.
4. Verify interaction behavior.
5. Compare against the original reference.
6. Check for new regressions.

Avoid adding CSS overrides without understanding the underlying cause.

## 22. Visual Review Without Browser Access

Sometimes an agent cannot launch the application or inspect browser screenshots.

In that situation, perform a limited code-level review.

Inspect:

- Component structure.
- CSS and design tokens.
- Responsive media queries.
- Semantic markup.
- Accessibility attributes.
- Image configuration.
- Animation logic.
- Potential layout problems.

However, clearly distinguish between:

**Code-level review**

The source code was inspected.

**Rendered visual review**

The actual browser output was inspected.

**Device testing**

The experience was tested on physical or representative devices.

These are different levels of evidence.

Never claim a rendered visual review or physical device test when only source code was inspected.

## 23. AI Agent Visual Review Checklist

### Layout

- [ ] Content alignment is consistent.
- [ ] Containers have appropriate widths.
- [ ] Grid and column proportions are correct.
- [ ] No unintended overlap exists.
- [ ] Section spacing is consistent.

### Typography

- [ ] Font choices are consistent.
- [ ] Heading hierarchy is clear.
- [ ] Text is readable.
- [ ] Wrapping is natural.
- [ ] Font loading works.

### Visual styling

- [ ] Colors follow the design system.
- [ ] Contrast is appropriate.
- [ ] Borders and radius are consistent.
- [ ] Shadows are appropriate.
- [ ] Icons are aligned.

### Assets

- [ ] Images load correctly.
- [ ] Cropping is appropriate.
- [ ] Image resolution is sufficient.
- [ ] No unwanted placeholders remain.
- [ ] Alt text is appropriate.

### Responsive behavior

- [ ] Desktop reviewed.
- [ ] Tablet reviewed.
- [ ] Mobile reviewed.
- [ ] No horizontal overflow.
- [ ] Navigation works at supported widths.
- [ ] Content remains readable.

### Interactions

- [ ] Buttons work.
- [ ] Links work.
- [ ] Menus work.
- [ ] Forms work.
- [ ] Focus states are visible.
- [ ] Keyboard behavior is correct.

### Animation and 3D

- [ ] Motion feels intentional.
- [ ] Reduced motion is respected.
- [ ] 3D framing is correct.
- [ ] Scene interactions work.
- [ ] Fallback behavior works.
- [ ] Performance is acceptable.

### Final validation

- [ ] Critical defects resolved.
- [ ] Important fixes rechecked.
- [ ] No major regressions introduced.
- [ ] Review findings documented.
- [ ] Verification limitations reported.

## 24. Definition of Done

Visual review is complete when:

1. The implementation has been evaluated against its requirements.
2. Important page sections have been inspected.
3. Relevant viewport sizes have been reviewed.
4. Major layout and styling issues have been identified.
5. Important interactions have been tested.
6. Accessibility concerns have been considered.
7. 3D and animation behavior has been reviewed where relevant.
8. High-impact defects have been resolved or documented.
9. Corrections have been rechecked.
10. The final report accurately describes the evidence and limitations.

Visual quality is not achieved by generating more CSS. It is achieved through careful observation, systematic correction, and repeated verification.

---

## Related Guides

- [AI Agent Planning Workflow](./planning.md)
- [AI Agent Implementation Workflow](./implementation.md)
- [AI Agent Optimization Workflow](./optimization.md)
- [Frontend Visual Audit Skill](../skills/frontend-visual-audit/SKILL.md)
- [Premium Landing Page Skill](../skills/premium-landing-page/SKILL.md)
- [Responsive Design](../fundamentals/responsive-design.md)
- [Component Architecture](../design-systems/components.md)
- [3D Web Optimization](../3d-web/optimization.md)