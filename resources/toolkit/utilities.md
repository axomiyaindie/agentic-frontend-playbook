# Developer Utilities

A collection of useful online tools and libraries for performance testing, accessibility, browser compatibility, asset optimization, and everyday development tasks.

## Performance and Diagnostics

### Lighthouse
- **Website:** https://developer.chrome.com/docs/lighthouse/overview/
- **GitHub:** https://github.com/GoogleChrome/lighthouse
- **Purpose:** Website auditing tool for performance, accessibility, and other quality signals.
- **Use cases:** Identifying performance bottlenecks and quality issues.
- **Getting started:** Run it through Chrome DevTools or its supported command-line workflow.

### PageSpeed Insights
- **Website:** https://pagespeed.web.dev/
- **Purpose:** Performance analysis for public web pages.
- **Use cases:** Reviewing Core Web Vitals and performance recommendations.
- **Getting started:** Enter a URL and review available field and lab data.

### WebPageTest
- **Website:** https://www.webpagetest.org/
- **Purpose:** Detailed website performance testing.
- **Use cases:** Network waterfall analysis, loading behavior, and performance comparisons.
- **Getting started:** Enter a URL and choose a test configuration.

### Bundlephobia
- **Website:** https://bundlephobia.com/
- **GitHub:** https://github.com/Bundlephobia/bundlephobia
- **Purpose:** Estimates the bundle size impact of npm packages.
- **Use cases:** Evaluating dependencies before adding them to an application.
- **Getting started:** Search for a package and inspect its reported size and dependencies.

## Accessibility

### W3C WAI Evaluation Tools
- **Website:** https://www.w3.org/WAI/test-evaluate/tools/list/
- **Purpose:** Directory of accessibility evaluation tools.
- **Use cases:** Finding tools for automated and manual accessibility evaluation.

### axe-core
- **Website:** https://www.deque.com/axe/
- **GitHub:** https://github.com/dequelabs/axe-core
- **Purpose:** Accessibility testing engine.
- **Use cases:** Detecting common accessibility problems in web applications.
- **Getting started:** https://github.com/dequelabs/axe-core

### Playwright Accessibility Testing
- **Website:** https://playwright.dev/docs/accessibility-testing
- **GitHub:** https://github.com/microsoft/playwright
- **Purpose:** Accessibility checks within browser testing workflows.
- **Use cases:** Automated accessibility checks during development and CI.
- **Getting started:** Follow the official accessibility testing guide.

Automated tools cannot detect every accessibility issue. Combine them with keyboard testing, screen-reader testing, and manual review.

## Browser Compatibility

### Can I Use
- **Website:** https://caniuse.com/
- **GitHub:** https://github.com/Fyrd/caniuse
- **Purpose:** Browser support reference for web technologies.
- **Use cases:** Checking support for CSS, HTML, JavaScript, and browser APIs.

### MDN Web Docs
- **Website:** https://developer.mozilla.org/
- **GitHub:** https://github.com/mdn
- **Purpose:** Technical documentation for web technologies.
- **Use cases:** Learning and referencing HTML, CSS, JavaScript, and browser APIs.
- **Getting started:** https://developer.mozilla.org/en-US/docs/Learn_web_development

## Image and SVG Optimization

### Squoosh
- **Website:** https://squoosh.app/
- **GitHub:** https://github.com/GoogleChromeLabs/squoosh
- **Purpose:** Browser-based image compression and format comparison.
- **Use cases:** Optimizing images for web performance.

### SVGO
- **Website:** https://svgo.dev/
- **GitHub:** https://github.com/svg/svgo
- **Purpose:** SVG optimization tool.
- **Use cases:** Reducing SVG file size and removing unnecessary markup.
- **Getting started:** https://svgo.dev/docs/usage/

### SVGOMG
- **Website:** https://jakearchibald.github.io/svgomg/
- **GitHub:** https://github.com/jakearchibald/svgomg
- **Purpose:** Browser interface for SVG optimization.
- **Use cases:** Previewing and optimizing SVG assets.

## General Developer Utilities

### JSON Crack
- **Website:** https://jsoncrack.com/
- **GitHub:** https://github.com/AykutSarac/jsoncrack
- **Purpose:** Visualizes JSON structures.
- **Use cases:** Understanding nested JSON and API response structures.

### Regex101
- **Website:** https://regex101.com/
- **Purpose:** Online regular expression editor and tester.
- **Use cases:** Creating, debugging, and explaining regular expressions.

### HTTP Status Codes
- **Website:** https://httpstatuses.com/
- **Purpose:** Reference for HTTP response status codes.
- **Use cases:** Understanding API and server response codes.

## Safe Usage

- Do not paste secrets or private production data into public tools.
- Treat performance scores as diagnostic indicators rather than absolute measures.
- Test on representative devices and network conditions.
- Combine automated accessibility checks with manual evaluation.
- Re-test after major changes to scripts, fonts, images, and rendering behavior.