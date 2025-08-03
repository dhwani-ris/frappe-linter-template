# Contributing to Frappe Linter Template

Thank you for your interest in contributing to the Frappe Linter Template! This document provides guidelines and information for contributors.

## 🤝 How to Contribute

We welcome contributions from the community! Here are the main ways you can contribute:

### 🐛 Reporting Bugs

1. **Check existing issues** - Search the [issues page](https://github.com/dhwani-rural/frappe-linter-template/issues) to see if the bug has already been reported
2. **Create a new issue** - Use the bug report template and provide:
   - Clear description of the problem
   - Steps to reproduce
   - Expected vs actual behavior
   - Environment details (OS, Python version, etc.)
   - Screenshots if applicable

### 💡 Suggesting Enhancements

1. **Check existing discussions** - Look through [GitHub Discussions](https://github.com/dhwani-rural/frappe-linter-template/discussions)
2. **Create a feature request** - Use the feature request template and include:
   - Clear description of the enhancement
   - Use cases and benefits
   - Implementation suggestions (if any)

### 🔧 Code Contributions

#### Prerequisites

- Python 3.8+
- Node.js 16+
- Git
- pre-commit

#### Development Setup

1. **Fork the repository**
   ```bash
   git clone https://github.com/your-username/frappe-linter-template.git
   cd frappe-linter-template
   ```

2. **Install dependencies**
   ```bash
   # Python dependencies
   pip install -e ".[dev]"

   # Node.js dependencies
   npm install

   # Install pre-commit hooks
   pre-commit install
   ```

3. **Create a feature branch**
   ```bash
   git checkout -b feature/your-feature-name
   ```

#### Development Guidelines

##### Code Style

- **Python**: Follow PEP 8 with Black formatting (88 character line length)
- **JavaScript/TypeScript**: Use ESLint and Prettier configuration
- **Vue**: Follow Vue 3 style guide
- **Documentation**: Use clear, concise language with proper markdown formatting

##### Commit Messages

Use conventional commit format:
```
type(scope): description

[optional body]

[optional footer]
```

Types:
- `feat`: New feature
- `fix`: Bug fix
- `docs`: Documentation changes
- `style`: Code style changes (formatting, etc.)
- `refactor`: Code refactoring
- `test`: Adding or updating tests
- `chore`: Maintenance tasks

Examples:
```
feat(pre-commit): add new linting rule for Python imports
fix(config): resolve Ruff configuration issue
docs(readme): update installation instructions
```

##### Testing

- Write tests for new features
- Ensure all existing tests pass
- Maintain good test coverage

##### Pull Request Process

1. **Create a pull request** with a clear description
2. **Reference issues** that the PR addresses
3. **Ensure CI passes** - all checks must be green
4. **Request review** from maintainers
5. **Address feedback** promptly

#### PR Checklist

- [ ] Code follows style guidelines
- [ ] Tests pass locally
- [ ] Documentation is updated
- [ ] Commit messages follow conventional format
- [ ] PR description is clear and complete
- [ ] All CI checks pass

## 📋 Issue Templates

### Bug Report Template

```markdown
## Bug Description
Brief description of the bug

## Steps to Reproduce
1. Step 1
2. Step 2
3. Step 3

## Expected Behavior
What you expected to happen

## Actual Behavior
What actually happened

## Environment
- OS: [e.g., Ubuntu 20.04]
- Python Version: [e.g., 3.9.7]
- Node.js Version: [e.g., 16.14.0]
- pre-commit Version: [e.g., 3.0.0]

## Additional Information
Any other context, logs, or screenshots
```

### Feature Request Template

```markdown
## Feature Description
Clear description of the feature

## Use Cases
How this feature would be used

## Benefits
Why this feature would be valuable

## Implementation Ideas
Any thoughts on how to implement (optional)

## Alternatives Considered
Other approaches you've considered (optional)
```

## 🏷️ Labels

We use the following labels to categorize issues and PRs:

- `bug`: Something isn't working
- `enhancement`: New feature or request
- `documentation`: Improvements or additions to documentation
- `good first issue`: Good for newcomers
- `help wanted`: Extra attention is needed
- `priority: high`: High priority items
- `priority: low`: Low priority items
- `python`: Python-related changes
- `javascript`: JavaScript/TypeScript changes
- `config`: Configuration changes

## 🎯 Development Priorities

1. **Bug fixes** - Critical issues affecting functionality
2. **Security updates** - Security-related improvements
3. **Documentation** - Improving clarity and completeness
4. **New features** - Adding useful functionality
5. **Code quality** - Refactoring and improvements

## 📞 Getting Help

- **GitHub Discussions**: [Ask questions](https://github.com/dhwani-rural/frappe-linter-template/discussions)
- **Issues**: [Report problems](https://github.com/dhwani-rural/frappe-linter-template/issues)
- **Email**: info@dhwani.org

## 🙏 Recognition

Contributors will be recognized in:
- Repository contributors list
- Release notes
- Documentation acknowledgments

## 📄 License

By contributing, you agree that your contributions will be licensed under the MIT License.

---

Thank you for contributing to the Frappe Linter Template! 🎉
