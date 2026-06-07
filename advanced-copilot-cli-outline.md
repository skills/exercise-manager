---
name: GitHub Skills Exercise
about: Template for creating a new GitHub Skills exercise
title: 'Advanced Copilot CLI: Use Advanced Features with Slash Commands'
labels: 'skills'
assignees: ''

---

# Logistics

- **Exercise Title:** Advanced Copilot CLI
- **Repo URL:** https://github.com/skills/advanced-copilot-cli
- **Experience Level**: Intermediate
- **Recommended Grouping**: GitHub Copilot

### Relationships to other exercises

- **Previous Exercise:** Introduction to GitHub Copilot CLI or Copilot CLI for beginners
- **Next Exercise:** Advanced automation with Copilot agents, skills, and MCP servers

---

# Outline

## Story Plot

You are a developer improving a small project from the terminal. Across the exercise, you will use advanced GitHub Copilot CLI slash commands and extensibility features to review code, plan work, apply team standards, connect external context, and complete a realistic feature workflow.

## README

**Title:** Advanced Copilot CLI

Learn how to get more from GitHub Copilot CLI by combining advanced slash commands, agents, custom instructions, agent skills, and MCP servers. This exercise teaches a practical workflow for using Copilot CLI efficiently and effectively from planning through review.

### Overview

1. Use Copilot CLI development workflows for review, refactoring, debugging, tests, and Git collaboration.
1. Configure agents and custom instructions to guide Copilot toward specialized outcomes.
1. Create and invoke agent skills for repeatable task-specific guidance.
1. Configure MCP servers to bring external context into Copilot CLI sessions.
1. Combine slash commands, agents, skills, and MCP in an end-to-end development workflow.

### What you will build

You will configure a repository with Copilot CLI customization files and use them to complete an advanced terminal-driven development workflow. By the end, the repository will include custom instructions, an agent, a skill, MCP configuration, and a workflow summary that demonstrates how to use slash commands effectively.

### Prerequisites

- Basic familiarity with GitHub repositories, commits, pull requests, and GitHub Actions.
- Basic experience using GitHub Copilot CLI in a terminal.
- Ability to edit files in a Codespace or local development environment.

### On Start

- Create a small sample application with a few intentionally incomplete files for review, refactoring, testing, and debugging activities.
- Add starter folders for `.github/agents/`, `.github/skills/`, and `.github/workflows/`.
- Add a starter `COPILOT_CLI_WORKFLOW.md` file where learners will record workflow decisions as each step is completed.

## Step 1 - Apply Development Workflows

### Story

Your team wants to use Copilot CLI as a daily development assistant, not just a chat tool. You will practice the core workflows that make Copilot CLI useful during regular coding work.

### Theory

GitHub Copilot CLI supports interactive terminal workflows where learners can reference files with `@`, ask for implementation plans, request focused reviews, and iterate in a multi-turn session. Advanced CLI usage starts with choosing the right workflow for the task: review before merging, refactor safely, debug from symptoms, generate tests, and summarize Git changes.

- File and directory references give Copilot concrete context for code review, debugging, and refactoring.
- Slash commands such as `/plan` and `/review` invoke specialized behaviors instead of relying only on free-form prompts.
- Strong workflows gather context first, then plan, then implement, then test, then review.

### References

- https://docs.github.com/copilot/how-tos/use-copilot-agents/use-copilot-cli
- https://docs.github.com/en/copilot/concepts/agents/about-copilot-cli

### Activity: Document a Development Workflow

1. Start Copilot CLI in the exercise repository.
1. Use file or directory context with `@` to ask Copilot to review the starter application.
1. Use `/plan` to outline a safe improvement to the starter application.
1. Use `/review` to inspect the planned or completed changes.
1. Update `COPILOT_CLI_WORKFLOW.md` with the slash commands and workflow sequence used.

### Transition

- **Actions Trigger:** [`push`](https://docs.github.com/en/actions/reference/events-that-trigger-workflows#push)
- **Grading-Check:** Verify `COPILOT_CLI_WORKFLOW.md` exists and includes `/plan`, `/review`, and a description of using `@` context.

## Step 2 - Configure Agents and Custom Instructions

### Story

Your team wants Copilot CLI responses to match project expectations without repeating the same standards in every prompt. You will add repository-level guidance and a specialized agent for focused work.

### Theory

Agents give Copilot a specialized role for a class of work, while custom instructions provide durable project context and standards. In Copilot CLI, learners can use built-in agents, switch agents with `/agent`, or define repository agents as `.agent.md` files. Repository custom instructions help Copilot follow team conventions across prompts.

- Agents are best for broad expertise, such as code review, testing, or documentation.
- Custom instructions are best for standards that should apply across the repository.
- Agent files use markdown instructions with frontmatter metadata so Copilot can identify the agent and its purpose.

### References

- https://docs.github.com/copilot/how-tos/use-copilot-agents/use-copilot-cli
- https://docs.github.com/en/copilot/how-tos/custom-instructions/adding-repository-custom-instructions-for-github-copilot

### Activity: Add Project Guidance and a Specialist Agent

1. Create `.github/copilot-instructions.md` with standards for the starter application.
1. Create `.github/agents/project-reviewer.agent.md` for focused code quality review.
1. Use `/agent` in Copilot CLI to select or reason about the specialist agent.
1. Update `COPILOT_CLI_WORKFLOW.md` with when to use custom instructions versus an agent.

### Transition

- **Actions Trigger:** [`push`](https://docs.github.com/en/actions/reference/events-that-trigger-workflows#push)
- **Grading-Check:** Verify `.github/copilot-instructions.md` exists and contains project standards.
- **Grading-Check:** Verify `.github/agents/project-reviewer.agent.md` exists with frontmatter and a `description` field.

## Step 3 - Create and Use Agent Skills

### Story

Your team has repeatable tasks, such as checking code quality or generating tests. You will create an agent skill so Copilot can apply the same task instructions consistently.

### Theory

Agent skills are folders of instructions, scripts, and resources that Copilot can load when relevant. Skills differ from agents because they describe a specific repeatable task rather than a broad persona. In Copilot CLI, skills can be discovered automatically from the prompt or invoked directly as slash commands.

- Project skills can live in `.github/skills/` and apply to the current repository.
- A skill folder includes a `SKILL.md` file with metadata and task instructions.
- Skills can be used naturally through prompt matching or explicitly with slash-command style invocation.

### References

- https://docs.github.com/copilot/concepts/agents/about-agent-skills
- https://docs.github.com/copilot/how-tos/copilot-cli/customize-copilot/add-skills

### Activity: Add a Repeatable Review Skill

1. Create `.github/skills/code-quality-check/SKILL.md`.
1. Define the skill description so it matches code quality review prompts.
1. Add a concise checklist for validation, error handling, tests, maintainability, and documentation.
1. Use Copilot CLI to apply the skill directly or through a natural language prompt.
1. Update `COPILOT_CLI_WORKFLOW.md` with when to use a skill instead of an agent.

### Transition

- **Actions Trigger:** [`push`](https://docs.github.com/en/actions/reference/events-that-trigger-workflows#push)
- **Grading-Check:** Verify `.github/skills/code-quality-check/SKILL.md` exists.
- **Grading-Check:** Verify the skill includes a description and a checklist covering code quality review criteria.

## Step 4 - Configure MCP Servers

### Story

Your local repository context is useful, but real development often needs live context from GitHub, project files, or documentation. You will configure MCP so Copilot CLI can access approved external context.

### Theory

Model Context Protocol, or MCP, is an open standard for connecting Copilot to external systems and tools. Copilot CLI supports MCP servers, including the built-in GitHub MCP server and additional local or remote servers. MCP helps Copilot gather live context when a workflow needs repository data, documentation, or other tool-backed information.

- MCP servers provide tools and data sources beyond the current prompt and selected files.
- The GitHub MCP server is built in for Copilot CLI.
- Project-level MCP configuration can document the servers needed for a repository workflow.

### References

- https://docs.github.com/copilot/concepts/context/mcp
- https://docs.github.com/copilot/how-tos/copilot-cli/customize-copilot/add-mcp-servers

### Activity: Add MCP Configuration Notes

1. Use `/mcp show` in Copilot CLI to inspect configured MCP servers.
1. Create `.mcp.json` or an MCP setup section in `COPILOT_CLI_WORKFLOW.md` for the exercise workflow.
1. Document how the GitHub MCP server supports issue, pull request, and repository context.
1. Add an example of when documentation or filesystem MCP context would improve a Copilot CLI answer.

### Transition

- **Actions Trigger:** [`push`](https://docs.github.com/en/actions/reference/events-that-trigger-workflows#push)
- **Grading-Check:** Verify `COPILOT_CLI_WORKFLOW.md` includes `/mcp show` and a short explanation of MCP.
- **Grading-Check:** Verify either `.mcp.json` exists or the workflow notes explain why the built-in GitHub MCP server is sufficient for the exercise.

## Step 5 - Put It All Together

### Story

Now you will act like the conductor of an orchestra: use the right Copilot CLI capability at the right moment to move from an idea to a reviewed change.

### Theory

Advanced Copilot CLI usage is most effective when learners combine features intentionally. A strong workflow gathers context with files or MCP, plans with a slash command or agent, applies repeatable standards with skills, validates with tests or review, and summarizes the result for collaboration.

- Agents, skills, and MCP solve different problems and can be combined in one workflow.
- Slash commands are most effective when learners use them deliberately for mode switches, reviews, skills, and context inspection.
- A reusable workflow helps developers avoid context switching between terminal, editor, documentation, and GitHub.

### References

- https://docs.github.com/copilot/how-tos/use-copilot-agents/use-copilot-cli
- https://docs.github.com/copilot/concepts/context/mcp
- https://docs.github.com/copilot/concepts/agents/about-agent-skills

### Activity: Complete an Advanced Copilot CLI Workflow

1. Choose a small improvement in the starter application.
1. Gather context with `@` references and, when useful, MCP-backed repository context.
1. Use `/plan` to define the work before making changes.
1. Use the custom agent or skill to review quality expectations.
1. Use `/review` to inspect the final changes.
1. Update `COPILOT_CLI_WORKFLOW.md` with the final advanced workflow and the reason each slash command was used.

### Transition

- **Actions Trigger:** [`push`](https://docs.github.com/en/actions/reference/events-that-trigger-workflows#push)
- **Grading-Check:** Verify `COPILOT_CLI_WORKFLOW.md` includes a complete workflow that mentions development workflows, agents/custom instructions, skills, MCP, and final review.
- **Grading-Check:** Verify the repository contains `.github/copilot-instructions.md`, `.github/agents/project-reviewer.agent.md`, and `.github/skills/code-quality-check/SKILL.md`.

## Review

In this exercise, learners configured and used advanced Copilot CLI features in a complete terminal-based development workflow. They practiced slash commands, agents, custom instructions, skills, MCP, and final review patterns.

- Used `/plan`, `/review`, `/agent`, and `/mcp show` efficiently in Copilot CLI.
- Added repository custom instructions and a custom agent.
- Created a project agent skill for repeatable code quality checks.
- Explained how MCP servers provide live external context.
- Combined advanced features into an end-to-end workflow for productive development.

### What's next?

- https://docs.github.com/copilot/how-tos/use-copilot-agents/use-copilot-cli
- https://docs.github.com/copilot/reference/customization-cheat-sheet
- https://learn.github.com/skills

# Future Considerations

- Split this large exercise into a multi-part series if learners need more time with each feature area.
- Add optional challenge paths for hooks, pre-commit review automation, or custom MCP server configuration.
- Add language-specific variants for JavaScript, Python, or .NET starter applications.
