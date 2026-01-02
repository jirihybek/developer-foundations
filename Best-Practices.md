# Best Practices

Below is a short list of best practices in general.

## KISS

- Kepp It Simple, Stupid. Always aim for the simplest solution that works. Avoid over-engineering.
- The best code is no code.
- If something feels complicated, it's probably a bad design and it should be re-thought and simplified.

## Self-explanatory Code

- Write code that is easy to read and understand without extensive comments. When somone reads your code, they should get the idea quickly.
- Use meaningful and descriptive names for variables, functions, classes, and modules.
- Yes it will be long and chatty but it's english and it should read like a story and you should always get idea what is going on.

**Variables:**
```typescript
// Bad
const a = 5;

// Good
const maxLoginAttempts = 5;
```

**Functions/Methods:**
```typescript
// Bad
function get(id: string): User {
  // ...
}

// Good
function getUserById(userId: string): User {
  // ...
}

function getUserByIdOrThrow(userId: string): User {
  // ...
}
```

## Consistent Formatting

- Follow a consistent coding style and formatting guidelines throughout the codebase. Each project may have its own style guide, so make sure to adhere to it.
- Use linters and formatters to automate code style enforcement (e.g., ESLint, Prettier for JavaScript/TypeScript).
