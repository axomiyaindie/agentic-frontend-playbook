# AI-Assisted Development Tools

A curated collection of AI coding agents, developer assistants, agent frameworks, and protocols for AI-assisted software development.

These tools can help developers explore codebases, generate implementations, debug problems, automate workflows, and build AI-powered applications.

## AI Coding Agents and Editors

### OpenAI Codex
- **Website:** https://openai.com/codex/
- **Documentation:** https://developers.openai.com/codex/
- **GitHub:** https://github.com/openai/codex
- **Purpose:** Coding agent for delegating software engineering tasks.
- **Use cases:** Codebase exploration, implementation, debugging, refactoring, and testing.
- **Getting started:** Follow the official documentation for available Codex experiences and setup.

### Claude Code
- **Website:** https://claude.com/product/claude-code
- **Documentation:** https://docs.claude.com/en/docs/claude-code/overview
- **Purpose:** Agentic coding assistant for terminal-based development workflows.
- **Use cases:** Repository analysis, multi-file changes, debugging, and code review.
- **Getting started:** Follow the official installation and authentication instructions.

### Cursor
- **Website:** https://cursor.com/
- **Documentation:** https://docs.cursor.com/
- **Purpose:** AI-powered code editor.
- **Use cases:** Code generation, codebase understanding, and agent-assisted implementation.
- **Getting started:** Install Cursor and follow its official onboarding guide.

### GitHub Copilot
- **Website:** https://github.com/features/copilot
- **Documentation:** https://docs.github.com/en/copilot
- **Purpose:** AI coding assistance integrated into supported development environments and GitHub workflows.
- **Use cases:** Code completion, explanations, testing, and agent-assisted development.
- **Getting started:** https://docs.github.com/en/copilot/getting-started

### Gemini CLI
- **Website:** https://github.com/google-gemini/gemini-cli
- **GitHub:** https://github.com/google-gemini/gemini-cli
- **Purpose:** Open-source terminal-based AI assistant.
- **Use cases:** Repository exploration, development assistance, and command-line workflows.
- **Getting started:** Follow the official repository installation instructions.

### OpenCode
- **Website:** https://opencode.ai/
- **GitHub:** https://github.com/anomalyco/opencode
- **Purpose:** Open-source AI coding agent interface supporting multiple model providers.
- **Use cases:** Terminal-based coding assistance and agent workflows.
- **Getting started:** https://opencode.ai/docs/

### Cline
- **Website:** https://cline.bot/
- **GitHub:** https://github.com/cline/cline
- **Purpose:** AI coding agent available as an editor extension.
- **Use cases:** Multi-step coding tasks and user-reviewed tool execution.
- **Getting started:** Follow the official extension installation and provider setup instructions.

### Aider
- **Website:** https://aider.chat/
- **GitHub:** https://github.com/Aider-AI/aider
- **Purpose:** AI pair programming tool designed for terminal workflows and Git repositories.
- **Use cases:** Editing existing projects, refactoring, and code generation.
- **Getting started:** https://aider.chat/docs/

### Continue
- **Website:** https://www.continue.dev/
- **GitHub:** https://github.com/continuedev/continue
- **Purpose:** Configurable AI coding assistance and agent workflows.
- **Use cases:** Code assistance, custom model configurations, and development integrations.
- **Getting started:** https://docs.continue.dev/

## Agent Frameworks and Protocols

### Model Context Protocol (MCP)
- **Website:** https://modelcontextprotocol.io/
- **GitHub:** https://github.com/modelcontextprotocol
- **Purpose:** Open protocol for connecting AI applications with tools and external data sources.
- **Use cases:** Connecting agents to APIs, databases, developer tools, and external services.
- **Getting started:** https://modelcontextprotocol.io/docs/getting-started/intro

### Agent Skills
- **Website:** https://agentskills.io/
- **GitHub:** https://github.com/agentskills/agentskills
- **Purpose:** A format for packaging reusable instructions and resources for compatible AI agents.
- **Use cases:** Reusable coding workflows, specialized agent capabilities, and project-specific instructions.
- **Getting started:** Read the specification and examples on the official website.

### LangGraph
- **Website:** https://www.langchain.com/langgraph
- **GitHub:** https://github.com/langchain-ai/langgraph
- **Purpose:** Framework for building stateful, multi-step agent workflows.
- **Use cases:** Tool-using agents, complex workflows, and human-in-the-loop systems.
- **Getting started:** https://docs.langchain.com/oss/python/langgraph/overview

### Vercel AI SDK
- **Website:** https://ai-sdk.dev/
- **GitHub:** https://github.com/vercel/ai
- **Purpose:** Toolkit for building AI-powered applications with TypeScript.
- **Use cases:** Streaming interfaces, chat applications, and model integrations.
- **Getting started:** https://ai-sdk.dev/docs/getting-started

## Responsible AI Development

- Review generated code before accepting it.
- Inspect terminal commands before execution.
- Keep API keys and secrets out of prompts and repositories.
- Check generated dependencies and licenses.
- Run tests, type checks, and security checks.
- Review agent permissions before granting filesystem, browser, or shell access.
- Verify provider privacy and data-retention policies before using sensitive project data.