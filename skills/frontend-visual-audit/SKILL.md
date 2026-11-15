---
name: frontend-visual-audit
description: Audit and improve frontend visual quality, design fidelity, responsiveness, accessibility, and interface consistency in existing websites and applications. Use when reviewing screenshots, comparing implementations against Figma or design references, identifying UI defects, or performing frontend visual quality assurance.
---

# Frontend Visual Audit

## Purpose

Guide AI coding agents through systematic frontend visual inspection and quality assurance.

Identify measurable visual and usability problems, prioritize defects, and implement targeted improvements without unnecessarily rewriting existing applications.

## Workflow

### 1. Understand the audit scope

Identify:

- Application or page to inspect.
- Intended design reference.
- Target viewport sizes.
- Relevant user journeys.
- Expected functionality.
- Available browser and testing tools.

Determine whether the task is a visual comparison, general UI audit, responsive audit, or combined review.

### 2. Inspect the implementation

Before making changes:

1. Review the project structure.
2. Identify framework and styling conventions.
3. Locate relevant components.
4. Inspect existing design tokens.
5. Identify available tests.
6. Understand the current implementation.

Preserve existing functionality and architecture.

### 3. Capture visual evidence

When browser or screenshot tools are available:

- Run the application.
- Capture relevant pages.
- Inspect desktop and mobile viewports.
- Examine important interaction states.
- Compare against supplied references.
- Record visible defects.

Use consistent viewport dimensions when comparing screenshots.

Never claim to have inspected a rendered page if only its source code was reviewed.

### 4. Evaluate visual quality

Review the following categories.

**Layout**
- Alignment.
- Spacing.
- Grid consistency.
- Container widths.
- Section proportions.
- Overflow and clipping.

**Typography**
- Font hierarchy.
- Font sizes.
- Line heights.
- Text wrapping.
- Readability.
- Contrast.

**Color and surfaces**
- Color consistency.
- Background relationships.
- Border treatments.
- Shadows.
- Contrast between foreground and background.

**Components**
- Button consistency.
- Input states.
- Navigation.
- Cards.
- Icons.
- Interactive feedback.

**Imagery and 3D**
- Asset quality.
- Aspect ratios.
- Image positioning.
- 3D scene integration.
- Loading behavior.
- Visual performance.

### 5. Audit responsiveness

Inspect:

- Desktop layouts.
- Tablet layouts.
- Mobile layouts.
- Narrow viewport behavior.

Identify:

- Horizontal scrolling.
- Clipped content.
- Broken grids.
- Overlapping elements.
- Unreadable typography.
- Navigation failures.
- Inaccessible controls.

### 6. Audit accessibility

Review:

- Semantic structure.
- Keyboard navigation.
- Focus visibility.
- Accessible names.
- Color contrast.
- Form labels.
- Image alternatives.
- Reduced-motion support.

Use automated accessibility tools where available, but do not treat automated results as a complete accessibility audit.

### 7. Prioritize findings

Classify defects:

**Critical**
- Broken navigation.
- Inaccessible primary actions.
- Content that cannot be used.
- Major layout failures.

**High**
- Significant responsive defects.
- Important visual mismatches.
- Broken interactive states.

**Medium**
- Inconsistent spacing.
- Typography problems.
- Component styling inconsistencies.

**Low**
- Minor decorative inconsistencies.
- Small alignment differences.
- Nonessential polish.

Explain the user impact and recommended correction.

### 8. Implement improvements

For each finding:

1. Identify the responsible component.
2. Determine the smallest appropriate fix.
3. Preserve existing behavior.
4. Apply the correction.
5. Reinspect the result.
6. Run relevant checks.

Avoid broad rewrites when focused changes are sufficient.

### 9. Produce an audit report

Summarize:

- Scope inspected.
- Tools and viewport sizes used.
- Findings by severity.
- Corrections made.
- Checks performed.
- Remaining issues.
- Unverified areas.

Clearly distinguish observed defects from potential risks.

## Engineering Rules

- Base findings on actual evidence.
- Never invent screenshot observations.
- Never claim pixel-perfect fidelity without meaningful comparison.
- Avoid changing unrelated functionality.
- Respect the established design system.
- Preserve responsive behavior.
- Prioritize accessibility.
- Recheck changes after implementation.
- Disclose unavailable testing tools.

## Expected Output

A useful visual audit should provide:

- A clear audit scope.
- Evidence-based findings.
- Severity classifications.
- Actionable recommendations.
- Targeted fixes where requested.
- Validation results.
- Remaining limitations.

## Common Mistakes

Avoid:

- Reviewing only the desktop viewport.
- Treating aesthetic preference as an objective defect.
- Making changes without inspecting existing components.
- Ignoring hover, focus, and active states.
- Claiming accessibility compliance from a single automated scan.
- Reporting unverified improvements.
- Rewriting entire pages to fix minor issues.

## Completion Checklist

- [ ] Audit scope established.
- [ ] Existing implementation inspected.
- [ ] Relevant visual evidence captured where available.
- [ ] Layout reviewed.
- [ ] Typography reviewed.
- [ ] Colors and components reviewed.
- [ ] Responsive behavior checked.
- [ ] Accessibility considered.
- [ ] Findings prioritized.
- [ ] Corrections validated.
- [ ] Remaining limitations documented.
