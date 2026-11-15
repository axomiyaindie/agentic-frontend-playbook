# Responsive Design

Responsive design is the practice of building interfaces that adapt to different screen sizes, input methods, and device capabilities.

A responsive application should remain usable, readable, and visually consistent across mobile phones, tablets, laptops, and desktop displays.

This guide establishes practical responsive design principles for modern frontend applications.

## 1. Core Principles

Build responsive interfaces around these principles:

- **Content first:** Let content and functionality determine layout requirements.
- **Fluid layouts:** Use flexible containers and sizing rather than fixed dimensions everywhere.
- **Progressive enhancement:** Start with a reliable experience and enhance it for capable devices.
- **Consistency:** Preserve the same visual language across screen sizes.
- **Accessibility:** Support different input methods, zoom levels, and assistive technologies.
- **Performance:** Avoid unnecessarily loading large assets or expensive effects on constrained devices.

Responsive design is more than shrinking a desktop layout.

## 2. Mobile-First Development

A mobile-first approach starts with the smallest practical viewport and progressively enhances the layout.

Benefits include:

- Prioritizing essential content.
- Reducing unnecessary interface complexity.
- Encouraging flexible component design.
- Identifying mobile usability problems early.
- Supporting constrained devices and network conditions.

Example:

```css
.container {
  width: min(100% - 2rem, 1200px);
  margin-inline: auto;
}

.grid {
  display: grid;
  grid-template-columns: 1fr;
  gap: 1rem;
}

@media (min-width: 48rem) {
  .grid {
    grid-template-columns: repeat(2, minmax(0, 1fr));
  }
}

@media (min-width: 72rem) {
  .grid {
    grid-template-columns: repeat(3, minmax(0, 1fr));
  }
}
```

Breakpoints should be selected according to where the content needs a layout change, not simply copied from a device list.

## 3. Viewport Configuration

Ensure mobile browsers use the correct viewport dimensions.

```html
<meta name="viewport" content="width=device-width, initial-scale=1">
```

Without suitable viewport configuration, mobile browsers may render pages at unexpected virtual widths.

## 4. Fluid Layouts and Sizing

Prefer flexible CSS sizing tools:

- `%` for proportional sizing.
- `rem` for scalable typography and spacing.
- `minmax()` for flexible grid tracks.
- `min()`, `max()`, and `clamp()` for bounded fluid values.
- `min-height` and `max-width` when appropriate.

Example:

```css
.hero-title {
  font-size: clamp(2.25rem, 5vw, 5rem);
}

.page-container {
  width: min(100% - 2rem, 1200px);
  margin-inline: auto;
}
```

Avoid fixed widths that create horizontal overflow on narrow screens.

## 5. Responsive Typography

Typography should remain readable across viewport sizes.

Consider:

- Fluid heading sizes.
- Comfortable line heights.
- Appropriate paragraph widths.
- Consistent type scales.
- Text wrapping and long words.
- Minimum readable sizes.

Example:

```css
body {
  font-size: 1rem;
  line-height: 1.6;
}

h1 {
  font-size: clamp(2rem, 5vw, 4.5rem);
  line-height: 1.1;
  max-width: 16ch;
}
```

Do not rely exclusively on viewport width for typography decisions. Content length and readability matter too.

## 6. Responsive Images and Media

Images should adapt to their containers without distortion.

```css
img,
video {
  display: block;
  max-width: 100%;
}

img {
  height: auto;
}
```

Use appropriate image sources and dimensions when multiple resolutions are available.

Example:

```html
<img
  src="product-small.webp"
  srcset="
    product-small.webp 480w,
    product-medium.webp 960w,
    product-large.webp 1600w
  "
  sizes="(max-width: 600px) 100vw, 50vw"
  alt="Product displayed on a desk"
>
```

Use `object-fit` and `aspect-ratio` when an image needs a consistent presentation.

## 7. Responsive Navigation

Navigation should remain understandable and usable on every screen.

Consider:

- Desktop navigation menus.
- Collapsible mobile navigation.
- Clear menu controls.
- Keyboard accessibility.
- Focus management.
- Appropriate touch targets.
- Predictable open and close behavior.

Avoid hiding important navigation without providing an accessible alternative.

## 8. Responsive Components

Components should adapt to their available space.

Examples:

- Cards may move from multiple columns to one column.
- Sidebars may become drawers.
- Tables may use horizontal scrolling or an alternative compact layout.
- Dialogs may become full-screen interfaces on small displays.
- Toolbars may reorganize their actions.

Use container queries when a component needs to respond to its parent container rather than the entire viewport.

Example:

```css
.card-container {
  container-type: inline-size;
}

.card {
  display: grid;
  grid-template-columns: 1fr;
  gap: 1rem;
}

@container (min-width: 36rem) {
  .card {
    grid-template-columns: 12rem 1fr;
  }
}
```

## 9. Input Methods and Accessibility

Responsive experiences must support different ways of interacting.

Check:

- Keyboard navigation.
- Touch interactions.
- Visible focus indicators.
- Sufficient target sizes.
- Accessible form controls.
- Browser zoom and text resizing.
- Reduced-motion preferences.
- Hover-independent functionality.

Do not make essential functionality available only through hover.

## 10. Responsive 3D and Visual Effects

3D scenes and advanced visual effects require additional consideration.

- Reduce unnecessary geometry and rendering work on constrained devices.
- Adapt camera framing to viewport proportions.
- Use appropriate asset resolutions.
- Avoid expensive post-processing by default.
- Provide useful loading and fallback states.
- Consider static alternatives when 3D is not essential.
- Respect reduced-motion preferences.

Responsive behavior should preserve the purpose of the experience, even when visual complexity must be reduced.

## 11. Testing Responsive Interfaces

Test layouts at multiple viewport sizes rather than relying on a single desktop and mobile preset.

Check:

- Narrow mobile widths.
- Larger mobile widths.
- Tablet layouts.
- Laptop displays.
- Wide desktop screens.
- Browser zoom.
- Portrait and landscape orientations.
- Touch and keyboard interactions.

Look for:

- Horizontal overflow.
- Clipped content.
- Broken grids.
- Overlapping elements.
- Unreadable text.
- Inaccessible navigation.
- Incorrect image scaling.
- Unexpected layout shifts.

Use browser developer tools and real devices where possible.

## 12. Responsive Design Checklist

Before completing an interface:

- [ ] Viewport configuration is correct.
- [ ] Layout adapts to different widths.
- [ ] Breakpoints are content-driven