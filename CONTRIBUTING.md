# Contributing to GraphQL Query Lab 🤝

Thank you for your interest in contributing to GraphQL Query Lab! We welcome contributions from the community and are excited to collaborate with you.

## Table of Contents

- [Code of Conduct](#code-of-conduct)
- [Getting Started](#getting-started)
- [Development Setup](#development-setup)
- [How to Contribute](#how-to-contribute)
- [Coding Standards](#coding-standards)
- [Testing Guidelines](#testing-guidelines)
- [Pull Request Process](#pull-request-process)
- [Issue Guidelines](#issue-guidelines)
- [Community](#community)

## Code of Conduct

This project and everyone participating in it is governed by our [Code of Conduct](CODE_OF_CONDUCT.md). By participating, you are expected to uphold this code. Please report unacceptable behavior to [contact@kevinpaulidor.de](mailto:contact@kevinpaulidor.de).

## Getting Started

### Prerequisites

Before contributing, make sure you have:

- Node.js (v14.0.0 or higher)
- npm or yarn package manager
- Git
- A GitHub account
- Basic knowledge of GraphQL, React, and TypeScript

### First Time Setup

1. **Fork the repository** on GitHub
2. **Clone your fork** locally:
   ```bash
   git clone https://github.com/bakadja/graphql-query-lab.git
   cd graphql-query-lab
   ```

3. **Add the original repository as upstream**:
   ```bash
   git remote add upstream https://github.com/bakadja/graphql-query-lab.git
   ```

4. **Install dependencies**:
   ```bash
   npm install
   ```

5. **Create a new branch** for your feature:
   ```bash
   git checkout -b feature/your-feature-name
   ```

## Development Setup

### Environment Configuration

Create a `.env.local` file in the root directory:

```bash
# Development environment variables
GRAPHQL_ENDPOINT=http://localhost:4000/graphql
NODE_ENV=development
PORT=3000
```

### Running the Development Server

```bash
# Start the development server
npm run dev

# Run with debug mode
npm run dev:debug

# Run storybook (if available)
npm run storybook
```

### Project Structure

```
graphql-query-lab/
├── src/
│   ├── components/          # React components
│   ├── hooks/              # Custom React hooks
│   ├── services/           # API services and utilities
│   ├── types/              # TypeScript type definitions
│   ├── utils/              # Utility functions
│   └── __tests__/          # Test files
├── public/                 # Static assets
├── docs/                   # Documentation
└── tests/                  # Integration and E2E tests
```

## How to Contribute

### Types of Contributions

We welcome various types of contributions:

- 🐛 **Bug fixes**
- ✨ **New features**
- 📚 **Documentation improvements**
- 🎨 **UI/UX enhancements**
- ⚡ **Performance optimizations**
- 🧪 **Test coverage improvements**
- 🌐 **Internationalization**

### Finding Issues to Work On

- Check our [Good First Issues](https://github.com/bakadja/graphql-query-lab/labels/good%20first%20issue) for beginners
- Look for [Help Wanted](https://github.com/bakadja/graphql-query-lab/labels/help%20wanted) issues
- Browse [Enhancement](https://github.com/bakadja/graphql-query-lab/labels/enhancement) requests

### Before You Start

1. **Check existing issues** to avoid duplicating work
2. **Comment on the issue** you'd like to work on
3. **Wait for assignment** or approval from maintainers
4. **Ask questions** if anything is unclear

## Coding Standards

### Code Style

We use ESLint and Prettier to maintain consistent code style:

```bash
# Check code style
npm run lint

# Fix auto-fixable issues
npm run lint:fix

# Format code with Prettier
npm run format

# Type checking
npm run type-check
```

### Naming Conventions

- **Components**: PascalCase (`QueryEditor.tsx`)
- **Files**: kebab-case (`query-editor.utils.ts`)
- **Variables/Functions**: camelCase (`executeQuery`)
- **Constants**: UPPER_SNAKE_CASE (`DEFAULT_TIMEOUT`)
- **Types/Interfaces**: PascalCase (`GraphQLQuery`)

### Component Guidelines

```typescript
// Use functional components with TypeScript
interface QueryEditorProps {
  endpoint: string;
  onQueryExecute?: (query: string) => void;
}

export const QueryEditor: React.FC<QueryEditorProps> = ({
  endpoint,
  onQueryExecute
}) => {
  // Component implementation
};
```

### Commit Message Format

We follow the [Conventional Commits](https://www.conventionalcommits.org/) specification:

```
<type>[optional scope]: <description>

[optional body]

[optional footer(s)]
```

**Types:**
- `feat`: New feature
- `fix`: Bug fix
- `docs`: Documentation changes
- `style`: Code style changes (formatting, etc.)
- `refactor`: Code refactoring
- `test`: Adding or updating tests
- `chore`: Maintenance tasks

**Examples:**
```
feat(editor): add syntax highlighting for GraphQL queries
fix(api): handle timeout errors in query execution
docs: update installation instructions
test: add unit tests for query validator
```

## Testing Guidelines

### Running Tests

```bash
# Run all tests
npm test

# Run tests in watch mode
npm run test:watch

# Run tests with coverage
npm run test:coverage

# Run specific test file
npm test -- QueryEditor.test.tsx

# Run E2E tests
npm run test:e2e
```

### Writing Tests

#### Unit Tests

```typescript
// src/components/__tests__/QueryEditor.test.tsx
import { render, screen, fireEvent } from '@testing-library/react';
import { QueryEditor } from '../QueryEditor';

describe('QueryEditor', () => {
  it('should render query editor', () => {
    render(<QueryEditor endpoint="http://localhost:4000/graphql" />);
    expect(screen.getByRole('textbox')).toBeInTheDocument();
  });

  it('should execute query on button click', () => {
    const onQueryExecute = jest.fn();
    render(
      <QueryEditor
        endpoint="http://localhost:4000/graphql"
        onQueryExecute={onQueryExecute}
      />
    );
    
    fireEvent.click(screen.getByText('Execute'));
    expect(onQueryExecute).toHaveBeenCalled();
  });
});
```

#### Integration Tests

```typescript
// tests/integration/query-execution.test.ts
describe('Query Execution Flow', () => {
  it('should execute GraphQL query and display results', async () => {
    // Test implementation
  });
});
```

### Test Coverage

We aim for:
- **Minimum 80% code coverage**
- **100% coverage for utility functions**
- **Critical path testing for all features**

## Pull Request Process

### Before Submitting

1. **Update your branch** with the latest changes:
   ```bash
   git fetch upstream
   git rebase upstream/main
   ```

2. **Run the test suite**:
   ```bash
   npm test
   npm run lint
   npm run type-check
   ```

3. **Update documentation** if necessary

### Pull Request Checklist

- [ ] Code follows the style guidelines
- [ ] Self-review of the code completed
- [ ] Comments added for complex logic
- [ ] Tests added/updated for new functionality
- [ ] Documentation updated if needed
- [ ] No breaking changes (or clearly documented)
- [ ] Branch is up-to-date with main

### PR Title and Description

**Title Format:**
```
feat(scope): brief description of changes
```

**Description Template:**
```markdown
## Description
Brief description of what this PR does.

## Type of Change
- [ ] Bug fix (non-breaking change which fixes an issue)
- [ ] New feature (non-breaking change which adds functionality)
- [ ] Breaking change (fix or feature that would cause existing functionality to not work as expected)
- [ ] This change requires a documentation update

## Testing
- [ ] Unit tests pass
- [ ] Integration tests pass
- [ ] Manual testing completed

## Screenshots (if applicable)
Add screenshots to help explain your changes.

## Additional Notes
Any additional information that reviewers should know.
```

### Review Process

1. **Automated checks** must pass (CI/CD, tests, linting)
2. **At least one maintainer** must approve
3. **All conversations** must be resolved
4. **Squash and merge** is preferred for feature branches

## Issue Guidelines

### Bug Reports

Use the bug report template and include:

- **Clear description** of the issue
- **Steps to reproduce** the problem
- **Expected vs actual behavior**
- **Environment details** (OS, browser, Node version)
- **Screenshots or error logs** if applicable

### Feature Requests

Use the feature request template and include:

- **Problem description** you're trying to solve
- **Proposed solution** with implementation details
- **Alternatives considered**
- **Additional context** or mockups

### Security Issues

**Do not** open public issues for security vulnerabilities. Instead:

1. Email details to [contact@kevinpaulidor.de](mailto:contact@kevinpaulidor.de)
2. Include steps to reproduce
3. Allow time for assessment and fix
4. Coordinate disclosure timeline

## Community

### Communication Channels

- **GitHub Discussions**: General questions and ideas
- **Discord**: Real-time chat with maintainers and contributors
- **Issues**: Bug reports and feature requests
- **Email**: [contact@kevinpaulidor.de](mailto:contact@kevinpaulidor.de)

### Recognition

Contributors are recognized in:

- **README.md** contributors section
- **Release notes** for significant contributions
- **Discord** contributor role
- **Annual contributor highlights**

### Getting Help

- **Read the documentation** first
- **Search existing issues** for similar problems
- **Ask in Discord** for quick questions
- **Open a discussion** for broader topics

## Development Tips

### Useful Commands

```bash
# Reset your environment
npm run clean && npm install

# Generate component boilerplate
npm run generate:component ComponentName

# Analyze bundle size
npm run analyze

# Update dependencies
npm run deps:update
```

### Debugging

```bash
# Debug tests
npm run test:debug

# Debug with VS Code
# Use the provided launch.json configuration

# Browser debugging
# React DevTools and Apollo DevTools recommended
```

---

## Thank You! 🎉

Every contribution makes GraphQL Query Lab better for everyone. We appreciate your time and effort in making this project successful!

For questions about contributing, feel free to reach out to the maintainers or join our community discussions.

**Happy coding!** 🚀