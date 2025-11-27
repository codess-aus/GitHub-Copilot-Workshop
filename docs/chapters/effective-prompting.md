# Effective Prompting

<div class="hero-container">
  <img src="../../assets/images/hero-prompting.svg" alt="Effective Prompting - Master AI Communication" class="hero-image">
</div>

Effective prompting is the key to getting the best results from GitHub Copilot. Learn how to communicate your intentions clearly and get high-quality code suggestions.

## The Art of Prompting

Prompting is how you communicate with AI. Better prompts lead to:

- More accurate suggestions
- Fewer iterations needed
- Higher quality code
- Better understanding of your intent

## Prompt Structure

### The CONTEXT Framework

| Element | Description | Example |
|---------|-------------|---------|
| **C**ontext | Background information | "In a React app with TypeScript..." |
| **O**bjective | What you want to achieve | "Create a component that..." |
| **N**uance | Specific requirements | "Using hooks, accessible..." |
| **T**one | Style preferences | "Following our team conventions..." |
| **E**xamples | Reference patterns | "Similar to UserCard component" |
| **X**tra | Additional constraints | "Must handle edge cases..." |

### Basic Structure

```
[Context] + [Objective] + [Constraints] + [Examples]
```

## Prompting Techniques

### 1. Be Specific

❌ **Vague:**
```
// function to handle data
```

✅ **Specific:**
```
// Function that fetches user data from /api/users endpoint,
// handles loading and error states, and returns typed UserData
```

### 2. Provide Context

❌ **No context:**
```
// sort array
```

✅ **With context:**
```
// Sort array of Product objects by price in descending order
// Products have: id (string), name (string), price (number)
interface Product {
  id: string;
  name: string;
  price: number;
}
```

### 3. Use Examples

```python
# Parse date strings in various formats to datetime objects
# Examples:
# "2024-01-15" -> datetime(2024, 1, 15)
# "January 15, 2024" -> datetime(2024, 1, 15)
# "15/01/2024" -> datetime(2024, 1, 15)

def parse_date(date_string: str) -> datetime:
```

### 4. Specify Output Format

```javascript
// Create a function that returns user statistics
// Input: array of User objects
// Output: { total: number, active: number, averageAge: number }
```

### 5. Include Edge Cases

```python
# Divide two numbers safely
# - Handle division by zero (return None)
# - Handle non-numeric inputs (raise TypeError)
# - Round result to 2 decimal places
```

## Prompt Patterns

### Pattern: Step-by-Step

Break complex tasks into steps:

```javascript
// Process user registration:
// Step 1: Validate email format
// Step 2: Check if email already exists
// Step 3: Hash the password
// Step 4: Create user record
// Step 5: Send welcome email
// Step 6: Return success response
```

### Pattern: Before/After

Show transformation:

```python
# Transform flat data to nested structure
# Before: [{"id": 1, "parent": null}, {"id": 2, "parent": 1}]
# After: [{"id": 1, "children": [{"id": 2, "children": []}]}]
```

### Pattern: Constraints List

```typescript
// Create a password validation function
// Must:
// - Be at least 8 characters
// - Contain uppercase and lowercase
// - Have at least one number
// - Have at least one special character
// Return: { valid: boolean, errors: string[] }
```

### Pattern: Role Assignment

```
You are an expert React developer. Create a reusable Modal 
component that:
- Uses React Portal for DOM placement
- Supports keyboard accessibility (ESC to close)
- Has customizable overlay and close button
- Includes animation on open/close
```

## Chat-Specific Prompting

### For Explanations

```
Explain this code like I'm a junior developer:
[code block]

Focus on:
- What each part does
- Why certain patterns are used
- Potential issues or improvements
```

### For Debugging

```
This function should [expected behavior] but instead 
[actual behavior].

Here's the code:
[code]

Here's the error:
[error message]

Input that causes the issue:
[example input]
```

### For Refactoring

```
Refactor this code to:
- Use async/await instead of callbacks
- Add TypeScript types
- Follow DRY principles
- Improve error handling

Current code:
[code block]
```

## Advanced Techniques

### Chain of Thought

Guide Copilot through reasoning:

```python
# To calculate shipping cost:
# First, determine the shipping zone based on zip code
# Then, calculate base cost from package weight
# Next, apply zone multiplier
# Finally, add any surcharges for special handling
```

### Negative Prompting

Specify what NOT to do:

```javascript
// Create a date formatter
// DO NOT use external libraries (no moment.js, date-fns)
// DO NOT use deprecated Date methods
// USE native Intl.DateTimeFormat
```

### Template Prompting

```python
# Create CRUD operations for {Entity}
# 
# Pattern to follow:
# - create_{entity}(data) -> {Entity}
# - get_{entity}(id) -> {Entity} | None
# - update_{entity}(id, data) -> {Entity}
# - delete_{entity}(id) -> bool
# - list_{entities}(filters) -> List[{Entity}]
#
# Now implement for: Product
```

## Common Mistakes

### ❌ Too Vague

```
// make it work
```

### ❌ Too Long

```
// Create a function that does many things and handles 
// every possible case and also logs and caches and 
// validates and transforms and... [continues for 20 lines]
```

### ❌ Contradictory

```
// Make it fast but also readable and also handle every 
// edge case but keep it simple
```

### ❌ Assuming Context

```
// use the user from before
// (Copilot doesn't remember previous files)
```

## Prompting Checklist

Before submitting a prompt, verify:

- [ ] **Clear objective**: Is it obvious what I want?
- [ ] **Sufficient context**: Does Copilot have needed background?
- [ ] **Specific constraints**: Are requirements explicit?
- [ ] **Examples provided**: Are there samples to guide output?
- [ ] **Output format defined**: Do I specify the expected result?
- [ ] **Edge cases mentioned**: Are special cases addressed?

## Practice Exercises

Try these prompting challenges:

1. **Basic**: Write a prompt for a function that calculates BMI
2. **Intermediate**: Prompt for a REST API endpoint handler
3. **Advanced**: Prompt for a state machine implementation
4. **Expert**: Prompt for a code generation tool

---

<div class="resource-links">
<h2>📚 Resources</h2>
<ul>
<li><a href="https://docs.github.com/en/copilot/using-github-copilot/prompt-engineering-for-github-copilot" target="_blank" rel="noopener">GitHub Copilot Prompt Engineering Guide</a></li>
<li><a href="https://github.blog/2023-06-20-how-to-write-better-prompts-for-github-copilot/" target="_blank" rel="noopener">How to Write Better Prompts</a></li>
<li><a href="https://code.visualstudio.com/docs/copilot/prompt-crafting" target="_blank" rel="noopener">VS Code Prompt Crafting Guide</a></li>
<li><a href="https://docs.github.com/en/copilot/using-github-copilot/getting-started-with-github-copilot" target="_blank" rel="noopener">Getting Started with Copilot</a></li>
</ul>
</div>
