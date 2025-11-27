# Chat Mode

<div class="hero-container">
  <img src="../../assets/images/hero-chat.svg" alt="GitHub Copilot Chat - Interactive AI Assistance" class="hero-image">
</div>

GitHub Copilot Chat brings conversational AI directly into your development environment, allowing you to ask questions, get explanations, and receive coding assistance through natural language.

## What is Chat Mode?

Chat Mode enables interactive conversations with GitHub Copilot. Instead of just receiving code suggestions, you can:

- Ask questions about code
- Request explanations
- Debug issues collaboratively
- Generate code from descriptions
- Refactor existing code

## Key Capabilities

### Code Explanation

```python
# Select this code and ask Copilot to explain it
def quicksort(arr):
    if len(arr) <= 1:
        return arr
    pivot = arr[len(arr) // 2]
    left = [x for x in arr if x < pivot]
    middle = [x for x in arr if x == pivot]
    right = [x for x in arr if x > pivot]
    return quicksort(left) + middle + quicksort(right)
```

Ask: *"Explain how this quicksort implementation works"*

### Code Generation

You can describe what you need:

> "Create a React component that displays a user profile card with name, avatar, and bio"

Copilot will generate the complete component with proper structure.

### Debugging Assistance

Share error messages with Copilot:

> "I'm getting this error: `TypeError: Cannot read property 'map' of undefined`. Here's my code..."

### Code Refactoring

Request improvements:

> "Refactor this function to use async/await instead of callbacks"

## Chat Commands

Use slash commands for specific actions:

| Command | Description |
|---------|-------------|
| `/explain` | Explain selected code |
| `/fix` | Suggest fixes for problems |
| `/tests` | Generate unit tests |
| `/doc` | Generate documentation |
| `/optimize` | Suggest performance improvements |

## Using Chat in Different IDEs

=== "VS Code"

    - Open Chat: `Ctrl+Shift+I` (Windows/Linux) or `Cmd+Shift+I` (Mac)
    - Inline Chat: `Ctrl+I` or `Cmd+I`
    - Select code and right-click for context menu options

=== "JetBrains"

    - Open Chat: `Alt+C` or through the Copilot tool window
    - Right-click selected code for options
    - Use the Copilot icon in the editor gutter

=== "GitHub.com"

    - Use Copilot Chat in pull requests
    - Ask questions about code changes
    - Get review suggestions

## Effective Chat Strategies

### Be Specific

❌ *"Fix this code"*

✅ *"This function should validate email addresses but it's accepting invalid formats. Can you fix the regex pattern?"*

### Provide Context

❌ *"How do I sort this?"*

✅ *"I have an array of user objects with 'createdAt' date strings. How do I sort them from newest to oldest?"*

### Iterate on Responses

Don't hesitate to ask follow-up questions:

1. "Generate a function to parse CSV files"
2. "Can you add error handling for malformed rows?"
3. "Now add type hints and docstrings"

!!! tip "Context Matters"
    Copilot Chat uses your current file and open tabs as context. Open relevant files before asking questions for better answers.

## Chat in GitHub.com

GitHub Copilot Chat is also available on GitHub.com:

- **Pull Requests**: Get explanations of changes
- **Issues**: Ask about implementation approaches
- **Discussions**: Technical Q&A
- **Repository Navigation**: Understand codebases

## Privacy and Data

!!! info "Your Conversations"
    - Chat conversations are not used to train Copilot models
    - Business and Enterprise users have additional privacy controls
    - You can clear conversation history at any time

---

<div class="resource-links">
<h2>📚 Resources</h2>
<ul>
<li><a href="https://docs.github.com/en/copilot/github-copilot-chat/about-github-copilot-chat" target="_blank" rel="noopener">About GitHub Copilot Chat</a></li>
<li><a href="https://docs.github.com/en/copilot/github-copilot-chat/using-github-copilot-chat" target="_blank" rel="noopener">Using Copilot Chat in Your IDE</a></li>
<li><a href="https://github.blog/2023-07-20-github-copilot-chat-beta-now-available-for-every-organization/" target="_blank" rel="noopener">Copilot Chat Announcement</a></li>
<li><a href="https://code.visualstudio.com/docs/copilot/copilot-chat" target="_blank" rel="noopener">VS Code Copilot Chat Guide</a></li>
</ul>
</div>
