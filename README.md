# GraphQL Query Lab 🧪

[![Build Status](https://img.shields.io/badge/build-passing-brightgreen)](https://github.com/username/graphql-query-lab)
[![Version](https://img.shields.io/badge/version-1.0.0-blue)](https://github.com/username/graphql-query-lab/releases)
[![License](https://img.shields.io/badge/license-MIT-green)](LICENSE)
[![Node.js](https://img.shields.io/badge/node-%3E%3D14.0.0-green)](https://nodejs.org/)
[![GraphQL](https://img.shields.io/badge/GraphQL-E10098?logo=graphql&logoColor=white)](https://graphql.org/)

A modern, interactive GraphQL query laboratory for learning, testing, and experimenting with GraphQL queries, mutations, and subscriptions.

## Table of Contents

- [Features](#features)
- [Quick Start](#quick-start)
- [Installation](#installation)
- [Usage](#usage)
- [API Documentation](#api-documentation)
- [Examples](#examples)
- [Contributing](#contributing)
- [Testing](#testing)
- [Deployment](#deployment)
- [Troubleshooting](#troubleshooting)
- [License](#license)
- [Support](#support)

## Features

✨ **Interactive Query Editor** - Built-in GraphQL playground with syntax highlighting
🔍 **Schema Explorer** - Browse and discover available types, queries, and mutations
📊 **Real-time Results** - Execute queries and see results instantly
🎯 **Query Validation** - Real-time validation with helpful error messages
📚 **Example Library** - Pre-built queries and mutations for learning
🔧 **Customizable Endpoints** - Connect to any GraphQL API
📱 **Responsive Design** - Works seamlessly on desktop and mobile
🚀 **Performance Metrics** - Query execution time and performance insights

## Quick Start

Get up and running in less than 2 minutes:

```bash
# Clone the repository
git clone https://github.com/bakadja/graphql-query-lab.git

# Navigate to the project directory
cd graphql-query-lab

# Install dependencies
npm install

# Start the development server
npm run dev

# Open your browser and navigate to http://localhost:3000
```

## Installation

### Prerequisites

- Node.js (v14.0.0 or higher)
- npm or yarn package manager
- Modern web browser with ES6 support

### Local Development

```bash
# Install dependencies
npm install

# Start development server with hot reload
npm run dev

# Build for production
npm run build

# Start production server
npm start
```

### Docker Installation

```bash
# Build the Docker image
docker build -t graphql-query-lab .

# Run the container
docker run -p 3000:3000 graphql-query-lab
```

## Usage

### Basic Query Execution

1. **Connect to a GraphQL endpoint:**
   ```
   http://localhost:4000/graphql
   ```

2. **Write your first query:**
   ```graphql
   query GetUsers {
     users {
       id
       name
       email
     }
   }
   ```

3. **Execute and view results** in the response panel

### Advanced Features

#### Variables Support
```graphql
query GetUser($id: ID!) {
  user(id: $id) {
    id
    name
    posts {
      title
      content
    }
  }
}
```

Variables panel:
```json
{
  "id": "123"
}
```

#### Mutations
```graphql
mutation CreateUser($input: CreateUserInput!) {
  createUser(input: $input) {
    id
    name
    email
  }
}
```

#### Subscriptions
```graphql
subscription OnCommentAdded($postId: ID!) {
  commentAdded(postId: $postId) {
    id
    content
    author {
      name
    }
  }
}
```

## API Documentation

### Configuration Options

| Option | Type | Default | Description |
|--------|------|---------|-------------|
| `endpoint` | string | `http://localhost:4000/graphql` | GraphQL endpoint URL |
| `headers` | object | `{}` | Custom headers for requests |
| `credentials` | string | `"same-origin"` | Request credentials mode |
| `timeout` | number | `10000` | Request timeout in milliseconds |

### Environment Variables

```bash
# .env file
GRAPHQL_ENDPOINT=http://localhost:4000/graphql
API_KEY=your-api-key
PORT=3000
NODE_ENV=development
```

## Examples

### Query Examples

<details>
<summary>User Management Queries</summary>

```graphql
# Get all users with pagination
query GetUsers($first: Int, $after: String) {
  users(first: $first, after: $after) {
    edges {
      node {
        id
        name
        email
        createdAt
      }
    }
    pageInfo {
      hasNextPage
      endCursor
    }
  }
}

# Search users by name
query SearchUsers($query: String!) {
  searchUsers(query: $query) {
    id
    name
    email
    avatar
  }
}
```

</details>

<details>
<summary>Post Management Mutations</summary>

```graphql
# Create a new post
mutation CreatePost($input: CreatePostInput!) {
  createPost(input: $input) {
    id
    title
    content
    author {
      name
    }
    createdAt
  }
}

# Update existing post
mutation UpdatePost($id: ID!, $input: UpdatePostInput!) {
  updatePost(id: $id, input: $input) {
    id
    title
    content
    updatedAt
  }
}
```

</details>

## Contributing

We welcome contributions! Please see our [Contributing Guide](CONTRIBUTING.md) for details.

### Development Workflow

1. **Fork the repository**
2. **Create a feature branch:**
   ```bash
   git checkout -b feature/amazing-feature
   ```
3. **Make your changes and commit:**
   ```bash
   git commit -m "Add amazing feature"
   ```
4. **Push to your branch:**
   ```bash
   git push origin feature/amazing-feature
   ```
5. **Open a Pull Request**

### Code Style

We use ESLint and Prettier for code formatting:

```bash
# Lint code
npm run lint

# Format code
npm run format

# Type check
npm run type-check
```

## Testing

### Running Tests

```bash
# Run all tests
npm test

# Run tests in watch mode
npm run test:watch

# Run tests with coverage
npm run test:coverage

# Run E2E tests
npm run test:e2e
```

### Test Structure

```
tests/
├── unit/           # Unit tests
├── integration/    # Integration tests
├── e2e/           # End-to-end tests
└── fixtures/      # Test data and mocks
```

## Deployment

### Vercel Deployment

[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/clone?repository-url=https://github.com/username/graphql-query-lab)

### Netlify Deployment

[![Deploy to Netlify](https://www.netlify.com/img/deploy/button.svg)](https://app.netlify.com/start/deploy?repository=https://github.com/username/graphql-query-lab)

### Manual Deployment

```bash
# Build the project
npm run build

# Deploy the build folder to your hosting service
```

## Troubleshooting

### Common Issues

**Q: GraphQL endpoint not responding**
```bash
# Check if the endpoint is accessible
curl -X POST -H "Content-Type: application/json" \
  -d '{"query": "{ __typename }"}' \
  http://localhost:4000/graphql
```

**Q: CORS errors when connecting to external APIs**
- Add proper CORS headers to your GraphQL server
- Use a proxy server for development

**Q: Queries timing out**
- Check your `timeout` configuration
- Optimize your GraphQL queries
- Consider using query complexity analysis

### Getting Help

- 📖 [Documentation](https://github.com/username/graphql-query-lab/wiki)
- 💬 [Discussions](https://github.com/username/graphql-query-lab/discussions)
- 🐛 [Issue Tracker](https://github.com/username/graphql-query-lab/issues)

## License

This project is licensed under the Apache License - see the [LICENSE](LICENSE) file for details.

## Support

### Community

- **GitHub Discussions:** [Ask questions and share ideas](https://github.com/username/graphql-query-lab/discussions)
- **Discord:** [Join our community server](https://discord.gg/graphql-query-lab)
- **Stack Overflow:** Tag your questions with `graphql-query-lab`

### Sponsors

This project is made possible by our amazing sponsors:

<a href="https://github.com/sponsors/bakadja">
  <img src="https://img.shields.io/badge/Sponsor-❤️-red?style=for-the-badge" alt="Sponsor" />
</a>

---

<p align="center">
  Made with ❤️ by <a href="https://github.com/username">Your Name</a>
</p>

<p align="center">
  <a href="#table-of-contents">Back to top ⬆️</a>
</p>
