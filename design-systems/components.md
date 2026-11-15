# Reusable UI Components & Component Architecture

Reusable components are the building blocks of modern frontend applications.

A well-designed component system improves consistency, maintainability, accessibility, development speed, and collaboration between developers and AI coding agents.

Instead of implementing the same interface patterns repeatedly, developers create reusable components with predictable APIs, variants, states, and behaviors.

This guide covers component architecture, composition, design-system integration, accessibility, React patterns, testing, and AI agent workflows.

## 1. Understanding Component Systems

A component is an independent, reusable piece of interface functionality.

Examples include:

- Buttons.
- Inputs.
- Cards.
- Navigation bars.
- Dialogs.
- Dropdown menus.
- Tabs.
- Tooltips.
- Badges.
- Alerts.
- Tables.
- Sidebars.
- Modals.
- Form controls.

A component system is a collection of these components, organized around shared design and engineering conventions.

A good component system should be:

1. Consistent.
2. Reusable.
3. Accessible.
4. Composable.
5. Predictable.
6. Maintainable.
7. Well documented.
8. Easy to extend.

The goal is not to create a component for every HTML element. The goal is to identify patterns that genuinely benefit from reuse.

## 2. Component Architecture

A scalable frontend separates components according to their responsibilities.

A practical architecture:

```text
src/
├── components/
│   ├── ui/
│   │   ├── button/
│   │   ├── input/
│   │   ├── card/
│   │   ├── dialog/
│   │   ├── badge/
│   │   └── tooltip/
│   ├── layout/
│   │   ├── header/
│   │   ├── footer/
│   │   └── sidebar/
│   ├── forms/
│   │   ├── login-form/
│   │   └── search-form/
│   └── features/
│       ├── dashboard/
│       └── product/
├── hooks/
├── lib/
├── styles/
└── app/
```

### UI components

Generic interface elements such as buttons, inputs, and badges.

### Layout components

Shared structural elements such as headers, footers, navigation, and sidebars.

### Feature components

Components tied to a particular product feature or business domain.

### Form components

Reusable form structures, validation patterns, and field combinations.

Keep generic components independent from feature-specific business logic whenever possible.

## 3. Component API Design

A component API defines how developers use and configure a component.

Example:

```jsx
<Button
  variant="primary"
  size="large"
  disabled={false}
>
  Get Started
</Button>
```

A good component API should be:

- Clear.
- Consistent.
- Easy to understand.
- Predictable.
- Flexible without unnecessary complexity.

Prefer meaningful prop names.

Good:

```jsx
<Button
  variant="secondary"
  size="small"
  loading={isLoading}
>
  Save
</Button>
```

Avoid:

```jsx
<Button
  type="blue"
  mode="two"
  activeThing
>
  Save
</Button>
```

Use TypeScript to make component contracts explicit.

## 4. Component Variants

Variants allow one component to support different visual styles.

A button may support:

- Primary.
- Secondary.
- Outline.
- Ghost.
- Destructive.
- Link.

Example:

```tsx
type ButtonVariant =
  | "primary"
  | "secondary"
  | "outline"
  | "ghost"
  | "destructive";

type ButtonProps = {
  variant?: ButtonVariant;
  children: React.ReactNode;
};
```

Example implementation:

```tsx
function Button({
  variant = "primary",
  children
}: ButtonProps) {
  return (
    <button className={`button button-${variant}`}>
      {children}
    </button>
  );
}
```

This is a simplified illustration. Production implementations should handle class composition, native button attributes, accessibility, and event behavior.

Avoid creating separate components for every minor visual variation when a shared component with a well-defined variant is more appropriate.

## 5. Component Sizes

Reusable components often need consistent size variants.

Example button sizes:

| Size | Typical height |
|---|---:|
| Small | 32px |
| Medium | 40px |
| Large | 48px |
| Extra large | 56px |

These are example dimensions. Adapt them to the design system and interaction requirements.

TypeScript example:

```tsx
type ButtonSize =
  | "small"
  | "medium"
  | "large";
```

Use shared spacing and typography tokens so sizes remain consistent.

Do not create arbitrary size variants for individual pages without a clear requirement.

## 6. Component States

Interactive components need predictable states.

A button may have:

1. Default.
2. Hover.
3. Focus-visible.
4. Active.
5. Disabled.
6. Loading.

An input may have:

1. Default.
2. Hover.
3. Focus.
4. Filled.
5. Invalid.
6. Disabled.
7. Read-only.

Example:

```css
.button {
  background: var(--color-primary);
  color: white;
}

.button:hover {
  background: var(--color-primary-hover);
}

.button:focus-visible {
  outline: 3px solid var(--color-focus);
  outline-offset: 3px;
}

.button:disabled {
  opacity: 0.55;
  cursor: not-allowed;
}
```

Do not treat hover as the only indication of interactivity.

Keyboard users need equally clear interaction feedback.

## 7. Building a Button Component

Buttons are among the most frequently reused UI components.

A production-ready button should support:

- Variants.
- Sizes.
- Disabled state.
- Loading state.
- Icons.
- Full-width layout when required.
- Native button attributes.
- Keyboard interaction.
- Accessible naming.

Example:

```tsx
import type {
  ButtonHTMLAttributes,
  ReactNode
} from "react";

type ButtonProps =
  ButtonHTMLAttributes<HTMLButtonElement> & {
    variant?: "primary" | "secondary" | "outline";
    size?: "small" | "medium" | "large";
    loading?: boolean;
    children: ReactNode;
  };

export function Button({
  variant = "primary",
  size = "medium",
  loading = false,
  disabled,
  children,
  ...props
}: ButtonProps) {
  return (
    <button
      className={`button button-${variant} button-${size}`}
      disabled={disabled || loading}
      aria-busy={loading || undefined}
      {...props}
    >
      {children}
    </button>
  );
}
```

A complete implementation should also consider:

- A visible loading indicator.
- Preventing duplicate submissions.
- Icon alignment.
- Stable button dimensions.
- Loading announcements where appropriate.

Use `type="button"` for buttons that should not submit a form. Use `type="submit"` when form submission is intended.

Do not use a clickable `div` as a substitute for a native button.

## 8. Building Input Components

Input components should provide a consistent experience across forms.

Common properties include:

- Label.
- Placeholder.
- Description.
- Error message.
- Disabled state.
- Required state.
- Input type.
- Value.
- Change handler.

Example:

```tsx
type InputProps = {
  label: string;
  id: string;
  error?: string;
} & React.InputHTMLAttributes<HTMLInputElement>;

export function Input({
  label,
  id,
  error,
  ...props
}: InputProps) {
  const errorId = `${id}-error`;

  return (
    <div className="form-field">
      <label htmlFor={id}>
        {label}
      </label>

      <input
        id={id}
        aria-invalid={Boolean(error)}
        aria-describedby={error ? errorId : undefined}
        {...props}
      />

      {error && (
        <p id={errorId} role="alert">
          {error}
        </p>
      )}
    </div>
  );
}
```

A production form system should also consider:

- Help text.
- Required indicators.
- Validation timing.
- Server errors.
- Accessible descriptions.
- Consistent spacing.
- Password visibility controls where appropriate.

Use native input elements whenever possible.

## 9. Card Components

Cards group related information into a visually recognizable unit.

Common card types:

- Product cards.
- Feature cards.
- Statistics cards.
- Profile cards.
- Article cards.
- Pricing cards.
- Dashboard cards.

A card may contain:

- Header.
- Image.
- Title.
- Description.
- Metadata.
- Actions.
- Footer.

Example:

```tsx
type CardProps = {
  title: string;
  description?: string;
  children?: React.ReactNode;
};

export function Card({
  title,
  description,
  children
}: CardProps) {
  return (
    <article className="card">
      <header className="card-header">
        <h3>{title}</h3>

        {description && (
          <p>{description}</p>
        )}
      </header>

      <div className="card-content">
        {children}
      </div>
    </article>
  );
}
```

Not every card should be clickable.

If the whole card navigates somewhere, use an appropriate link or a carefully structured interactive pattern.

Avoid nesting interactive elements such as buttons or links inside another clickable button.

## 10. Component Composition

Composition allows developers to combine smaller components into larger interfaces.

Instead of building one large component with dozens of conditional props, create smaller components that work together.

Example:

```tsx
function PricingCard() {
  return (
    <Card title="Professional">
      <PricingAmount />
      <PricingFeatures />
      <Button variant="primary">
        Choose Plan
      </Button>
    </Card>
  );
}
```

### Compound components

Some components are naturally composed of related subcomponents.

Example API:

```jsx
<Dialog>
  <Dialog.Trigger>
    Open settings
  </Dialog.Trigger>

  <Dialog.Content>
    <Dialog.Header>
      <Dialog.Title>Settings</Dialog.Title>
    </Dialog.Header>

    <Dialog.Description>
      Manage your preferences.
    </Dialog.Description>

    <Dialog.Footer>
      <Button>Save</Button>
    </Dialog.Footer>
  </Dialog.Content>
</Dialog>
```

Compound components can provide a flexible API while keeping related behavior organized.

Use them when a component has a meaningful internal structure.

Do not introduce complicated compound APIs for simple elements.

## 11. Component Reusability vs Over-Abstraction

Not every repeated piece of markup needs a reusable component.

Extract a component when:

- The pattern appears in multiple places.
- It has meaningful behavior.
- It requires consistent styling.
- It has a stable interface.
- It benefits from independent testing.
- It represents a recognizable design-system element.

Avoid abstraction when:

- The markup is extremely small.
- The pattern appears only once.
- The abstraction adds more complexity than it removes.
- The API requires many unrelated configuration props.

A good component system balances reuse with clarity.

## 12. Accessibility in Components

Accessibility must be built into reusable components from the beginning.

### Buttons

- Use native `<button>` elements.
- Provide an accessible name.
- Support keyboard interaction.
- Show visible focus.
- Communicate disabled and loading states.

### Links

- Use `<a>` elements for navigation.
- Use descriptive link text.
- Preserve expected browser behavior.
- Do not use links for actions that should be buttons.

### Dialogs

- Provide an accessible title.
- Manage focus appropriately.
- Support Escape when appropriate.
- Keep keyboard navigation within modal content.
- Restore focus when the dialog closes.
- Prevent background interaction while modal.

### Inputs

- Associate labels with fields.
- Identify validation errors.
- Provide useful descriptions.
- Preserve keyboard navigation.

### Menus

- Use established interaction patterns.
- Manage focus correctly.
- Support expected keyboard behavior.
- Do not confuse a navigation list with an application menu.

For complex widgets, use established accessibility patterns rather than inventing custom keyboard behavior.

Useful reference:

[WAI-ARIA Authoring Practices Guide](https://www.w3.org/WAI/ARIA/apg/)

## 13. Component Styling Architecture

A component system should use shared design tokens.

Example:

```css
:root {
  --radius-sm: 0.375rem;
  --radius-md: 0.625rem;
  --radius-lg: 1rem;

  --spacing-1: 0.25rem;
  --spacing-2: 0.5rem;
  --spacing-3: 0.75rem;
  --spacing-4: 1rem;

  --transition-fast: 150ms ease;
  --transition-normal: 250ms ease;
}
```

A component can then consume these tokens:

```css
.card {
  padding: var(--spacing-4);
  border-radius: var(--radius-lg);
  border: 1px solid var(--color-border);
  background: var(--color-surface);
}

.button {
  border-radius: var(--radius-md);
  transition: background var(--transition-fast);
}
```

The goal is to make component styling consistent and centrally maintainable.

Related guide: [Colors](./colors.md).

## 14. React Component Patterns

React supports several useful component patterns.

### Props-based components

Best for simple reusable elements.

```tsx
<Badge variant="success">
  Active
</Badge>
```

### Children composition

Useful for flexible content structures.

```tsx
<Card>
  <CardContent />
</Card>
```

### Controlled components

The parent owns the state.

```tsx
function SearchExample() {
  const [query, setQuery] = React.useState("");

  return (
    <input
      value={query}
      onChange={(event) => setQuery(event.target.value)}
    />
  );
}
```

### Uncontrolled components

The DOM manages the input state, which can be accessed through a ref when needed.

Use controlled or uncontrolled patterns according to the interaction requirements.

Avoid mixing them accidentally.

### Polymorphic components

Some component libraries allow an element to render as a different HTML element.

This can be useful, but it introduces additional typing and accessibility complexity.

Only use polymorphic APIs when they provide real value.

## 15. Design Tokens and Component Variants

Design tokens and component variants should work together.

Example:

```css
.button-primary {
  background: var(--color-primary);
  color: var(--color-on-primary);
}

.button-secondary {
  background: var(--color-surface);
  color: var(--color-text-primary);
  border: 1px solid var(--color-border);
}
```

A consistent token system makes it possible to change the visual language without rewriting component behavior.

Component variants should describe meaningful visual or behavioral differences, not arbitrary page-specific styling.

## 16. Tailwind CSS and Component Systems

Tailwind CSS is often used to build component systems.

Example:

```tsx
type ButtonProps = {
  variant?: "primary" | "secondary";
  children: React.ReactNode;
};

function Button({
  variant = "primary",
  children
}: ButtonProps) {
  const styles = {
    primary:
      "bg-primary text-white hover:bg-primary-hover",
    secondary:
      "border border-border bg-surface text-foreground"
  };

  return (
    <button
      className={`rounded-lg px-4 py-2 font-medium ${styles[variant]}`}
    >
      {children}
    </button>
  );
}
```

For larger systems, consider a class composition utility such as:

- `clsx`
- `tailwind-merge`
- `class-variance-authority`

These tools solve different problems:

- `clsx` helps construct conditional class names.
- `tailwind-merge` resolves conflicting Tailwind utility classes.
- `class-variance-authority` organizes component variants.

Use them when needed rather than adding dependencies automatically.

Inspect the existing project's styling architecture before introducing a new pattern.

## 17. Using Established Component Libraries

Building every component from scratch is not always the best approach.

Existing libraries can provide accessible, tested, reusable primitives.

Examples:

- [Radix UI](https://www.radix-ui.com/)
- [shadcn/ui](https://ui.shadcn.com/)
- [React Aria](https://react-spectrum.adobe.com/react-aria/)
- [Base UI](https://base-ui.com/)
- [Material UI](https://mui.com/)
- [Chakra UI](https://chakra-ui.com/)

### Choosing a library

Evaluate:

1. Accessibility.
2. Customization.
3. Styling architecture.
4. Bundle impact.
5. Framework compatibility.
6. Maintenance.
7. Documentation.
8. License.
9. Existing project conventions.

Do not install several competing component libraries without a clear reason.

### Important distinction

A component primitive library and a complete visual component system are not the same thing.

Some libraries provide behavior and accessibility primitives. Others provide ready-to-use styled components.

Understand what the project needs before choosing.

## 18. Component Documentation

Reusable components should have clear documentation.

For each component, document:

- Purpose.
- Usage.
- Props.
- Variants.
- Sizes.
- States.
- Accessibility behavior.
- Examples.
- Known limitations.

Example:

```md
# Button

A reusable action component.

## Variants

- Primary
- Secondary
- Outline
- Ghost

## Sizes

- Small
- Medium
- Large

## States

- Default
- Hover
- Focus
- Active
- Disabled
- Loading
```

Storybook and similar tools can help teams document and test component variations.

Reference:

[Storybook Documentation](https://storybook.js.org/docs)

## 19. Component Testing

Component systems need testing at multiple levels.

### Unit tests

Test component logic and behavior.

### Interaction tests

Test user actions such as:

- Clicking.
- Typing.
- Selecting.
- Opening dialogs.
- Closing menus.
- Submitting forms.

### Accessibility tests

Check:

- Accessible names.
- Labels.
- Roles.
- Keyboard behavior.
- Focus management.
- Relevant ARIA attributes.

### Visual regression tests

Compare component screenshots across versions to identify unintended visual changes.

Useful tools:

- [Vitest](https://vitest.dev/)
- [React Testing Library](https://testing-library.com/docs/react-testing-library/intro/)
- [Playwright](https://playwright.dev/)
- [Storybook](https://storybook.js.org/docs)

Testing tools should match the existing project stack.

## 20. Performance and Maintainability

A reusable component system should not introduce unnecessary runtime overhead.

Best practices:

- Keep component responsibilities clear.
- Avoid unnecessary state.
- Avoid excessive prop drilling.
- Use composition where appropriate.
- Avoid unnecessary effects.
- Keep dependencies controlled.
- Avoid premature memoization.
- Split large components when responsibilities become difficult to understand.
- Use lazy loading for genuinely expensive features.
- Profile before optimizing.

Do not add `React.memo`, `useMemo`, or `useCallback` everywhere without evidence that they solve a real performance problem.

Maintainability is more important than clever abstraction.

## 21. AI Coding Agent Workflow

AI coding agents should follow a structured workflow when creating or extending a component system.

### Before implementation

1. Inspect the existing repository.
2. Identify the frontend framework.
3. Inspect existing UI components.
4. Identify design tokens.
5. Check whether a component library already exists.
6. Understand the desired interaction.
7. Review accessibility requirements.
8. Identify existing naming conventions.

### During implementation

1. Define component responsibilities.
2. Create clear TypeScript interfaces.
3. Use semantic HTML.
4. Implement variants.
5. Implement component states.
6. Connect design tokens.
7. Add keyboard behavior.
8. Handle loading and error states.
9. Keep feature-specific logic separate.
10. Document usage.

### During visual review

- Compare component dimensions.
- Check spacing.
- Review typography.
- Check color consistency.
- Inspect borders and radius.
- Test all variants.
- Review responsive behavior.
- Test focus and hover states.

### Before completion

- Run available tests.
- Verify keyboard interaction.
- Check accessibility.
- Inspect console errors.
- Confirm TypeScript checks.
- Run the production build.
- Update documentation.

AI agents should extend existing component systems before introducing competing patterns.

## 22. Common Component Architecture Mistakes

### God components

A single component handles unrelated responsibilities.

**Better:** Split by responsibility and compose smaller components.

### Excessive abstraction

Simple markup becomes hidden behind complex APIs.

**Better:** Extract only meaningful reusable patterns.

### Inconsistent props

Similar components use unrelated naming conventions.

**Better:** Standardize prop names and variants.

### Missing states

Components support only their default appearance.

**Better:** Design hover, focus, disabled, loading, and error states where relevant.

### Inaccessible interactions

Clickable containers replace native controls.

**Better:** Use semantic HTML and established interaction patterns.

### Duplicated styling

Similar components use slightly different values.

**Better:** Use shared design tokens.

### Too many dependencies

Several libraries solve the same problem.

**Better:** Choose a consistent component architecture.

## 23. Recommended Project Structure

A scalable React component system may use:

```text
src/
├── components/
│   ├── ui/
│   │   ├── button/
│   │   │   ├── button.tsx
│   │   │   ├── button.css
│   │   │   └── index.ts
│   │   ├── input/
│   │   ├── card/
│   │   ├── dialog/
│   │   └── badge/
│   ├── layout/
│   └── features/
├── hooks/
├── lib/
├── styles/
│   ├── tokens/
│   └── themes/
└── app/
```

For smaller applications, a flatter structure is often sufficient.

Choose folder depth according to the project's size and complexity.

## 24. Production Checklist

### Architecture

- [ ] Component responsibilities are clear.
- [ ] Reusable patterns are identified.
- [ ] Feature logic is separated from generic UI.
- [ ] Component APIs are predictable.
- [ ] Composition is used where appropriate.

### Design consistency

- [ ] Components use shared tokens.
- [ ] Variants are documented.
- [ ] Sizes are consistent.
- [ ] Interaction states are defined.
- [ ] Responsive behavior is considered.

### Accessibility

- [ ] Semantic HTML is used.
- [ ] Keyboard interaction works.
- [ ] Focus states are visible.
- [ ] Inputs have labels.
- [ ] Dialogs manage focus.
- [ ] Accessible names are provided.

### Code quality

- [ ] TypeScript contracts are clear.
- [ ] Unnecessary dependencies are avoided.
- [ ] Components are not over-abstracted.
- [ ] State is managed appropriately.
- [ ] Documentation is available.

### Validation

- [ ] Component behavior is tested.
- [ ] Important variants are reviewed.
- [ ] Responsive layouts are checked.
- [ ] Accessibility is checked.
- [ ] Production build succeeds.

## 25. Further Learning

Official and useful resources:

- [React Documentation](https://react.dev/learn)
- [WAI-ARIA Authoring Practices](https://www.w3.org/WAI/ARIA/apg/)
- [Radix UI](https://www.radix-ui.com/)
- [shadcn/ui](https://ui.shadcn.com/)
- [React Aria](https://react-spectrum.adobe.com/react-aria/)
- [Base UI](https://base-ui.com/)
- [Storybook](https://storybook.js.org/docs)
- [React Testing Library](https://testing-library.com/docs/react-testing-library/intro/)
- [Playwright](https://playwright.dev/)

---

## 26. Design Systems Documentation Complete

The Design Systems section now has three foundational guides:

1. [Colors](./colors.md) — Color palettes, semantic tokens, themes, and contrast.
2. [Typography](./typography.md) — Font systems, hierarchy, responsive type, and readability.
3. [Components](./components.md) — Reusable UI architecture, variants, states, and accessibility.

Together, these guides establish the foundations of a consistent and maintainable design system for modern frontend applications.