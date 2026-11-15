# Typography Systems & Visual Hierarchy

Typography is one of the most important foundations of interface design.

It influences readability, visual hierarchy, brand personality, accessibility, and the overall quality of a digital experience.

A strong typography system goes beyond selecting attractive fonts. It defines how text is structured, sized, spaced, weighted, and presented consistently throughout an application.

For AI coding agents, typography should be implemented through reusable tokens and clear hierarchy rather than arbitrary font sizes and inconsistent styling.

This guide covers font selection, type scales, responsive typography, variable fonts, web font loading, accessibility, and implementation workflows.

## 1. Understanding Typography Systems

A typography system is a collection of rules that defines how text appears throughout a product.

It typically includes:

- Font families.
- Font weights.
- Font sizes.
- Heading hierarchy.
- Body text styles.
- Line heights.
- Letter spacing.
- Text colors.
- Responsive type scales.
- Font loading strategies.
- Text alignment and wrapping rules.

A good typography system should be:

1. Readable across different devices.
2. Consistent across application pages.
3. Accessible to different users.
4. Aligned with the brand identity.
5. Responsive to available screen space.
6. Easy to maintain and extend.

Typography should support content rather than compete with it.

## 2. Font Classification

Understanding font categories helps developers choose appropriate typefaces.

### Sans-serif

Sans-serif fonts have clean letterforms without decorative strokes.

Common uses:

- SaaS applications.
- Dashboards.
- Developer tools.
- Modern landing pages.
- Mobile interfaces.

Examples:

- Inter
- Geist
- Manrope
- DM Sans
- Plus Jakarta Sans

### Serif

Serif fonts have small decorative strokes at the ends of letterforms.

Common uses:

- Editorial websites.
- Publications.
- Premium brands.
- Long-form reading.
- Literary and cultural experiences.

Examples:

- Lora
- Merriweather
- Playfair Display
- Source Serif 4

### Monospace

Monospace fonts use equal-width character spacing.

Common uses:

- Code editors.
- Technical documentation.
- Terminal interfaces.
- Data displays.
- Developer dashboards.

Examples:

- JetBrains Mono
- IBM Plex Mono
- Fira Code
- Geist Mono

### Display fonts

Display fonts are designed for prominent visual use.

Common uses:

- Hero headings.
- Brand statements.
- Campaign graphics.
- Large editorial titles.

Display fonts should generally be used selectively rather than throughout an entire interface.

## 3. Choosing the Right Font

Font selection should consider:

- Product personality.
- Target audience.
- Reading environment.
- Language support.
- Available font weights.
- Screen rendering quality.
- Performance.
- Licensing.
- Accessibility.

### Example font directions

| Product type | Possible typography direction |
|---|---|
| Enterprise SaaS | Inter, Geist |
| Creative portfolio | Manrope, Space Grotesk |
| Editorial website | Source Serif 4, Lora |
| Developer tools | Geist, IBM Plex Sans |
| Premium brand | Carefully paired serif and sans-serif |
| Technical documentation | Inter, Source Sans 3 |

These are suggestions, not mandatory pairings.

Always inspect the actual font rendering in the interface.

### Font pairing

A typography system may use:

- One family for headings and body text.
- A display family for headings and a neutral family for body text.
- A sans-serif family with a monospace family for technical content.

Example:

```css
:root {
  --font-display: "Manrope", sans-serif;
  --font-body: "Inter", sans-serif;
  --font-mono: "JetBrains Mono", monospace;
}
```

Avoid introducing many font families without a clear design reason.

Two complementary families are often sufficient.

## 4. Typography Hierarchy

Visual hierarchy helps users understand the importance and relationship of content.

A typical interface hierarchy includes:

| Level | Typical purpose |
|---|---|
| Display | Hero statements and major visual headings |
| H1 | Main page title |
| H2 | Major section headings |
| H3 | Subsection headings |
| H4 | Component or content headings |
| Body large | Introductory content |
| Body | Main reading content |
| Body small | Supporting content |
| Caption | Metadata and annotations |
| Label | Form fields and controls |

Do not use heading levels solely because of their visual appearance.

Semantic heading structure should reflect the document's actual hierarchy.

### Example HTML structure

```html
<main>
  <header>
    <h1>Build better digital experiences</h1>
    <p>
      A modern platform for building and shipping products.
    </p>
  </header>

  <section>
    <h2>Explore the platform</h2>

    <article>
      <h3>Frontend engineering</h3>
      <p>Build accessible and maintainable interfaces.</p>
    </article>
  </section>
</main>
```

Use CSS to control appearance independently of semantic heading levels.

## 5. Creating a Type Scale

A type scale establishes consistent relationships between font sizes.

Example scale:

| Token | Font size |
|---|---:|
| `text-xs` | 12px |
| `text-sm` | 14px |
| `text-base` | 16px |
| `text-lg` | 18px |
| `text-xl` | 20px |
| `text-2xl` | 24px |
| `text-3xl` | 30px |
| `text-4xl` | 36px |
| `text-5xl` | 48px |
| `text-6xl` | 60px |

This is an example scale. Adapt it to the product's visual direction.

### Modular type scales

A modular scale uses a consistent ratio to derive larger and smaller sizes.

For example:

- Base size: 16px.
- Ratio: 1.25.

The approximate scale becomes:

- 16px
- 20px
- 25px
- 31.25px
- 39px
- 48.8px

A modular scale can help create visual consistency, but designers may adjust individual sizes to improve readability and layout.

## 6. Typography Design Tokens

Define reusable tokens rather than scattering font declarations throughout the project.

Example:

```css
:root {
  --font-display: "Manrope", sans-serif;
  --font-body: "Inter", sans-serif;
  --font-mono: "JetBrains Mono", monospace;

  --font-weight-regular: 400;
  --font-weight-medium: 500;
  --font-weight-semibold: 600;
  --font-weight-bold: 700;

  --font-size-xs: 0.75rem;
  --font-size-sm: 0.875rem;
  --font-size-base: 1rem;
  --font-size-lg: 1.125rem;
  --font-size-xl: 1.25rem;
  --font-size-2xl: 1.5rem;
  --font-size-3xl: 1.875rem;
  --font-size-4xl: 2.25rem;
  --font-size-5xl: 3rem;
  --font-size-6xl: 3.75rem;

  --line-height-tight: 1.1;
  --line-height-heading: 1.2;
  --line-height-body: 1.6;

  --letter-spacing-tight: -0.04em;
  --letter-spacing-normal: 0;
  --letter-spacing-wide: 0.04em;
}
```

Use tokens consistently:

```css
body {
  font-family: var(--font-body);
  font-size: var(--font-size-base);
  line-height: var(--line-height-body);
}

h1,
h2,
h3 {
  font-family: var(--font-display);
  font-weight: var(--font-weight-bold);
}
```

## 7. Font Weight and Emphasis

Font weight changes how text is perceived.

Common weight values:

| Weight | Meaning |
|---|---|
| 300 | Light |
| 400 | Regular |
| 500 | Medium |
| 600 | Semibold |
| 700 | Bold |
| 800 | Extra bold |
| 900 | Black |

Use weights to communicate hierarchy.

Example:

```css
.heading {
  font-weight: 700;
}

.body {
  font-weight: 400;
}

.label {
  font-weight: 600;
}
```

Avoid using too many weights without purpose.

A typical interface can often work with regular, medium, semibold, and bold.

Ensure the selected font actually provides the weights being requested. Browsers may synthesize missing weights.

## 8. Line Height and Readability

Line height determines the vertical spacing between lines of text.

Recommended starting points:

| Text type | Typical line height |
|---|---|
| Large display heading | 1.0–1.15 |
| Page heading | 1.1–1.25 |
| Subheading | 1.2–1.4 |
| Body text | 1.45–1.7 |
| Small supporting text | 1.4–1.6 |

These are starting points, not fixed rules.

Example:

```css
h1 {
  line-height: 1.1;
}

h2 {
  line-height: 1.2;
}

p {
  line-height: 1.65;
}
```

### Common mistakes

- Body text with extremely tight line height.
- Headings with excessive vertical spacing.
- Different line heights for similar components.
- Text blocks that become difficult to scan.

Always evaluate line height in the actual font and content context.

## 9. Letter Spacing

Letter spacing controls the distance between characters.

Common approaches:

- Tight spacing for large display headings.
- Normal spacing for body text.
- Slightly increased spacing for uppercase labels.

Example:

```css
.hero-title {
  letter-spacing: -0.045em;
}

.body-copy {
  letter-spacing: 0;
}

.eyebrow {
  letter-spacing: 0.08em;
  text-transform: uppercase;
}
```

Avoid excessive negative tracking, particularly at small sizes.

Some fonts require different spacing adjustments because of their individual letterforms.

## 10. Responsive Typography

Typography must adapt to different screen sizes.

A heading that looks balanced on a desktop monitor may overflow on a mobile screen.

Use fluid typography where appropriate.

### CSS clamp()

```css
.hero-title {
  font-size: clamp(2.5rem, 6vw, 5.5rem);
  line-height: 1.05;
}
```

The three arguments represent:

1. Minimum size.
2. Preferred fluid size.
3. Maximum size.

Another example:

```css
.section-title {
  font-size: clamp(1.75rem, 3vw, 3rem);
}
```

### Responsive typography tokens

```css
:root {
  --heading-xl: clamp(2.5rem, 6vw, 5.5rem);
  --heading-lg: clamp(2rem, 4vw, 3.5rem);
  --heading-md: clamp(1.5rem, 3vw, 2.5rem);
  --body-lg: clamp(1rem, 1.2vw, 1.25rem);
}
```

Use them in components:

```css
.hero h1 {
  font-size: var(--heading-xl);
}

.section h2 {
  font-size: var(--heading-lg);
}
```

### Responsive considerations

- Avoid horizontal overflow.
- Test heading wrapping.
- Check line lengths.
- Keep buttons readable.
- Adjust heading widths.
- Review navigation labels.
- Consider different font metrics.

Fluid sizing does not eliminate the need for responsive testing.

## 11. Content Width and Readability

Typography depends on more than font size.

Line length has a major effect on reading comfort.

Example:

```css
.prose {
  max-width: 68ch;
}
```

The `ch` unit provides a useful approximate character-based width.

For long-form reading, a narrower content column often improves readability.

For large marketing headlines, wider text containers may be appropriate.

Do not apply one global maximum width to every text element.

### Text wrapping

Modern CSS offers useful text-wrapping controls.

```css
.hero-title {
  text-wrap: balance;
}

.article-heading {
  text-wrap: pretty;
}
```

These properties can improve heading and paragraph wrapping where supported.

Always inspect the actual layout because text wrapping depends on font metrics and available space.

## 12. Loading Web Fonts

Font loading affects visual consistency and page performance.

Fonts can be loaded from:

- Local font files.
- Google Fonts.
- Other hosted font services.
- Self-hosted font infrastructure.

### Google Fonts

Example:

```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>

<link
  href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap"
  rel="stylesheet"
>
```

Only request the weights and styles the project needs.

### Self-hosted fonts

```css
@font-face {
  font-family: "Inter";
  src: url("/fonts/inter-variable.woff2") format("woff2");
  font-weight: 100 900;
  font-style: normal;
  font-display: swap;
}
```

Use the actual weight range provided by the font file.

### Font loading best practices

- Prefer modern WOFF2 files.
- Avoid unnecessary font families.
- Load only required weights.
- Consider font subsets.
- Use appropriate fallback fonts.
- Preload only critical fonts.
- Avoid excessive font requests.
- Check font licensing.

A font should not delay access to essential page content.

## 13. Variable Fonts

Variable fonts contain multiple design variations within a single font file.

They can support variable:

- Weight.
- Width.
- Slant.
- Optical size.
- Other registered or custom axes.

Example:

```css
@font-face {
  font-family: "VariableFont";
  src: url("/fonts/variable-font.woff2") format("woff2");
  font-weight: 100 900;
  font-style: normal;
  font-display: swap;
}
```

Usage:

```css
.heading {
  font-family: "VariableFont", sans-serif;
  font-weight: 750;
}
```

Variable fonts can reduce the number of font files needed, but actual performance depends on file size, subsets, and usage.

### Variable font animation

Some variable fonts support animated weight or width changes.

```css
.animated-heading {
  font-variation-settings: "wght" 400;
  transition: font-variation-settings 250ms ease;
}

.animated-heading:hover {
  font-variation-settings: "wght" 700;
}
```

Use only axes supported by the selected font.

Avoid unnecessary typography animation that harms readability or performance.

## 14. Typography in Forms and Components

Text styles should remain consistent across interface components.

Consider:

### Buttons

```css
.button {
  font-family: var(--font-body);
  font-size: var(--font-size-sm);
  font-weight: var(--font-weight-semibold);
}
```

### Form labels

```css
.form-label {
  font-size: var(--font-size-sm);
  font-weight: var(--font-weight-medium);
}
```

### Helper text

```css
.form-helper {
  font-size: var(--font-size-xs);
  line-height: 1.5;
}
```

### Navigation

```css
.navigation-link {
  font-size: var(--font-size-sm);
  font-weight: var(--font-weight-medium);
}
```

### Code blocks

```css
code,
pre {
  font-family: var(--font-mono);
}
```

Do not make every component use a unique font size.

Establish a shared typographic vocabulary.

## 15. Multilingual and International Typography

Modern applications may support multiple languages and writing systems.

Font selection should consider:

- Latin scripts.
- Assamese.
- Bengali.
- Devanagari.
- Arabic.
- CJK scripts.
- Other required writing systems.

A font that looks excellent in English may not contain the glyphs needed for another language.

### Font fallback

```css
body {
  font-family:
    "Inter",
    "Noto Sans Bengali",
    "Noto Sans",
    sans-serif;
}
```

This is an illustrative fallback stack. Choose fonts that actually cover the languages your product supports.

For Assamese and Bengali content, test:

- Character rendering.
- Conjunct characters.
- Matras and vowel signs.
- Line spacing.
- Font fallback.
- Mixed-script text.
- Text selection and copying.

### Language-specific typography

Different scripts have different typographic characteristics.

Do not assume Latin font sizes and line heights will produce equally readable results in every script.

Test real language content rather than relying exclusively on placeholder English text.

## 16. Accessibility and Typography

Accessible typography makes content easier to understand and use.

Important considerations:

- Maintain sufficient text contrast.
- Allow text resizing.
- Avoid excessively small text.
- Preserve readable line lengths.
- Avoid justified text when it creates uneven word spacing.
- Use semantic HTML.
- Do not communicate meaning through typography alone.
- Preserve content when users increase text size.
- Ensure zoom does not cause clipping.

### Text resizing

Interfaces should remain usable when users enlarge text.

Test browser zoom and text scaling, including layouts with:

- Navigation menus.
- Buttons.
- Cards.
- Tables.
- Forms.
- Dialogs.
- Long headings.

Avoid fixed-height containers that clip enlarged content.

### Contrast

Typography should follow applicable WCAG contrast requirements.

As common WCAG AA guidance:

- Normal text: at least 4.5:1.
- Large text: at least 3:1.

Validate actual foreground and background colors.

## 17. Typography with Tailwind CSS

Tailwind provides utility classes for common typographic properties.

Example:

```jsx
<h1 className="text-5xl font-bold tracking-tight leading-tight">
  Build something exceptional
</h1>

<p className="text-base leading-relaxed text-slate-600">
  Create modern, accessible digital experiences.
</p>
```

Responsive typography:

```jsx
<h1 className="text-4xl md:text-5xl lg:text-7xl font-bold tracking-tight">
  Design for the future
</h1>
```

Use theme tokens when the project has a custom typography system.

Avoid accumulating arbitrary font sizes across components.

Inspect the project's Tailwind version and configuration before modifying typography conventions.

## 18. Typography in Design Systems

A mature design system should document typography as reusable styles.

Example naming structure:

```text
Typography
├── Display
│   ├── Display Large
│   ├── Display Medium
│   └── Display Small
├── Heading
│   ├── Heading 1
│   ├── Heading 2
│   ├── Heading 3
│   └── Heading 4
├── Body
│   ├── Body Large
│   ├── Body Medium
│   └── Body Small
├── Label
│   ├── Label Large
│   └── Label Small
└── Code
    ├── Code Large
    └── Code Small
```

Document the following for each style:

- Font family.
- Font size.
- Font weight.
- Line height.
- Letter spacing.
- Responsive behavior.
- Intended usage.

This makes typography easier to implement consistently in both design tools and frontend code.

## 19. Common Typography Mistakes

### Too many font families

Excessive font combinations make interfaces feel inconsistent.

**Better:** Use a small, intentional font system.

### Inconsistent type sizes

Arbitrary font sizes weaken hierarchy.

**Better:** Define a type scale.

### Poor line height

Text becomes difficult to read when spacing is too tight or too loose.

**Better:** Choose line heights according to text size and content.

### Oversized mobile headings

Large desktop typography can overflow smaller screens.

**Better:** Use fluid sizing and responsive review.

### Missing font weights

Browsers may synthesize unavailable weights.

**Better:** Load the actual weights required.

### Excessive uppercase text

Large amounts of uppercase text can reduce readability.

**Better:** Reserve uppercase for short labels and small interface elements.

### Ignoring international scripts

Fallback fonts can produce inconsistent rendering.

**Better:** Test every supported language.

### Fixed-height text containers

Content can become clipped when text is enlarged.

**Better:** Prefer flexible sizing and content-driven height.

## 20. AI Coding Agent Workflow

AI coding agents should follow a structured process when building typography systems.

### Before implementation

1. Inspect the frontend framework.
2. Identify the existing font families.
3. Inspect existing design tokens.
4. Understand the brand direction.
5. Identify supported languages.
6. Review responsive requirements.
7. Check font licensing and availability.

### During implementation

1. Select appropriate font families.
2. Define font-family tokens.
3. Establish a type scale.
4. Define font weights.
5. Set line-height conventions.
6. Define letter-spacing tokens.
7. Implement responsive sizes.
8. Configure web font loading.
9. Update component styles.
10. Preserve semantic HTML.

### During visual review

- Inspect heading hierarchy.
- Check paragraph readability.
- Review line wrapping.
- Test mobile typography.
- Inspect font loading.
- Check multilingual rendering.
- Verify text contrast.
- Review button and form labels.

### Before completion

- Confirm there are no unnecessary font requests.
- Verify all requested weights are available.
- Check fallback behavior.
- Test browser zoom.
- Check responsive layouts.
- Confirm the production build succeeds.

Do not replace an established product typography system without understanding the existing design direction.

## 21. Recommended File Organization

A frontend project may organize typography tokens like this:

```text
src/
├── styles/
│   ├── tokens/
│   │   ├── colors.css
│   │   ├── typography.css
│   │   └── spacing.css
│   ├── fonts/
│   │   └── fonts.css
│   ├── globals.css
│   └── utilities.css
├── components/
└── app/
```

For smaller applications, typography tokens and font definitions can live in a shared stylesheet.

Choose an architecture that fits the project.

## 22. Production Checklist

### Font selection

- [ ] Font families match the brand direction.
- [ ] Font pairing is intentional.
- [ ] Required font weights are available.
- [ ] Font licensing is checked.
- [ ] Language coverage is verified.

### Typography system

- [ ] Heading hierarchy is defined.
- [ ] Type scale is documented.
- [ ] Font weights are standardized.
- [ ] Line heights are consistent.
- [ ] Letter spacing is intentional.
- [ ] Responsive typography is implemented.

### Performance

- [ ] Fonts use efficient formats.
- [ ] Unnecessary weights are excluded.
- [ ] Font loading is optimized.
- [ ] Fallback fonts are configured.
- [ ] Critical fonts are prioritized appropriately.

### Accessibility

- [ ] Text contrast is sufficient.
- [ ] Text resizing works.
- [ ] Content is not clipped.
- [ ] Semantic headings are used.
- [ ] Multilingual content is readable.

### Quality

- [ ] Desktop typography is reviewed.
- [ ] Mobile typography is reviewed.
- [ ] Paragraph width is appropriate.
- [ ] Form and button typography is consistent.
- [ ] Production build succeeds.

## 23. Further Learning

Official and useful resources:

- [MDN CSS Fonts](https://developer.mozilla.org/en-US/docs/Web/CSS/Guides/Fonts)
- [MDN CSS Text](https://developer.mozilla.org/en-US/docs/Web/CSS/Guides/Text)
- [Google Fonts](https://fonts.google.com/)
- [Variable Fonts Guide](https://web.dev/articles/variable-fonts)
- [W3C WCAG 2.2](https://www.w3.org/TR/WCAG22/)
- [Tailwind CSS Typography](https://tailwindcss.com/docs/font-family)
- [Fontsource](https://fontsource.org/)
- [The Elements of Typographic Style](https://www.hartleyandmarks.com/)

---

## 24. Design Systems Documentation

This guide establishes the typography foundation for the playbook.

Related guides:

- [Colors](./colors.md)
- [Components](./components.md)

A complete design system combines color, typography, spacing, layout, and reusable components into one consistent visual language.