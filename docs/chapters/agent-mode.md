# Agent Mode

<div class="hero-container">
  <img src="../../assets/images/hero-agent.svg" alt="GitHub Copilot Agent Mode - Autonomous AI Assistance" class="hero-image">
</div>

Agent Mode represents the next evolution of GitHub Copilot, enabling autonomous AI agents that can perform complex, multi-step tasks with minimal human intervention.

## What is Agent Mode?

Agent Mode allows Copilot to act as an autonomous agent that can:

- Execute multi-step workflows
- Make decisions based on context
- Interact with external tools and services
- Complete complex tasks end-to-end

Unlike traditional Copilot suggestions, Agent Mode can plan, execute, and iterate on solutions independently.

## Key Capabilities

### Autonomous Task Execution

Agent Mode can handle complex requests like:

> "Create a REST API endpoint for user authentication with JWT tokens, including tests and documentation"

The agent will:

1. Analyze existing code structure
2. Create the authentication logic
3. Set up middleware
4. Write unit and integration tests
5. Generate API documentation
6. Commit changes with meaningful messages

### Tool Integration

Agents can interact with:

- **File System**: Create, read, update, delete files
- **Terminal**: Run commands, install packages
- **Git**: Create branches, commits, pull requests
- **External APIs**: Make HTTP requests
- **Databases**: Query and modify data

### Planning and Reasoning

The agent thinks through problems:

```
📋 Plan:
1. Analyze existing authentication code
2. Identify integration points
3. Create JWT utility functions
4. Implement login/logout endpoints
5. Add middleware for protected routes
6. Write comprehensive tests
7. Update documentation

🔄 Executing step 1 of 7...
```

## Using Agent Mode

### Activation

In supported IDEs, Agent Mode can be activated through:

1. **Chat Command**: Type `@workspace` to enable workspace-aware agent
2. **Specific Prompts**: Use action-oriented language
3. **Task Files**: Create `.github/copilot/tasks.md`

### Example Workflow

**Request:**
> "Set up a CI/CD pipeline for this Node.js project with testing, linting, and deployment to AWS"

**Agent Actions:**

```yaml
# .github/workflows/ci-cd.yml - Created by Copilot Agent
name: CI/CD Pipeline

on:
  push:
    branches: [main]
  pull_request:
    branches: [main]

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with:
          node-version: '20'
      - run: npm ci
      - run: npm run lint
      - run: npm test

  deploy:
    needs: test
    if: github.ref == 'refs/heads/main'
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Deploy to AWS
        # Deployment steps...
```

## Agent Capabilities Matrix

| Capability | Description | Example |
|------------|-------------|---------|
| Code Generation | Create new files and functions | "Create a user service" |
| Refactoring | Modify existing code | "Migrate to TypeScript" |
| Testing | Write and run tests | "Add integration tests" |
| Documentation | Generate docs | "Document all APIs" |
| DevOps | CI/CD and infrastructure | "Set up Docker" |

## Safety and Control

### Human-in-the-Loop

Agent Mode includes safeguards:

1. **Confirmation Prompts**: For destructive operations
2. **Preview Mode**: See changes before applying
3. **Rollback**: Undo agent actions
4. **Scope Limits**: Restrict agent permissions

### Permission Model

```yaml
# .github/copilot/config.yml
agent:
  permissions:
    file_write: true
    file_delete: false
    terminal_execute: true
    git_commit: true
    external_api: false
```

!!! warning "Review Agent Actions"
    Always review changes made by Agent Mode. While powerful, agents can make mistakes or misunderstand requirements.

## Best Practices

### Clear Instructions

Provide detailed requirements:

❌ *"Make this better"*

✅ *"Refactor this service to follow the repository pattern, add dependency injection, create interfaces for testing, and add unit tests with >80% coverage"*

### Incremental Tasks

Break large tasks into smaller steps:

1. "First, create the data models"
2. "Now add the repository layer"
3. "Add the service layer with business logic"
4. "Finally, create the API endpoints"

### Context Setting

Help the agent understand your codebase:

- Keep relevant files open
- Use descriptive file and function names
- Maintain up-to-date documentation
- Provide architecture diagrams

## Agent Mode vs Other Modes

| Feature | Agent Mode | Chat Mode | Edit Mode |
|---------|------------|-----------|-----------|
| Autonomy | High | Low | None |
| Multi-step | Yes | Limited | No |
| Tool Use | Extensive | Limited | None |
| Supervision | Less needed | Moderate | High |
| Complexity | Complex tasks | Q&A | Simple edits |

## Future of Agent Mode

Agent Mode continues to evolve with:

- **Enhanced Planning**: Better task decomposition
- **Improved Memory**: Longer context retention
- **More Tools**: Additional integrations
- **Collaboration**: Multi-agent workflows

---

<div class="resource-links">
<h2>📚 Resources</h2>
<ul>
<li><a href="https://github.blog/news-insights/product-news/github-copilot-the-agent-awakens/" target="_blank" rel="noopener">GitHub Blog: Copilot Agent Mode</a></li>
<li><a href="https://docs.github.com/en/copilot" target="_blank" rel="noopener">GitHub Copilot Documentation</a></li>
<li><a href="https://code.visualstudio.com/docs/copilot/copilot-chat" target="_blank" rel="noopener">VS Code Copilot Integration</a></li>
<li><a href="https://github.blog/changelog/" target="_blank" rel="noopener">GitHub Changelog for Latest Updates</a></li>
</ul>
</div>
