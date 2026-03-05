# How to Use Skills in Claude Code

Skills are reusable, specialized workflows that extend Claude's capabilities beyond its defaults. This guide walks you through finding, invoking, and creating skills.

---

## 1. What Is a Skill?

A **skill** is a structured prompt (stored as a Markdown file) that encodes a specific workflow, tool integration, or area of domain expertise. Skills are invoked via slash commands and can accept arguments to customize their behavior.

For a full reference of available built-in skills and their categories, see [claude-code-skills.md](./claude-code-skills.md).

---

## 2. Invoking a Skill

Skills are triggered with a leading `/` followed by the skill name:

```
/skill-name
```

### With Arguments

Many skills accept optional or required arguments:

```
/commit -m "Fix null pointer exception in auth module"
/review-pr 42
/pptx create --title "Q3 Planning" --template "corporate"
```

### Quick Reference

| Command | What it does |
|---|---|
| `/commit` | Stage and commit changes with a structured message |
| `/commit-push-pr` | Commit, push, and open a pull request |
| `/code-review <PR URL>` | Fetch and review a pull request |
| `/pptx` | Create or edit a PowerPoint presentation |
| `/pdf` | Extract, merge, or manipulate PDFs |
| `/frontend-design` | Build a production-grade web interface |
| `/skill-creator` | Scaffold a new custom skill |

---

## 3. Creating a Custom Skill

Use the built-in `/skill-creator` skill to scaffold new skills, or create one manually by following the structure below.

### Skill File Structure

Save your skill as a `.md` file (e.g., `my-skill.md`) in your skills directory. A well-formed skill file contains:

```markdown
# Skill Name

## Description
What the skill does and when to use it.

## Invocation
/my-skill [options]

## Parameters
- `--option` — Description of the option

## Steps
1. Step one
2. Step two
3. Step three
```

### Example: A Custom Deploy Skill

```markdown
# deploy

## Description
Runs tests, commits changes, and pushes to the remote branch.

## Invocation
/deploy [--branch <name>]

## Parameters
- `--branch` — Target branch (default: current branch)

## Steps
1. Run the project test suite and report failures.
2. If tests pass, commit all staged changes.
3. Push to the specified branch.
4. Print a summary of the deployment.
```

---

## 4. Best Practices

1. **One responsibility per skill** — Keep each skill focused on a single, well-defined task.
2. **Descriptive names** — Choose names that clearly signal what the skill does (e.g., `deploy`, `changelog`, `lint-fix`).
3. **Document parameters** — List every accepted argument with a short description.
4. **Handle edge cases** — Include validation steps and describe what the skill does when inputs are missing or invalid.
5. **Test before sharing** — Run the skill across different scenarios before distributing it to teammates.

---

## 5. Example Walkthrough

### Creating a Git Commit

```
/commit
```

Claude will:
1. Run `git status` and `git diff` to inspect staged and unstaged changes.
2. Review recent commit messages to match the project's commit style.
3. Draft an appropriate commit message.
4. Create the commit with proper attribution.

### Reviewing a Pull Request

```
/code-review https://github.com/your-org/your-repo/pull/7
```

Claude will:
1. Fetch the pull request diff and metadata.
2. Analyze the changes for bugs, style issues, and improvements.
3. Return structured feedback organized by file and severity.

---

## 6. Further Reading

- [claude-code-skills.md](./claude-code-skills.md) — Full catalogue of built-in skills and advanced features
- [Claude Code documentation](https://github.com/anthropics/claude-code) — Official reference
- Use `/help` inside Claude Code to list all available skills in your current environment
