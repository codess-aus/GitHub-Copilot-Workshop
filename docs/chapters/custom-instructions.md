# Custom Instructions

<div class="hero-container">
  <img src="../../assets/images/hero-custom-instructions.svg" alt="Custom Instructions - Personalize GitHub Copilot" class="hero-image">
</div>

Custom Instructions allow you to personalize GitHub Copilot's behavior to match your coding style, project requirements, and team standards.

## What are Custom Instructions?

Custom Instructions are persistent guidelines that shape how Copilot responds to your requests. They help Copilot understand:

- Your preferred coding style
- Project-specific conventions
- Technology stack preferences
- Documentation standards

## Setting Up Custom Instructions

### Repository-Level Instructions

Create a `.github/copilot-instructions.md` file:

```markdown
# Project Copilot Instructions

## Code Style
- Use TypeScript for all new files
- Follow ESLint Airbnb configuration
- Use functional components with hooks for React
- Prefer named exports over default exports

## Naming Conventions
- Components: PascalCase (e.g., UserProfile.tsx)
- Functions: camelCase (e.g., getUserData)
- Constants: SCREAMING_SNAKE_CASE (e.g., MAX_RETRIES)
- Files: kebab-case (e.g., user-service.ts)

## Documentation
- All public functions must have JSDoc comments
- Include @param and @returns tags
- Add example usage for complex functions

## Testing
- Write tests using Jest and React Testing Library
- Aim for >80% code coverage
- Include edge cases and error scenarios
```

### User-Level Instructions

Set personal preferences in your IDE:

=== "VS Code"

    1. Open Settings (Ctrl+,)
    2. Search for "Copilot instructions"
    3. Add your preferences in the text field

=== "JetBrains"

    1. Open Settings → GitHub Copilot
    2. Find "Custom Instructions" section
    3. Enter your guidelines

### Example Personal Instructions

```markdown
# My Copilot Preferences

## General
- I prefer verbose variable names over abbreviations
- Always include error handling
- Add comments explaining "why" not "what"

## Languages
- Python: Use type hints, follow PEP 8
- JavaScript: Use modern ES6+ syntax
- SQL: Use uppercase keywords

## Frameworks
- React: Functional components with TypeScript
- Express: Async/await with error middleware
- Testing: Arrange-Act-Assert pattern
```

## Effective Instructions

### Be Specific

❌ Vague:
```
Write good code
```

✅ Specific:
```
- Use early returns to reduce nesting
- Limit functions to 20 lines when possible
- Extract complex conditions into named variables
```

### Include Examples

```markdown
## Error Handling Pattern

Always use this error handling pattern:

```typescript
try {
  const result = await riskyOperation();
  return { success: true, data: result };
} catch (error) {
  logger.error('Operation failed', { error, context });
  return { success: false, error: error.message };
}
```
```

### Specify Anti-Patterns

```markdown
## Avoid These Patterns

❌ Don't use:
- `any` type in TypeScript
- Nested ternary operators
- Magic numbers without constants
- Console.log in production code

✅ Do use:
- Proper typing with interfaces
- Clear if/else or switch statements
- Named constants for values
- Structured logging
```

## Instruction Categories

### Code Quality

```markdown
## Quality Guidelines
- DRY: Don't repeat yourself
- SOLID principles for OOP code
- Prefer composition over inheritance
- Keep cyclomatic complexity low
```

### Security

```markdown
## Security Requirements
- Never hardcode credentials
- Sanitize all user inputs
- Use parameterized queries
- Implement proper authentication checks
- Log security-relevant events
```

### Performance

```markdown
## Performance Guidelines
- Use pagination for list endpoints
- Implement caching where appropriate
- Optimize database queries
- Use lazy loading for heavy components
- Consider bundle size for imports
```

### Accessibility

```markdown
## Accessibility Standards
- Include ARIA labels where needed
- Ensure keyboard navigation works
- Use semantic HTML elements
- Maintain color contrast ratios
- Test with screen readers
```

## Project-Specific Examples

### React Project

```markdown
# React Project Instructions

## Component Structure
- One component per file
- Props interface at the top
- Hooks before render logic
- Event handlers prefixed with "handle"

## State Management
- Use React Query for server state
- Use Zustand for client state
- Avoid prop drilling > 2 levels

## Styling
- Use CSS Modules or Tailwind
- Follow BEM naming for CSS classes
- Mobile-first responsive design
```

### Python API Project

```markdown
# Python API Instructions

## Code Style
- Follow PEP 8
- Use type hints everywhere
- Maximum line length: 88 (Black formatter)

## API Design
- RESTful endpoints
- Use Pydantic for validation
- Return consistent response formats

## Database
- Use SQLAlchemy ORM
- Always use transactions
- Index frequently queried columns
```

## Team Collaboration

### Shared Instructions

Store team instructions in the repository:

```
.github/
├── copilot-instructions.md    # Main instructions
├── copilot/
│   ├── style-guide.md         # Coding style
│   ├── security.md            # Security rules
│   └── testing.md             # Testing standards
```

### Instruction Templates

Create templates for common project types:

| Project Type | Template Focus |
|--------------|----------------|
| Frontend | Components, styling, accessibility |
| Backend | API design, database, security |
| Library | Documentation, compatibility, testing |
| Infrastructure | Security, scalability, monitoring |

## Troubleshooting

### Instructions Not Working?

1. **Check File Location**: Must be in `.github/copilot-instructions.md`
2. **Verify Syntax**: Use valid Markdown
3. **Clear Instructions**: Avoid conflicting rules
4. **Restart IDE**: Changes may require restart

### Conflicting Instructions

If user and repository instructions conflict:

- Repository instructions take precedence for that project
- Consider aligning personal preferences with team standards

!!! tip "Keep It Simple"
    Start with a few key instructions and expand over time. Too many rules can be counterproductive.

---

<div class="resource-links">
<h2>📚 Resources</h2>
<ul>
<li><a href="https://docs.github.com/en/copilot/customizing-copilot/adding-custom-instructions-for-github-copilot" target="_blank" rel="noopener">Custom Instructions Documentation</a></li>
<li><a href="https://docs.github.com/en/copilot/using-github-copilot/getting-started-with-github-copilot" target="_blank" rel="noopener">Getting Started with Copilot</a></li>
<li><a href="https://github.blog/2023-11-08-universe-2023-copilot-transforms-github-into-the-ai-powered-developer-platform/" target="_blank" rel="noopener">GitHub Universe 2023 - Copilot Updates</a></li>
<li><a href="https://code.visualstudio.com/docs/copilot/copilot-customization" target="_blank" rel="noopener">VS Code Copilot Customization</a></li>
<li><a href="https://github.com/github/awesome-copilot" target="_blank" rel="noopener">Awesome GitHub Copilot Customizations</a></li>
</ul>
</div>
