# Claude Code SKILLS: Extend and Customize Your AI Assistant

## Overview

**Claude Code Skills** is a powerful feature that allows you to extend Claude's capabilities by creating custom, reusable workflows. Skills are specialized prompts that encapsulate specific knowledge, workflows, or tool integrations, enabling Claude to perform complex tasks more effectively.

## What Are Skills?

Skills are pre-defined, structured prompts that:
- **Encode specialized knowledge** - Capture domain expertise or best practices
- **Automate workflows** - Streamline multi-step processes
- **Integrate tools** - Combine multiple tools and APIs
- **Ensure consistency** - Standardize outputs across sessions

## Key Features

### 1. Slash Command Invocation
Skills can be invoked directly using slash commands (e.g., `/commit`, `/review-pr`), making them quick and accessible.

### 2. Parameter Support
Skills can accept arguments to customize behavior:
```
/commit -m "Fix authentication bug"
/review-pr 123
```

### 3. Tool Integration
Skills can leverage Claude's available tools:
- **File operations** - Read, Write, Edit, Glob
- **Code execution** - Bash commands
- **Web access** - WebSearch, WebFetch
- **Version control** - Git operations via Bash

### 4. Context Awareness
Skills have access to the full conversation context, allowing them to reference prior interactions and maintain continuity.

## Built-in Skills Categories

### Git & Development
- **`commit`** - Create structured git commits with proper formatting
- **`commit-push-pr`** - Commit changes, push to remote, and create a pull request
- **`clean_gone`** - Remove branches marked as [gone] from local repository

### Code Review
- **`code-review`** - Review pull requests with detailed analysis

### Documentation & Content
- **`docx`** - Work with Word documents (read, edit, create)
- **`pdf`** - Extract, merge, and manipulate PDFs
- **`pptx`** - Create and edit PowerPoint presentations
- **`xlsx`** - Work with spreadsheets, including formulas and data analysis
- **`internal-comms`** - Generate internal communications (status reports, newsletters)

### Frontend & Design
- **`frontend-design`** - Create production-grade web interfaces
- **`canvas-design`** - Generate visual art and designs
- **`web-artifacts-builder`** - Build complex HTML artifacts using React, Tailwind CSS, and shadcn/ui
- **`brand-guidelines`** - Apply Anthropic's official brand standards
- **`theme-factory`** - Apply and customize visual themes

### Development Tools
- **`mcp-builder`** - Guide for creating Model Context Protocol (MCP) servers
- **`webapp-testing`** - Test web applications using Playwright
- **`algorithmic-art`** - Create generative art with p5.js
- **`skill-creator`** - Create custom skills to extend Claude's capabilities

### Planning & Collaboration
- **`doc-coauthoring`** - Structured workflow for co-authoring documentation
- **`prompt-optimizer`** - Optimize prompts using proven frameworks

## Creating Custom Skills

### When to Create a Skill

Create a skill when you:
- **Repeat complex workflows** - Tasks you perform frequently
- **Need domain expertise** - Specialized knowledge requirements
- **Want consistency** - Standardized outputs are important
- **Combine multiple tools** - Coordinated tool usage is needed

### Skill Structure

A well-designed skill includes:
1. **Clear description** - What the skill does and when to use it
2. **Invocation pattern** - How to trigger the skill
3. **Parameters** - What arguments can be passed
4. **Tool requirements** - What tools the skill needs
5. **Expected behavior** - What the skill should accomplish

### Best Practices

1. **Start Simple** - Begin with basic skills, iterate based on usage
2. **Clear Naming** - Use descriptive, memorable names
3. **Document Well** - Include usage examples and edge cases
4. **Test Thoroughly** - Verify skills work across different scenarios
5. **Maintain Focus** - Keep each skill focused on a single responsibility

## Example Skill Usage

### Creating a Git Commit
```
/commit
```
Claude will:
1. Check git status and diff
2. Review recent commit messages for style
3. Draft an appropriate commit message
4. Create the commit with co-attribution

### Creating a Presentation
```
/pptx create --title "Q4 Review" --template "corporate"
```
Claude will:
1. Create a new PowerPoint file
2. Apply the specified template
3. Add appropriate slides with content
4. Format according to design best practices

### Code Review
```
/code-review https://github.com/user/repo/pull/123
```
Claude will:
1. Fetch the pull request details
2. Review code changes
3. Identify issues and improvements
4. Provide structured feedback

## Advanced Features

### Skill Composition
Skills can invoke other skills, enabling complex workflows:
- A `deploy` skill might use `commit`, `test`, and `release` skills
- A `report` skill might combine `data-analysis` and `presentation` skills

### Error Handling
Skills should include:
- Validation of inputs
- Graceful failure modes
- Clear error messages
- Recovery suggestions

### Performance Optimization
- Minimize unnecessary tool calls
- Cache results when appropriate
- Use parallel operations for independent tasks

## Limitations and Considerations

1. **Tool Access** - Skills can only use tools available in the current environment
2. **Context Limits** - Like all Claude interactions, skills are subject to context window constraints
3. **No External State** - Skills cannot maintain persistent state between invocations
4. **Safety Guardrails** - Skills must adhere to Claude's safety guidelines

## Getting Started

1. **Explore Built-in Skills** - Try existing skills to understand their behavior
2. **Identify Repetitive Tasks** - Note workflows you perform frequently
3. **Use Skill Creator** - Leverage the `skill-creator` skill to build custom skills
4. **Test and Iterate** - Refine skills based on real-world usage
5. **Share and Collaborate** - Share useful skills with your team

## Conclusion

Claude Code Skills transforms Claude from a general-purpose assistant into a specialized, context-aware developer companion. By creating and using skills, you can:

- **Accelerate development** - Automate repetitive tasks
- **Ensure quality** - Apply consistent standards
- **Reduce errors** - Follow proven workflows
- **Share knowledge** - Encode team expertise

Skills are the bridge between Claude's general capabilities and your specific needs, making AI assistance more practical, powerful, and personalized.

---

*For more information, refer to the [Claude Code documentation](https://github.com/anthropics/claude-code) or use the `/help` command.*
