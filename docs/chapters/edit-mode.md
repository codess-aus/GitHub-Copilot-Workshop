# Edit Mode

<div class="hero-container">
  <img src="../../assets/images/hero-edit.svg" alt="GitHub Copilot Edit Mode - Inline Code Editing" class="hero-image">
</div>

Edit Mode in GitHub Copilot allows you to make inline modifications to your code using natural language instructions. It's perfect for quick refactoring, adding features, or modifying existing implementations.

## What is Edit Mode?

Edit Mode lets you select code and describe changes you want to make. Copilot then suggests modifications directly in your editor, showing you exactly what will change before you accept.

## How to Use Edit Mode

### Basic Workflow

1. **Select Code**: Highlight the code you want to modify
2. **Invoke Edit**: Use `Ctrl+I` (Windows/Linux) or `Cmd+I` (Mac)
3. **Describe Changes**: Type what you want to change
4. **Review**: See the diff of proposed changes
5. **Accept or Modify**: Apply changes or request adjustments

### Example: Adding Error Handling

**Before:**
```javascript
function fetchUser(id) {
  return fetch(`/api/users/${id}`)
    .then(response => response.json());
}
```

**Instruction:** *"Add error handling and retry logic"*

**After:**
```javascript
async function fetchUser(id, retries = 3) {
  for (let i = 0; i < retries; i++) {
    try {
      const response = await fetch(`/api/users/${id}`);
      if (!response.ok) {
        throw new Error(`HTTP error! status: ${response.status}`);
      }
      return await response.json();
    } catch (error) {
      if (i === retries - 1) throw error;
      await new Promise(r => setTimeout(r, 1000 * (i + 1)));
    }
  }
}
```

## Common Edit Operations

### Refactoring

| Request | Example |
|---------|---------|
| Convert to async/await | *"Convert this callback function to async/await"* |
| Extract method | *"Extract the validation logic into a separate function"* |
| Add types | *"Add TypeScript types to this function"* |
| Simplify | *"Simplify this conditional logic"* |

### Adding Features

- *"Add input validation"*
- *"Add logging statements"*
- *"Add caching to this function"*
- *"Add pagination support"*

### Code Quality

- *"Add JSDoc comments"*
- *"Make this code more readable"*
- *"Follow the single responsibility principle"*
- *"Add unit tests for edge cases"*

## Multi-File Edits

Edit Mode can work across multiple files:

1. Select code in multiple files (using multi-cursor or file selection)
2. Invoke Edit Mode
3. Describe the change
4. Review changes across all files

!!! tip "Consistent Changes"
    Use multi-file edits for consistent refactoring, like renaming a function across your codebase.

## Edit Mode vs Chat Mode

| Feature | Edit Mode | Chat Mode |
|---------|-----------|-----------|
| **Purpose** | Modify existing code | Discuss and generate |
| **Interaction** | Inline in editor | Sidebar conversation |
| **Output** | Diff view | Text and code blocks |
| **Best for** | Quick refactoring | Exploration and learning |

## Keyboard Shortcuts

=== "VS Code"

    | Action | Shortcut |
    |--------|----------|
    | Start Edit | `Ctrl+I` / `Cmd+I` |
    | Accept Change | `Ctrl+Enter` |
    | Reject Change | `Escape` |
    | Cycle Suggestions | `Alt+]` / `Alt+[` |

=== "JetBrains"

    | Action | Shortcut |
    |--------|----------|
    | Start Edit | `Alt+\` |
    | Accept Change | `Tab` |
    | Reject Change | `Escape` |

## Best Practices

### Be Precise

❌ *"Make this better"*

✅ *"Add input validation to check that email is a valid format"*

### Scope Your Selection

Select only the code you want to modify. Too much context can lead to unnecessary changes.

### Review Carefully

Always review the diff before accepting:

- Check that only intended lines changed
- Verify the logic is correct
- Ensure no unintended side effects

### Iterative Refinement

Don't expect perfection on the first try:

1. Make the initial edit
2. Review the result
3. Request additional refinements
4. Accept when satisfied

!!! warning "Test Your Changes"
    Always run tests after applying edits to ensure functionality is preserved.

## Advanced Techniques

### Combining with Chat

Use Chat Mode to understand code first, then Edit Mode to make changes:

1. Ask Chat: *"Explain what this function does"*
2. Use Edit: *"Now optimize it for performance"*

### Template Transformations

Edit Mode excels at pattern-based changes:

- *"Convert all console.log to logger.debug"*
- *"Replace var with const where possible"*
- *"Add error boundaries to all async operations"*

---

<div class="resource-links">
<h2>📚 Resources</h2>
<ul>
<li><a href="https://docs.github.com/en/copilot/using-github-copilot/using-github-copilot-in-the-command-line" target="_blank" rel="noopener">GitHub Copilot Documentation</a></li>
<li><a href="https://code.visualstudio.com/docs/copilot/copilot-edits" target="_blank" rel="noopener">VS Code Copilot Edits Guide</a></li>
<li><a href="https://github.blog/changelog/2024-10-29-github-copilot-code-review-in-github-com-public-preview/" target="_blank" rel="noopener">Copilot Code Review Features</a></li>
<li><a href="https://docs.github.com/en/copilot/quickstart" target="_blank" rel="noopener">Copilot Quickstart Guide</a></li>
</ul>
</div>
