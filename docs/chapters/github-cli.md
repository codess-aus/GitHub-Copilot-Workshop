# GitHub CLI

<div class="hero-container">
  <img src="../../assets/images/hero-cli.svg" alt="GitHub CLI with Copilot - Command Line AI" class="hero-image">
</div>

GitHub CLI (`gh`) brings Copilot's AI capabilities to your terminal, enabling AI-assisted workflows directly from the command line.

## What is GitHub CLI with Copilot?

GitHub CLI integrates Copilot directly into your terminal workflow, allowing you to:

- Get command suggestions
- Explain complex commands
- Generate scripts
- Interact with GitHub from the terminal

## Installation

### Prerequisites

1. Install GitHub CLI (`gh`)
2. Have GitHub Copilot access
3. Authenticate with GitHub

### Setup

```bash
# Install GitHub CLI (if not already installed)
# macOS
brew install gh

# Windows
winget install GitHub.cli

# Linux
sudo apt install gh
# or
sudo dnf install gh

# Authenticate
gh auth login

# Install Copilot extension
gh extension install github/gh-copilot
```

## Core Commands

### Ask Copilot

Get help with any question:

```bash
# Ask a question
gh copilot suggest "how do I find large files in git history"

# Response:
# Command: git rev-list --objects --all | git cat-file --batch-check='%(objecttype) %(objectname) %(objectsize) %(rest)' | sed -n 's/^blob //p' | sort -nk2 | tail -20
# Explanation: This finds the 20 largest blobs in your git history...
```

### Explain Commands

Understand complex commands:

```bash
gh copilot explain "awk '{print $2}' file.txt | sort | uniq -c | sort -rn | head -10"

# Response:
# This command pipeline:
# 1. Extracts the second column from file.txt
# 2. Sorts the values
# 3. Counts unique occurrences
# 4. Sorts by count in descending order
# 5. Shows the top 10 results
```

### Suggest Commands

Get command suggestions for tasks:

```bash
gh copilot suggest "create a new branch and switch to it"

# Response:
# git checkout -b new-branch-name
# or
# git switch -c new-branch-name
```

## Common Use Cases

### Git Operations

| Task | Ask Copilot |
|------|-------------|
| Undo last commit | "how to undo the last commit but keep changes" |
| Squash commits | "squash last 3 commits into one" |
| Find commit | "find commit that introduced a bug" |
| Clean up | "remove all merged branches" |

### GitHub Operations

```bash
# Create a PR
gh copilot suggest "create a pull request with title and body"

# Review PRs
gh copilot suggest "list all PRs that need my review"

# Issues
gh copilot suggest "close all issues with label 'wontfix'"
```

### Shell Operations

```bash
# File operations
gh copilot suggest "find all files modified in the last 24 hours"

# Process management
gh copilot suggest "find process using port 3000 and kill it"

# Disk usage
gh copilot suggest "show disk usage by directory sorted by size"
```

## Interactive Mode

Enter interactive mode for multi-turn conversations:

```bash
gh copilot
# Entering interactive mode...

> How do I set up a git hook?

I can help you set up a git hook. What kind of hook do you need?
- pre-commit: runs before commit
- post-commit: runs after commit
- pre-push: runs before push
...

> I want a pre-commit hook to run linting

Here's how to set up a pre-commit hook for linting:

1. Create the hook file:
   echo '#!/bin/sh
   npm run lint
   if [ $? -ne 0 ]; then
     echo "Linting failed. Please fix errors before committing."
     exit 1
   fi' > .git/hooks/pre-commit

2. Make it executable:
   chmod +x .git/hooks/pre-commit
```

## Shell Integration

### Aliases

Add helpful aliases to your shell config:

```bash
# ~/.bashrc or ~/.zshrc

# Quick Copilot access
alias cop='gh copilot suggest'
alias cope='gh copilot explain'

# Common tasks
alias gc='gh copilot suggest "git commit with message"'
alias gpr='gh copilot suggest "create pull request"'
```

### Completions

Enable shell completions:

```bash
# Bash
gh completion -s bash > /etc/bash_completion.d/gh

# Zsh
gh completion -s zsh > ~/.zsh/completions/_gh

# Fish
gh completion -s fish > ~/.config/fish/completions/gh.fish
```

## Advanced Usage

### Scripting

Use Copilot in scripts:

```bash
#!/bin/bash
# Automated code review script

# Get Copilot's suggestion for reviewing changes
changes=$(git diff --stat)
gh copilot suggest "review these git changes for issues: $changes"
```

### Integration with Other Tools

```bash
# Pipe output to Copilot
cat error.log | gh copilot explain "what's wrong in this log"

# Use with other CLI tools
gh copilot suggest "jq query to extract user names from this json" < users.json
```

## Tips and Tricks

### Be Specific

❌ `gh copilot suggest "do git stuff"`

✅ `gh copilot suggest "rebase my branch onto main and resolve conflicts automatically preferring my changes"`

### Context Helps

Provide context for better suggestions:

```bash
gh copilot suggest "I'm working on a Node.js project with npm, how do I update all dependencies"
```

### Learn from Explanations

Use `explain` to learn new commands:

```bash
# Found a command online? Understand it before running:
gh copilot explain "find . -type f -name '*.js' -exec grep -l 'TODO' {} +"
```

!!! warning "Security"
    Always review suggested commands before running them, especially those that:
    
    - Delete files (`rm`, `del`)
    - Modify system settings
    - Access sensitive data
    - Make network requests

## Troubleshooting

| Issue | Solution |
|-------|----------|
| Extension not found | Run `gh extension install github/gh-copilot` |
| Authentication error | Run `gh auth login` again |
| Slow responses | Check network connection |
| Incorrect suggestions | Provide more context |

---

<div class="resource-links">
<h2>📚 Resources</h2>
<ul>
<li><a href="https://cli.github.com/" target="_blank" rel="noopener">GitHub CLI Official Site</a></li>
<li><a href="https://docs.github.com/en/copilot/using-github-copilot/using-github-copilot-in-the-command-line" target="_blank" rel="noopener">Copilot in CLI Documentation</a></li>
<li><a href="https://github.com/cli/cli" target="_blank" rel="noopener">GitHub CLI Repository</a></li>
<li><a href="https://github.com/github/gh-copilot" target="_blank" rel="noopener">Copilot CLI Extension</a></li>
</ul>
</div>
