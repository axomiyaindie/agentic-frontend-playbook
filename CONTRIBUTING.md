# Contributing to Agentic Frontend & 3D Web Playbook

Thank you for your interest in contributing to **Agentic Frontend & 3D Web Playbook**.

This project aims to make modern frontend engineering, 3D web development, animation, and AI-assisted development more accessible through practical documentation, reusable AI agent skills, and implementation examples.

Contributions of all kinds are welcome, including documentation improvements, new skills, practical examples, code samples, corrections, and resource recommendations.

## Ways to Contribute

You can contribute by:

- Improving existing documentation for clarity, accuracy, and usefulness.
- Adding guides covering frontend engineering, 3D web development, animation, or design systems.
- Creating or improving reusable AI agent skills.
- Adding practical project blueprints and implementation examples.
- Sharing useful libraries, tools, and learning resources.
- Fixing technical errors, broken links, and outdated recommendations.
- Improving accessibility, performance, responsive design, and developer workflows.

Contributions should provide practical value to developers and AI coding agents.

## Getting Started

### 1. Fork the repository

Fork the repository to your GitHub account:

https://github.com/axomiyaindie/agentic-frontend-playbook

### 2. Clone your fork

Replace `YOUR_USERNAME` with your GitHub username.

```bash
git clone https://github.com/YOUR_USERNAME/agentic-frontend-playbook.git
cd agentic-frontend-playbook
```

### 3. Create a branch

Create a separate branch for your contribution.

```bash
git checkout -b docs/add-new-guide
```

Use a descriptive branch name, such as:

- `docs/improve-responsive-design`
- `skills/add-animation-review`
- `examples/add-portfolio-blueprint`
- `fix/update-threejs-guide`

### 4. Make your changes

Follow the documentation, skill, and example guidelines below.

Keep contributions focused, technically accurate, and easy for others to understand.

### 5. Review your changes

Before submitting, check that:

- Markdown formatting is correct.
- Links point to valid resources.
- Code examples are readable and technically sound.
- New files follow the existing naming conventions.
- Your changes do not introduce unrelated modifications.

You can review your changes with:

```bash
git status
git diff
```

### 6. Commit and push

Use a clear commit message describing your changes.

```bash
git add .
git commit -m "docs: add frontend performance guide"
git push origin docs/add-new-guide
```

### 7. Open a Pull Request

Open a pull request against the repository's `main` branch.

Include:

- A clear title.
- A short explanation of what you changed.
- The reason for the contribution.
- Relevant links or references, if applicable.

The maintainers will review your contribution and may request changes before merging.

## Documentation Guidelines

Documentation should be practical, structured, and useful to developers working on real projects.

### Writing standards

- Use clear and direct language.
- Prefer practical explanations over unnecessary theory.
- Break complex topics into meaningful sections.
- Include examples when they improve understanding.
- Use Markdown headings consistently.
- Keep technical recommendations accurate and current.
- Link to official documentation when appropriate.
- Avoid unsupported claims and unexplained jargon.

### Recommended document structure

Adapt this structure to the topic rather than following it rigidly.

```markdown
# Topic Name

## Overview

Explain the topic and why it matters.

## Core Concepts

Describe the important concepts.

## Practical Guidelines

Provide recommendations and implementation guidance.

## Examples

Include useful code or practical scenarios.

## Best Practices

Summarize important considerations.

## Resources

Link to relevant documentation and references.
```

Not every document needs every section. Prioritize usefulness and readability.

## AI Agent Skill Guidelines

AI agent skills are an important part of this repository.

A skill should give an AI coding agent clear, reusable instructions for completing a specific development task.

### Skill requirements

Every skill must have its own directory containing a `SKILL.md` file.

Example:

```text
skills/
└── skill-name/
    ├── SKILL.md
    ├── references/
    ├── examples/
    └── scripts/
```

Only include additional directories when they provide genuine value.

### Skill writing standards

A good skill should:

- Have a clearly defined purpose.
- Explain when the skill should and should not be used.
- Provide actionable instructions.
- Define a logical workflow.
- Include relevant technical constraints.
- Encourage maintainable and accessible implementations.
- Include validation or review steps where appropriate.
- Avoid vague instructions and unnecessary repetition.

### Frontmatter example

Use valid YAML frontmatter at the beginning of `SKILL.md`.

```yaml
---
name: skill-name
description: Explains what the skill does and when an AI agent should use it.
---
```

Keep the skill focused on a specific task. Avoid creating multiple skills that substantially duplicate one another.

## Code and Example Guidelines

Code examples and project blueprints should demonstrate realistic implementation practices.

When contributing code:

- Use appropriate TypeScript types where applicable.
- Follow established framework conventions.
- Prefer reusable and maintainable components.
- Consider responsive behavior and accessibility.
- Avoid unnecessary dependencies.
- Include installation or setup instructions when required.
- Explain important implementation decisions.
- Do not include API keys, credentials, or other secrets.

For 3D web examples, consider:

- Scene structure and component organization.
- Rendering performance.
- Asset loading and optimization.
- Responsive canvas behavior.
- Mobile device limitations.
- Accessibility and graceful fallbacks.

Examples should help developers understand how to approach and build real experiences, not merely demonstrate isolated effects.

## Repository Organization

Place contributions in the appropriate existing area.

```text
assets/
fundamentals/
3d-web/
animation/
design-systems/
agent-workflows/
skills/
examples/
resources/
```

Use the existing naming conventions and avoid introducing unnecessary top-level directories.

If a contribution does not fit the current organization, explain the proposed placement in your pull request.

## Quality Standards

Every contribution should aim to meet these standards:

**Accuracy:** Technical information should be correct and supported by reliable references where appropriate.

**Clarity:** Content should be understandable to its intended audience.

**Practicality:** Recommendations should help developers solve real implementation problems.

**Maintainability:** Documentation, examples, and skills should be easy to update.

**Accessibility:** Frontend guidance should consider accessibility as a fundamental requirement.

**Performance:** Recommendations should account for runtime performance, loading behavior, and resource usage.

**Compatibility:** Examples should identify relevant framework or library assumptions when necessary.

## Pull Request Guidelines

Before submitting a pull request:

- Check whether a similar guide, skill, or example already exists.
- Keep each pull request focused on a logical set of changes.
- Explain the problem your contribution addresses.
- Mention any relevant dependencies or compatibility requirements.
- Include screenshots or demonstrations when they help reviewers understand visual changes.
- Respond constructively to review feedback.

Large contributions and new sections are welcome, but discussing the proposed direction in an issue first can help avoid duplicated work.

## Issues and Suggestions

Use GitHub Issues to:

- Report incorrect or outdated documentation.
- Suggest new topics or skills.
- Propose improvements to existing workflows.
- Report broken examples or links.
- Discuss potential architectural or organizational changes.

Provide enough context for others to understand the problem or proposal.

## License and Attribution

This repository is licensed under the **MIT License**.

By submitting a contribution, you agree that your contribution will be distributed under the repository's MIT License.

When contributing material created by someone else:

- Ensure you have permission to redistribute it.
- Preserve required copyright and license notices.
- Provide attribution where required.
- Include source links for external references.
- Do not submit copyrighted material without appropriate permission.

See the [`LICENSE`](LICENSE) file for the complete license terms.

## Community Principles

We aim to maintain a welcoming, collaborative, and constructive environment.

Contributors are expected to:

- Communicate respectfully.
- Provide constructive feedback.
- Welcome different technical perspectives.
- Focus discussions on ideas and implementation quality.
- Help maintain accurate and useful project resources.

Thank you for helping make frontend engineering and 3D web development more accessible to developers and AI coding agents.