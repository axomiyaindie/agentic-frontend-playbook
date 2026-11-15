# Contributing to Agentic Frontend & 3D Web Playbook

Thank you for your interest in contributing!

Agentic Frontend & 3D Web Playbook is a community-driven engineering resource for developers and AI coding agents building modern frontend applications, immersive 3D websites, and interactive digital experiences.

We welcome contributions from developers, designers, technical writers, researchers, and AI tooling enthusiasts.

## Table of Contents

- [Ways to Contribute](#ways-to-contribute)
- [Getting Started](#getting-started)
- [Repository Structure](#repository-structure)
- [Documentation Guidelines](#documentation-guidelines)
- [AI Agent Skill Guidelines](#ai-agent-skill-guidelines)
- [Code and Example Guidelines](#code-and-example-guidelines)
- [Quality Standards](#quality-standards)
- [Pull Request Process](#pull-request-process)
- [Issues and Suggestions](#issues-and-suggestions)
- [Licensing and Attribution](#licensing-and-attribution)

## Ways to Contribute

You can contribute by:

- Improving existing engineering documentation.
- Adding tutorials and implementation guides.
- Creating or refining AI agent skills.
- Contributing frontend and 3D web examples.
- Documenting useful libraries, tools, and workflows.
- Improving accessibility, responsiveness, and performance guidance.
- Reporting outdated instructions, broken links, or technical inaccuracies.
- Suggesting new topics and improvements.

Contributions should provide practical value to developers and AI coding agents.

## Getting Started

### 1. Fork the repository

Fork the repository on GitHub:

https://github.com/axomiyaindie/agentic-frontend-playbook

### 2. Clone your fork

```bash
git clone https://github.com/YOUR_USERNAME/agentic-frontend-playbook.git
cd agentic-frontend-playbook
```

### 3. Create a branch

Use a descriptive branch name:

```bash
git checkout -b docs/improve-responsive-design
```

Other examples:

```text
feat/add-3d-product-example
docs/update-threejs-guide
fix/correct-skill-instructions
```

### 4. Make your changes

Keep contributions focused, organized, and consistent with the existing repository structure.

### 5. Review your changes

Before submitting:

```bash
git diff --check
git status
```

For code examples, run the relevant build, tests, or validation commands where applicable.

### 6. Commit your changes

Use clear commit messages:

```bash
git add .
git commit -m "docs: improve responsive design guide"
```

### 7. Push and open a pull request

```bash
git push origin docs/improve-responsive-design
```

Open a pull request against the repository's `main` branch.

## Repository Structure

Contributions should follow the existing organization:

```text
agentic-frontend-playbook/
├── fundamentals/
├── 3d-web/
├── animation/
├── design-systems/
├── agent-workflows/
├── skills/
│   ├── 3d-scene-builder/
│   ├── premium-landing-page/
│   └── frontend-visual-audit/
├── examples/
├── resources/
├── AGENTS.md
├── CONTRIBUTING.md
└── README.md
```

Place new material in the most relevant directory. If a contribution introduces a new category, explain why a separate directory is necessary.

## Documentation Guidelines

Documentation should be:

- Clear, accurate, and practical.
- Organized with descriptive headings.
- Written in accessible English.
- Useful to both humans and AI coding agents.
- Supported by relevant examples where appropriate.
- Maintained when referenced technologies or APIs change.

### Recommended documentation structure

```markdown
# Topic Name

## Overview

Explain the topic and why it matters.

## Core Concepts

Introduce the important concepts.

## Implementation

Provide practical implementation guidance.

## Best Practices

Explain recommended approaches.

## Common Mistakes

Document pitfalls and how to avoid them.

## References

Link to official documentation and useful resources.
```

Avoid unnecessary repetition, vague recommendations, and unsupported technical claims.

## AI Agent Skill Guidelines

AI agent skills are a core part of this project.

Every skill must have its own directory containing a `SKILL.md` file.

Recommended structure:

```text
skills/
└── example-skill/
    ├── SKILL.md
    ├── references/
    ├── examples/
    └── scripts/
```

### SKILL.md requirements

Each skill must:

1. Begin with valid YAML frontmatter.
2. Include a `name` matching its directory name.
3. Include a meaningful `description` explaining what the skill does and when to use it.
4. Provide clear, actionable instructions.
5. Define relevant workflows and quality expectations.
6. Avoid unnecessary duplication with other skills.

Example:

```yaml
---
name: example-skill
description: Explain what this skill does and when an AI agent should use it.
---
```

### Skill design principles

- Write instructions that an AI coding agent can execute.
- Prefer specific steps over vague advice.
- Include relevant implementation and validation guidance.
- Explain important constraints and common failure cases.
- Use references and examples for detailed supporting material.
- Keep the main skill file focused and reasonably concise.
- Never claim that a skill supports a tool or framework unless its instructions actually cover it.

Follow the official Agent Skills specification:

https://agentskills.io/specification

## Code and Example Guidelines

Code contributions should demonstrate reliable engineering practices.

### Frontend examples

- Use semantic HTML.
- Prefer reusable components.
- Support responsive layouts.
- Include accessible interactions.
- Keep components maintainable.
- Avoid unnecessary dependencies.

### 3D web examples

- Use appropriate Three.js, React Three Fiber, or related tooling.
- Consider GPU performance and mobile limitations.
- Manage geometries, materials, textures, and other resources responsibly.
- Provide loading and fallback experiences where appropriate.
- Consider reduced-motion preferences and accessibility.
- Avoid unnecessarily complex scenes.

### Dependencies

- Avoid introducing dependencies without a clear reason.
- Prefer established and actively maintained libraries.
- Document important setup requirements.
- Never commit secrets, API keys, or private credentials.

## Quality Standards

Before submitting a contribution, check the following:

- [ ] Content is relevant to the repository.
- [ ] Technical information is accurate.
- [ ] Markdown formatting is consistent.
- [ ] Links point to relevant resources.
- [ ] Code examples have been checked where applicable.
- [ ] No secrets or private credentials are included.
- [ ] New skills have valid frontmatter and follow the skill guidelines.
- [ ] Existing documentation and functionality have not been unintentionally broken.

Not every documentation contribution requires a build or automated test. Use checks appropriate to the change.

## Pull Request Process

A good pull request should:

1. Have a clear, descriptive title.
2. Explain the problem or opportunity.
3. Describe the changes made.
4. Identify relevant files or sections.
5. Include screenshots or demonstrations for visual changes when useful.
6. Mention any testing or validation performed.

Keep pull requests focused. Large contributions should be discussed through an issue before implementation.

Maintainers may request revisions to improve clarity, correctness, consistency, or maintainability.

## Issues and Suggestions

Before opening an issue, check whether a similar discussion already exists.

When reporting a problem, include:

- A clear description.
- Relevant file paths or documentation sections.
- Steps to reproduce, if applicable.
- Expected and actual behavior.
- Relevant screenshots, code snippets, or references.

For feature suggestions, explain the intended use case and how the proposed contribution would benefit the project.

## Licensing and Attribution

The repository's license has not yet been selected.

Until a license is added, do not assume that repository content is available for unrestricted reuse, redistribution, or modification.

When contributing:

- Submit original work or material you have permission to contribute.
- Credit external sources where appropriate.
- Respect third-party licenses and attribution requirements.
- Do not copy proprietary documentation, code, designs, or assets without permission.

A repository-wide license and any additional contribution terms will be documented separately once finalized.

## Community Principles

We aim to build a technically useful, welcoming, and collaborative resource.

Please:

- Be respectful and constructive.
- Welcome different experience levels.
- Focus feedback on the work, not the contributor.
- Explain technical disagreements with evidence.
- Prefer practical improvements over unnecessary complexity.

Thank you for helping make frontend and 3D web engineering more accessible to developers and AI coding agents.

**Maintained by [AxomiyaIndie](https://github.com/axomiyaindie).**