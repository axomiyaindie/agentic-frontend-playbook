# Color Systems & Design Tokens

Color is one of the most important foundations of a visual design system.

A well-designed color system creates visual consistency, communicates hierarchy, reinforces brand identity, and improves usability.

For AI coding agents, color selection should not be a collection of arbitrary hexadecimal values. It should be a structured system of reusable design tokens with clear semantic meaning.

This guide covers color theory, palette creation, design tokens, CSS variables, dark mode, accessibility, gradients, and implementation workflows.

## 1. Understanding Color Systems

A color system is a structured collection of colors used throughout an application or website.

It typically includes:

- Brand colors.
- Primary and secondary colors.
- Background colors.
- Surface colors.
- Text colors.
- Border colors.
- Interactive states.
- Feedback colors.
- Decorative colors.
- Dark-mode equivalents.

A good color system should be:

1. Consistent across the application.
2. Accessible to users with different visual needs.
3. Easy to maintain.
4. Scalable as the product grows.
5. Reusable across components.
6. Adaptable to different themes.

Avoid defining unrelated colors separately inside every component.

## 2. Color Theory Fundamentals

Understanding basic color theory helps designers and developers create intentional palettes.

### Hue

Hue represents the color family, such as red, blue, green, or yellow.

### Saturation

Saturation describes the intensity or vividness of a color.

High saturation produces vivid colors. Low saturation produces muted colors.

### Lightness

Lightness describes how bright or dark a color appears.

### Temperature

Colors can feel warm or cool.

- Warm colors: red, orange, yellow.
- Cool colors: blue, green, violet.

These properties influence how a design feels and how visual elements relate to each other.

## 3. Common Color Relationships

Color theory provides useful starting points for creating palettes.

| Relationship | Description | Typical use |
|---|---|---|
| Monochromatic | Variations of one hue | Minimal interfaces |
| Analogous | Neighboring hues | Harmonious palettes |
| Complementary | Opposite hues | Strong contrast |
| Split complementary | One hue with two neighboring opposites | Balanced visual variety |
| Triadic | Three evenly spaced hues | Expressive brands |

These relationships are starting points, not strict rules.

A production interface still needs carefully selected background, text, border, and interaction colors.

## 4. Defining a Brand Palette

Start by identifying the product's visual personality.

Examples:

| Brand direction | Possible palette direction |
|---|---|
| Enterprise SaaS | Blue, slate, neutral gray |
| Healthcare | Teal, blue, soft neutrals |
| Finance | Navy, green, restrained accents |
| Creative portfolio | Expressive colors and neutral backgrounds |
| Premium product | Muted neutrals with selective accents |
| Developer tools | Dark surfaces and clear accent colors |

A palette should support the product's audience and positioning.

Do not choose a color merely because it is currently fashionable.

### A practical palette structure

A typical product palette contains:

- One primary brand color.
- One secondary color, when needed.
- One accent color, when needed.
- A neutral scale.
- Semantic feedback colors.

The neutral scale is particularly important because most interface surfaces, text, and borders rely on neutral colors.

## 5. Building a Neutral Color Scale

Neutral colors form the foundation of most interfaces.

Example:

```css
:root {
  --neutral-50: #fafafa;
  --neutral-100: #f4f4f5;
  --neutral-200: #e4e4e7;
  --neutral-300: #d4d4d8;
  --neutral-400: #a1a1aa;
  --neutral-500: #71717a;
  --neutral-600: #52525b;
  --neutral-700: #3f3f46;
  --neutral-800: #27272a;
  --neutral-900: #18181b;
  --neutral-950: #09090b;
}
```

These values are illustrative. Adjust the scale to the actual brand and contrast requirements.

### Recommended uses

| Token | Common usage |
|---|---|
| `neutral-50` | Lightest surfaces |
| `neutral-100` | Subtle backgrounds |
| `neutral-200` | Borders and dividers |
| `neutral-300` | Stronger borders |
| `neutral-400` | Muted icons |
| `neutral-500` | Secondary text candidates |
| `neutral-600` | Secondary content |
| `neutral-700` | Strong text candidates |
| `neutral-800` | Headings and dark surfaces |
| `neutral-900` | Primary dark text |
| `neutral-950` | Deep backgrounds |

Do not assume a token is accessible for every purpose. Verify actual foreground and background combinations.

## 6. Creating a Brand Color Scale

A brand color should have multiple shades for different interface contexts.

Example:

```css
:root {
  --brand-50: #eff6ff;
  --brand-100: #dbeafe;
  --brand-200: #bfdbfe;
  --brand-300: #93c5fd;
  --brand-400: #60a5fa;
  --brand-500: #3b82f6;
  --brand-600: #2563eb;
  --brand-700: #1d4ed8;
  --brand-800: #1e40af;
  --brand-900: #1e3a8a;
  --brand-950: #172554;
}
```

This is an example blue palette, not a universal brand recommendation.

A scale makes it easier to support:

- Buttons.
- Links.
- Focus states.
- Hover backgrounds.
- Active navigation.
- Selected elements.
- Subtle highlights.
- Dark and light themes.

Do not automatically use the same shade for text, backgrounds, borders, and interactive states.

## 7. Semantic Color Tokens

Semantic tokens describe what a color means rather than what color it physically is.

For example:

```css
:root {
  --color-primary: var(--brand-600);
  --color-primary-hover: var(--brand-700);

  --color-background: var(--neutral-50);
  --color-surface: #ffffff;
  --color-surface-muted: var(--neutral-100);

  --color-text-primary: var(--neutral-900);
  --color-text-secondary: var(--neutral-600);
  --color-text-muted: var(--neutral-500);

  --color-border: var(--neutral-200);
  --color-border-strong: var(--neutral-300);

  --color-success: #15803d;
  --color-warning: #b45309;
  --color-danger: #b91c1c;
  --color-info: #0369a1;
}
```

Semantic tokens make the design system easier to maintain.

For example, changing `--color-primary` can update the primary brand color throughout the application without editing every component.

### Why semantic tokens matter

Compare:

```css
.button {
  background: #2563eb;
}
```

With:

```css
.button {
  background: var(--color-primary);
}
```

The second approach is easier to theme, maintain, and reuse.

Prefer semantic tokens in component styles.

## 8. Design Token Architecture

A scalable system can separate raw palette values from semantic meanings and component-specific decisions.

A useful three-layer architecture:

### Layer 1: Primitive tokens

Raw values without interface-specific meaning.

```css
:root {
  --blue-600: #2563eb;
  --gray-900: #18181b;
  --white: #ffffff;
}
```

### Layer 2: Semantic tokens

Tokens that describe the role of a color.

```css
:root {
  --color-primary: var(--blue-600);
  --color-text-primary: var(--gray-900);
  --color-surface: var(--white);
}
```

### Layer 3: Component tokens

Tokens that describe a component-specific decision.

```css
:root {
  --button-primary-bg: var(--color-primary);
  --button-primary-text: #ffffff;
  --button-primary-hover: #1d4ed8;
}
```

Not every project needs all three layers. Start with a simple structure and introduce component-level tokens when they provide genuine value.

## 9. CSS Custom Properties

CSS custom properties are a practical way to implement design tokens.

Example:

```css
:root {
  --color-background: #ffffff;
  --color-surface: #f8fafc;
  --color-text-primary: #0f172a;
  --color-text-secondary: #475569;
  --color-primary: #2563eb;
  --color-border: #e2e8f0;
}
```

Use them in components:

```css
body {
  background: var(--color-background);
  color: var(--color-text-primary);
}

.card {
  background: var(--color-surface);
  border: 1px solid var(--color-border);
}

.button-primary {
  background: var(--color-primary);
  color: #ffffff;
}
```

CSS variables can also be overridden at different scopes.

```css
.dashboard {
  --color-surface: #f1f5f9;
}
```

Use scoped overrides carefully. Global semantic tokens should remain predictable.

## 10. Dark Mode Architecture

Dark mode should be a deliberate theme, not simply an inversion of light-mode colors.

Dark interfaces need appropriate:

- Background colors.
- Elevated surfaces.
- Text contrast.
- Borders.
- Interactive states.
- Shadows.
- Feedback colors.
- Focus indicators.

Example:

```css
:root {
  color-scheme: light;

  --color-background: #ffffff;
  --color-surface: #f8fafc;
  --color-text-primary: #0f172a;
  --color-text-secondary: #475569;
  --color-border: #e2e8f0;
  --color-primary: #2563eb;
}

[data-theme="dark"] {
  color-scheme: dark;

  --color-background: #09090b;
  --color-surface: #18181b;
  --color-text-primary: #fafafa;
  --color-text-secondary: #a1a1aa;
  --color-border: #3f3f46;
  --color-primary: #60a5fa;
}
```

### Theme switching

A simple theme selector can use a root attribute:

```js
document.documentElement.dataset.theme = "dark";
```

A production implementation should also consider:

- User preference.
- System preference.
- Persistent theme selection.
- Server-rendering behavior.
- Avoiding a flash of the wrong theme.
- Theme-specific component states.

### System preference

CSS can detect the operating-system preference:

```css
@media (prefers-color-scheme: dark) {
  /* System dark theme styles */
}
```

If the application supports manual theme selection, define how manual preferences interact with the system setting.

## 11. Semantic Feedback Colors

Feedback colors communicate application states.

Common semantic categories:

| State | Typical meaning |
|---|---|
| Success | Completed successfully |
| Warning | Requires attention |
| Danger | Error or destructive action |
| Info | Informational message |
| Neutral | General status |

Example:

```css
:root {
  --color-success: #15803d;
  --color-success-bg: #f0fdf4;

  --color-warning: #a16207;
  --color-warning-bg: #fefce8;

  --color-danger: #b91c1c;
  --color-danger-bg: #fef2f2;

  --color-info: #0369a1;
  --color-info-bg: #f0f9ff;
}
```

Always test the foreground and background combinations.

Do not rely exclusively on color to communicate a state. Pair color with text, icons, or another visual indicator.

## 12. Accessibility and Color Contrast

Color accessibility is a core design-system requirement.

WCAG contrast requirements commonly used for text are:

| Content | Minimum contrast |
|---|---:|
| Normal text, AA | 4.5:1 |
| Large text, AA | 3:1 |
| Normal text, AAA | 7:1 |
| Large text, AAA | 4.5:1 |

Large text generally means at least 18pt regular or 14pt bold.

For user-interface components and meaningful graphical objects, WCAG 2.2 Success Criterion 1.4.11 generally requires a 3:1 contrast ratio against adjacent colors, subject to its exceptions.

### Common accessibility mistakes

- Light gray text on white backgrounds.
- Low-contrast placeholder text.
- Muted labels that are difficult to read.
- Colored text on similar backgrounds.
- Focus indicators with insufficient contrast.
- Status messages communicated only through color.
- Dark-mode colors copied directly from light mode.

### Useful contrast tools

- [WebAIM Contrast Checker](https://webaim.org/resources/contrastchecker/)
- [Colour Contrast Analyser](https://www.tpgi.com/color-contrast-checker/)
- [Accessible Colors](https://accessible-colors.com/)
- [W3C WCAG 2.2](https://www.w3.org/TR/WCAG22/)

Test real color pairs rather than assuming a palette is accessible.

## 13. Gradients

Gradients add depth and visual interest.

Common types:

- Linear gradients.
- Radial gradients.
- Conic gradients.
- Layered gradients.
- Mesh-style gradients.

### Linear gradient

```css
.hero {
  background: linear-gradient(
    135deg,
    #0f172a,
    #1e3a8a,
    #2563eb
  );
}
```

### Radial gradient

```css
.hero {
  background:
    radial-gradient(
      circle at 50% 20%,
      rgba(59, 130, 246, 0.25),
      transparent 60%
    ),
    #09090b;
}
```

### Layered gradient

```css
.hero {
  background:
    radial-gradient(
      circle at 20% 20%,
      rgba(59, 130, 246, 0.2),
      transparent 35%
    ),
    radial-gradient(
      circle at 80% 70%,
      rgba(168, 85, 247, 0.16),
      transparent 40%
    ),
    #09090b;
}
```

### Gradient best practices

- Preserve text readability.
- Avoid excessive color combinations.
- Use gradients to reinforce hierarchy.
- Keep backgrounds visually consistent.
- Test gradients on different displays.
- Avoid unnecessary animated gradients.
- Consider performance when using large blurred layers.

Gradients should enhance the design, not replace a coherent color system.

## 14. Color in Component States

Interactive components require deliberate color states.

A button may need:

- Default.
- Hover.
- Active.
- Focus-visible.
- Disabled.
- Loading.

Example:

```css
.button-primary {
  background: var(--color-primary);
  color: #ffffff;
}

.button-primary:hover {
  background: var(--color-primary-hover);
}

.button-primary:focus-visible {
  outline: 3px solid var(--color-focus);
  outline-offset: 3px;
}

.button-primary:disabled {
  opacity: 0.55;
  cursor: not-allowed;
}
```

Define a focus token:

```css
:root {
  --color-focus: #2563eb;
}
```

Disabled components should still be understandable and distinguishable.

Do not rely on opacity alone if it makes text or controls difficult to perceive.

## 15. Using Color Systems with Tailwind CSS

Tailwind CSS can consume design tokens through CSS variables.

A practical approach:

```css
@import "tailwindcss";

@theme inline {
  --color-primary: var(--color-primary);
  --color-background: var(--color-background);
  --color-surface: var(--color-surface);
  --color-foreground: var(--color-text-primary);
}
```

The example illustrates token integration. Check the exact configuration conventions for the Tailwind version and project setup before implementation.

Components can then use semantic utility classes when the theme configuration exposes them.

```jsx
<button className="bg-primary text-white">
  Get Started
</button>
```

Avoid mixing arbitrary color values with semantic tokens throughout the codebase.

For Tailwind projects, inspect the existing version and configuration before changing the theme architecture.

## 16. Design Tokens Across Platforms

Larger products may share visual foundations across:

- Web applications.
- Mobile applications.
- Marketing websites.
- Design tools.
- Component libraries.
- Documentation sites.

A shared token source can help keep these platforms consistent.

Example JSON structure:

```json
{
  "color": {
    "brand": {
      "primary": {
        "value": "#2563eb"
      }
    },
    "background": {
      "default": {
        "value": "#ffffff"
      }
    },
    "text": {
      "primary": {
        "value": "#0f172a"
      }
    }
  }
}
```

For cross-platform design tokens, consider the [Design Tokens Community Group format](https://www.designtokens.org/).

A shared source of truth can be transformed into platform-specific formats through a build process.

Do not assume that every design tool or framework uses the same token format.

## 17. Common Color-System Mistakes

Avoid these common problems:

### Arbitrary color values

Repeated hardcoded colors make maintenance difficult.

**Better:** Define reusable tokens.

### Too many brand colors

An oversized palette weakens visual consistency.

**Better:** Establish a clear primary palette and introduce additional colors only when they have a purpose.

### Poor contrast

A visually attractive palette can still be difficult to read.

**Better:** Validate text and component contrast.

### Inconsistent semantic meaning

Using green for errors in one component and success in another creates confusion.

**Better:** Define semantic conventions.

### Inadequate dark mode

Simply inverting every color often creates harsh and inaccessible interfaces.

**Better:** Design and validate dark-mode surfaces and text separately.

### Excessive gradients

Too many competing gradients make interfaces visually noisy.

**Better:** Use gradients selectively.

### Color-only communication

Users may not recognize states if color is the only indicator.

**Better:** Include text, icons, or additional visual cues.

## 18. AI Coding Agent Workflow

AI coding agents should follow a consistent process when implementing color systems.

### Before implementation

1. Inspect the existing project structure.
2. Identify the styling framework.
3. Locate existing color definitions.
4. Inspect the brand identity or reference designs.
5. Identify light and dark theme requirements.
6. Identify accessibility requirements.
7. Understand component naming conventions.

### During implementation

1. Define primitive palette values.
2. Create semantic color tokens.
3. Add CSS custom properties.
4. Define theme variants.
5. Map tokens into the styling framework.
6. Replace duplicated hardcoded values.
7. Define interactive states.
8. Check contrast.
9. Test all major components.

### During visual review

- Compare the interface against its intended visual direction.
- Check consistency across pages.
- Inspect text and surface contrast.
- Check hover and focus states.
- Review light and dark themes.
- Inspect gradients and overlays.
- Check disabled and error states.

### Before completion

- Confirm there are no unnecessary duplicate tokens.
- Verify semantic token names.
- Check responsive layouts.
- Run the project's available tests.
- Confirm the production build succeeds.
- Document theme behavior.

Do not invent a new brand palette when an established design system already exists.

## 19. Recommended File Organization

A larger frontend project may organize color tokens like this:

```text
src/
├── styles/
│   ├── tokens/
│   │   ├── colors.css
│   │   ├── typography.css
│   │   └── spacing.css
│   ├── themes/
│   │   ├── light.css
│   │   └── dark.css
│   ├── globals.css
│   └── utilities.css
├── components/
└── app/
```

For smaller projects, keeping tokens in one global stylesheet may be sufficient.

Choose the simplest architecture that supports the project's actual needs.

## 20. Production Checklist

### Palette

- [ ] Brand palette is clearly defined.
- [ ] Neutral scale is established.
- [ ] Semantic colors are documented.
- [ ] Color usage is consistent.

### Tokens

- [ ] Primitive tokens are defined.
- [ ] Semantic tokens are available.
- [ ] Component tokens are introduced only when useful.
- [ ] CSS custom properties are reusable.
- [ ] No unnecessary hardcoded color duplication exists.

### Themes

- [ ] Light theme is implemented.
- [ ] Dark theme is designed intentionally.
- [ ] System preference is considered.
- [ ] Manual theme selection works when supported.
- [ ] Theme changes do not create visual inconsistencies.

### Accessibility

- [ ] Text contrast is validated.
- [ ] Large text contrast is validated.
- [ ] Interactive component contrast is checked.
- [ ] Focus states are visible.
- [ ] Color is not the only way to communicate meaning.

### Quality

- [ ] Gradients are used intentionally.
- [ ] Component states are defined.
- [ ] Responsive layouts are checked.
- [ ] Styling conventions match the project.
- [ ] Production build succeeds.

## 21. Further Learning

Official and useful resources:

- [W3C WCAG 2.2](https://www.w3.org/TR/WCAG22/)
- [WebAIM Contrast Checker](https://webaim.org/resources/contrastchecker/)
- [MDN CSS Custom Properties](https://developer.mozilla.org/en-US/docs/Web/CSS/Guides/Cascading_variables/Using_custom_properties)
- [Tailwind CSS Documentation](https://tailwindcss.com/docs)
- [Design Tokens Community Group](https://www.designtokens.org/)
- [Material Design Color System](https://m3.material.io/styles/color/overview)
- [Radix Colors](https://www.radix-ui.com/colors)

---

## 22. Design Systems Documentation

This guide establishes the color foundation for the playbook.

Related guides:

- [Typography](./typography.md)
- [Components](./components.md)

A successful design system connects color, typography, spacing, layout, and reusable components into one consistent visual language.