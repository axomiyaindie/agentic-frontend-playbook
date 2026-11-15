# Frontend Architecture

Frontend architecture defines how an application is structured, how its components communicate, how data flows, and how the codebase evolves over time.

A good architecture makes applications easier to build, test, understand, scale, and maintain.

This guide establishes practical architectural principles for modern frontend applications.

## 1. Architecture Principles

Follow these principles when designing frontend applications:

- **Separation of concerns:** Keep UI, business logic, data access, and infrastructure responsibilities understandable.
- **Component composition:** Build interfaces from focused, reusable components.
- **Predictability:** Prefer explicit data flow and clear state ownership.
- **Maintainability:** Organize code around understandable responsibilities.
- **Scalability:** Allow the project to grow without unnecessary complexity.
- **Performance:** Avoid unnecessary rendering, network requests, and large bundles.
- **Accessibility:** Treat accessible interactions as an architectural requirement.

Choose architecture based on actual product requirements rather than trends.

## 2. Understand the Existing Project First

Before modifying an existing application:

1. Inspect its directory structure.
2. Identify its framework and build tools.
3. Read package configuration and existing scripts.
4. Understand routing and navigation.
5. Identify shared components and design tokens.
6. Inspect state management and data-fetching patterns.
7. Review existing testing conventions.
8. Follow established project conventions unless there is a clear reason to change them.

AI coding agents should avoid replacing an existing architecture without understanding its purpose.

## 3. Component Architecture

Components should have clear responsibilities.

A practical hierarchy includes:

### Application components

Responsible for application initialization, routing, global providers, and high-level configuration.

### Page components

Represent routes or major application views.

### Feature components

Implement product-specific functionality, such as dashboards, authentication forms, or product configurators.

### Shared UI components

Provide reusable interface elements such as buttons, dialogs, inputs, cards, and navigation elements.

### Layout components

Define shared page structures, containers, sidebars, and application shells.

Prefer composition over deeply nested components with many unrelated responsibilities.

## 4. Project Organization

Organize files according to application size and complexity.

A possible feature-oriented structure:

```text
src/
├── app/
│   ├── routes/
│   ├── providers/
│   └── layouts/
├── features/
│   ├── authentication/
│   ├── dashboard/
│   └── settings/
├── components/
│   ├── ui/
│   └── shared/
├── hooks/
├── lib/
├── services