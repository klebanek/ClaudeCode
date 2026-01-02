# CLAUDE.md - AI Assistant Guide for ClaudeCode

> **Purpose**: This document provides comprehensive guidance for AI assistants (like Claude) working with this codebase. It covers structure, conventions, workflows, and best practices.

---

## Table of Contents

1. [Repository Overview](#repository-overview)
2. [Codebase Structure](#codebase-structure)
3. [Development Workflows](#development-workflows)
4. [Key Conventions](#key-conventions)
5. [Testing Guidelines](#testing-guidelines)
6. [Common Tasks](#common-tasks)
7. [AI Assistant Best Practices](#ai-assistant-best-practices)

---

## Repository Overview

### Project Description
ClaudeCode is [describe the project purpose here].

### Tech Stack
- **Language**: [Primary programming language]
- **Framework**: [Main framework if applicable]
- **Package Manager**: [npm, yarn, pip, cargo, etc.]
- **Runtime**: [Node.js, Python, etc.]

### Key Dependencies
[List major dependencies and their purposes]

---

## Codebase Structure

```
ClaudeCode/
├── src/                 # Source code
│   ├── components/      # Reusable components
│   ├── utils/          # Utility functions
│   ├── services/       # Business logic and API services
│   └── types/          # Type definitions
├── tests/              # Test files
├── docs/               # Documentation
├── scripts/            # Build and utility scripts
├── .github/            # GitHub workflows and templates
└── config/             # Configuration files
```

### Directory Purposes

- **src/**: Main application source code
- **tests/**: Unit, integration, and e2e tests
- **docs/**: Project documentation and guides
- **scripts/**: Development and deployment scripts
- **config/**: Environment and build configurations

### Key Files

- **package.json**: Project metadata and dependencies
- **tsconfig.json**: TypeScript configuration
- **.eslintrc**: Linting rules
- **.prettierrc**: Code formatting rules
- **README.md**: Project overview and setup instructions

---

## Development Workflows

### Initial Setup

```bash
# Clone the repository
git clone [repository-url]
cd ClaudeCode

# Install dependencies
npm install  # or yarn install, pip install -r requirements.txt, etc.

# Set up environment variables
cp .env.example .env
# Edit .env with your configuration

# Run initial build
npm run build
```

### Git Workflow

1. **Branch Naming Convention**:
   - Feature branches: `feature/description`
   - Bug fixes: `fix/description`
   - AI assistant branches: `claude/description-XXXXX`

2. **Commit Message Format**:
   ```
   type(scope): brief description

   Detailed explanation if needed
   ```
   Types: `feat`, `fix`, `docs`, `style`, `refactor`, `test`, `chore`

3. **Development Flow**:
   ```bash
   # Create feature branch
   git checkout -b feature/my-feature

   # Make changes and commit
   git add .
   git commit -m "feat: add new feature"

   # Push to remote
   git push -u origin feature/my-feature

   # Create pull request
   gh pr create --title "Add new feature" --body "Description..."
   ```

### Code Review Process

- All changes require pull request review
- Automated checks must pass (linting, tests, build)
- At least one approving review required
- Squash commits when merging

---

## Key Conventions

### Code Style

- **Indentation**: [2 spaces, 4 spaces, tabs]
- **Line Length**: Maximum [80, 100, 120] characters
- **Naming Conventions**:
  - Variables/Functions: `camelCase`
  - Classes/Types: `PascalCase`
  - Constants: `UPPER_SNAKE_CASE`
  - Files: `kebab-case.ts` or `PascalCase.tsx`

### File Organization

- **One component per file**: Each component should have its own file
- **Index files**: Use for barrel exports only
- **Test files**: Co-locate with source files as `*.test.ts` or in `__tests__/`
- **Type definitions**: Place in `types/` or co-locate as `*.types.ts`

### Import Order

```typescript
// 1. External dependencies
import React from 'react';
import { useState } from 'react';

// 2. Internal modules
import { utils } from '@/utils';

// 3. Relative imports
import { Component } from './Component';

// 4. Types
import type { Props } from './types';

// 5. Styles
import styles from './styles.module.css';
```

### Error Handling

- Use try-catch blocks for async operations
- Always validate external inputs
- Provide meaningful error messages
- Log errors appropriately (debug, info, warn, error)

### Comments and Documentation

- **JSDoc**: Use for public APIs and complex functions
- **Inline comments**: Explain "why", not "what"
- **TODOs**: Format as `// TODO(name): description`
- **FIXMEs**: Format as `// FIXME: description`

---

## Testing Guidelines

### Test Structure

```typescript
describe('ComponentName', () => {
  it('should perform expected behavior', () => {
    // Arrange
    const input = setupInput();

    // Act
    const result = performAction(input);

    // Assert
    expect(result).toBe(expected);
  });
});
```

### Testing Principles

- **Unit Tests**: Test individual functions/components in isolation
- **Integration Tests**: Test component interactions
- **E2E Tests**: Test complete user workflows
- **Coverage Target**: Aim for >80% code coverage
- **Test Naming**: Use descriptive names explaining the scenario

### Running Tests

```bash
# Run all tests
npm test

# Run tests in watch mode
npm test -- --watch

# Run tests with coverage
npm test -- --coverage

# Run specific test file
npm test path/to/test.test.ts
```

---

## Common Tasks

### Adding a New Feature

1. Create feature branch: `git checkout -b feature/new-feature`
2. Implement the feature with tests
3. Update documentation if needed
4. Run linter and tests: `npm run lint && npm test`
5. Commit changes with descriptive message
6. Push and create pull request

### Fixing a Bug

1. Create bug fix branch: `git checkout -b fix/bug-description`
2. Write a failing test that reproduces the bug
3. Fix the bug and ensure test passes
4. Run full test suite
5. Commit and push changes

### Updating Dependencies

```bash
# Check for outdated packages
npm outdated

# Update specific package
npm update package-name

# Update all packages (use with caution)
npm update

# Audit for security vulnerabilities
npm audit

# Fix vulnerabilities
npm audit fix
```

### Running Linters and Formatters

```bash
# Lint code
npm run lint

# Fix linting issues automatically
npm run lint:fix

# Format code
npm run format

# Check formatting without changes
npm run format:check
```

### Building for Production

```bash
# Build production bundle
npm run build

# Preview production build locally
npm run preview

# Run production build locally
npm start
```

---

## AI Assistant Best Practices

### When Working with This Codebase

1. **Always Read Before Modifying**
   - Use Read tool to understand existing code
   - Never propose changes to code you haven't read
   - Understand context before making suggestions

2. **Follow Existing Patterns**
   - Match the style and structure of existing code
   - Use the same naming conventions
   - Follow the established directory structure

3. **Avoid Over-Engineering**
   - Only make changes that are directly requested
   - Keep solutions simple and focused
   - Don't add unnecessary features or abstractions

4. **Security Considerations**
   - Watch for common vulnerabilities (XSS, SQL injection, etc.)
   - Validate all external inputs
   - Use parameterized queries for database operations
   - Sanitize user-generated content

5. **Testing Requirements**
   - Write tests for new features
   - Update tests when modifying existing code
   - Ensure all tests pass before committing

6. **Documentation**
   - Update documentation when changing functionality
   - Add JSDoc comments for public APIs
   - Keep README.md current with setup instructions

7. **Git Practices**
   - Use clear, descriptive commit messages
   - Don't commit secrets or sensitive data
   - Check git status before committing
   - Review changes before pushing

8. **Communication**
   - Ask clarifying questions when requirements are unclear
   - Explain the reasoning behind significant changes
   - Provide context for architectural decisions

### Tools and Commands Reference

```bash
# Development
npm run dev              # Start development server
npm run build           # Build for production
npm run test            # Run tests
npm run lint            # Lint code
npm run format          # Format code

# Git
git status              # Check repository status
git log --oneline -10   # View recent commits
git diff                # View unstaged changes
git diff --staged       # View staged changes

# Package Management
npm install package     # Install new package
npm uninstall package   # Remove package
npm outdated           # Check for updates
npm audit              # Security audit
```

### File Navigation Patterns

When referencing code locations, use the format:
- `file_path:line_number` (e.g., `src/utils/helper.ts:42`)

### Task Management

Use the TodoWrite tool to:
- Break down complex tasks into steps
- Track progress on multi-step operations
- Provide visibility to users
- Ensure all requirements are met

---

## Updating This Document

This document should be updated when:
- Project structure changes significantly
- New conventions are adopted
- Development workflows are modified
- New tools or frameworks are added
- Common issues and solutions are discovered

**Last Updated**: 2026-01-02

---

## Additional Resources

- [Project README](./README.md)
- [Contributing Guidelines](./CONTRIBUTING.md)
- [Code of Conduct](./CODE_OF_CONDUCT.md)
- [API Documentation](./docs/api.md)
- [Architecture Overview](./docs/architecture.md)

---

## Contact and Support

- **Repository**: https://github.com/klebanek/ClaudeCode
- **Issues**: Use GitHub Issues for bug reports and feature requests
- **Discussions**: Use GitHub Discussions for questions and ideas

---

*This document is maintained for AI assistants working with this codebase. It should be kept current as the project evolves.*
