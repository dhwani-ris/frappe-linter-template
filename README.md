# Frappe Linter Template

A comprehensive template repository for Frappe-based projects with pre-configured linting, formatting, code quality tools, and automated CI/CD pipeline. This template ensures every custom Frappe app follows the same high-quality standards and best practices.

## 🚀 Features

### 🔧 **Code Quality & Linting**
- **Pre-commit Hooks**: Automated code quality checks before commits
- **Multi-language Support**: Python, JavaScript, Vue, SCSS, and more
- **Code Formatting**: Consistent code style with Ruff and Prettier
- **Comprehensive Linting**: Ruff, ESLint, and TypeScript support
- **Type Checking**: MyPy integration for Python type safety

### 🛡️ **Security & Safety**
- **Semgrep Integration**: Security-focused static analysis
- **Dependency Scanning**: Automated vulnerability detection with pip-audit
- **Bandit Security**: Python security linting
- **Safety Checks**: Dependency vulnerability scanning

### 🔄 **CI/CD Pipeline**
- **GitHub Actions**: Comprehensive automated testing and quality checks
- **Semantic Commits**: Enforced conventional commit format
- **Multi-version Testing**: Python 3.8-3.13 compatibility
- **Build Verification**: Automated package and asset building
- **Coverage Reporting**: Code coverage tracking and reporting

### 📚 **Documentation & Standards**
- **Documentation Templates**: Ready-to-use documentation structure
- **Frappe Guidelines**: Comprehensive Frappe app development standards
- **Development Tools**: VS Code settings and recommended extensions
- **Contributing Guidelines**: Clear contribution and development workflows

## 📋 Prerequisites

- **Python 3.8+** (supports up to 3.13)
- **Node.js 16+** (recommended: 22+)
- **Git** with conventional commits
- **Frappe Framework 14+**

## 🛠️ Quick Start

### 1. Use This Template

```bash
# Create a new repository using this template
gh repo create your-project-name --template dhwani-rural/frappe-linter-template

# Or clone and customize
git clone https://github.com/dhwani-rural/frappe-linter-template.git your-project-name
cd your-project-name
```

### 2. Install Dependencies

```bash
# Install Python dependencies
pip install -e ".[dev]"

# Install pre-commit hooks
pre-commit install

# Install Node.js dependencies (if using frontend tools)
npm install
```

### 3. Customize Configuration

1. Update `pyproject.toml` with your project details
2. Modify `.pre-commit-config.yaml` for your specific needs
3. Update GitHub Actions in `.github/workflows/`
4. Customize documentation templates

## 📁 Project Structure

```
frappe-linter-template/
├── .github/
│   └── workflows/          # GitHub Actions CI/CD
│       ├── ci.yml         # Comprehensive CI pipeline
│       └── linters.yml    # Linting workflow
├── .vscode/               # VS Code settings
├── docs/                  # Documentation templates
│   ├── CONTRIBUTING.md    # Contribution guidelines
│   ├── CHANGELOG.md       # Version history template
│   ├── CODE_OF_CONDUCT.md # Community standards
│   ├── DEVELOPMENT.md     # Development setup guide
│   └── FRAPPE_APP_GUIDELINES.md # Frappe-specific standards
├── templates/             # Project templates
├── scripts/               # Utility scripts
├── .pre-commit-config.yaml # Pre-commit configuration
├── pyproject.toml         # Python project configuration
├── package.json           # Node.js dependencies
└── README.md             # This file
```

## 🔧 Configuration

### Pre-commit Hooks

The template includes the following pre-commit hooks:

- **trailing-whitespace**: Removes trailing whitespace
- **check-merge-conflict**: Detects merge conflict markers
- **check-ast**: Validates Python syntax
- **check-json/toml/yaml**: Validates configuration files
- **debug-statements**: Removes debug statements
- **ruff**: Python linting and formatting
- **prettier**: Code formatting for JS/CSS
- **eslint**: JavaScript linting

### CI/CD Pipeline

The comprehensive CI workflow includes:

- **Semantic Commits**: Validates commit message format
- **Security Scanning**: Semgrep and dependency vulnerability checks
- **Code Quality**: Pre-commit hooks and linting
- **Testing**: Multi-version Python testing with coverage
- **Build Verification**: Package and asset building
- **Dependency Management**: Outdated dependency detection

### Customization

Edit configuration files to:
- Add/remove hooks in `.pre-commit-config.yaml`
- Modify linting rules in `pyproject.toml`
- Adjust CI workflow in `.github/workflows/ci.yml`
- Update VS Code settings in `.vscode/`

## 🛡️ Security Features

### Automated Security Checks

- **Semgrep**: Static analysis with Frappe-specific rules
- **pip-audit**: Python dependency vulnerability scanning
- **Bandit**: Python security linting
- **Safety**: Additional dependency security checks

### Security Best Practices

- Regular dependency updates
- Automated vulnerability scanning
- Security-focused linting rules
- Comprehensive error handling

## 📚 Documentation Templates

The `docs/` directory contains comprehensive templates for:

- **API Documentation**: Standardized API reference format
- **Contributing Guidelines**: Clear contribution workflows
- **Changelog Template**: Version history tracking
- **Code of Conduct**: Community standards
- **Development Setup Guide**: Environment configuration
- **Frappe App Guidelines**: Frappe-specific best practices

## 🎯 Best Practices

### Code Quality
- Run `pre-commit run --all-files` before pushing
- Keep commits atomic and well-described using conventional format
- Follow the established code style and linting rules
- Write comprehensive tests with good coverage

### Documentation
- Update README.md for project-specific information
- Maintain up-to-date API documentation
- Document breaking changes in CHANGELOG.md
- Follow Frappe app development guidelines

### Development Workflow
1. Create feature branch from main
2. Make changes with proper commit messages
3. Run pre-commit hooks locally
4. Create pull request with description
5. Ensure CI passes before merging
6. Follow semantic versioning

### Security
- Regularly update dependencies
- Address security warnings promptly
- Follow secure coding practices
- Use automated security scanning

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Make your changes following the coding standards
4. Run pre-commit hooks (`pre-commit run --all-files`)
5. Commit with conventional format (`git commit -m "feat: add amazing feature"`)
6. Push to the branch (`git push origin feature/amazing-feature`)
7. Submit a pull request

See [CONTRIBUTING.md](docs/CONTRIBUTING.md) for detailed guidelines.

## 🧪 Testing

### Running Tests

```bash
# Run all tests
pytest

# Run with coverage
pytest --cov=frappe_linter_template

# Run specific test categories
pytest -m unit
pytest -m integration
pytest -m "not slow"
```

### Test Coverage

The template includes comprehensive test coverage reporting:
- HTML coverage reports
- XML coverage for CI integration
- Coverage thresholds and exclusions
- Integration with Codecov

## 🔄 CI/CD Pipeline

### Automated Checks

The CI pipeline runs on every pull request and push:

1. **Semantic Commits**: Validates commit message format
2. **Security Scanning**: Semgrep and dependency checks
3. **Code Quality**: Pre-commit hooks and linting
4. **Testing**: Multi-version Python testing
5. **Build Verification**: Package and asset building
6. **Dependency Management**: Outdated dependency detection

### Pipeline Features

- **Concurrency Control**: Prevents multiple workflows from running simultaneously
- **Caching**: Optimized dependency caching for faster builds
- **Artifact Management**: Uploads reports and build artifacts
- **Graceful Degradation**: Handles missing configurations gracefully
- **Matrix Testing**: Tests across multiple Python versions

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🆘 Support

- **Issues**: [GitHub Issues](https://github.com/dhwani-rural/frappe-linter-template/issues)
- **Discussions**: [GitHub Discussions](https://github.com/dhwani-rural/frappe-linter-template/discussions)
- **Documentation**: [Wiki](https://github.com/dhwani-rural/frappe-linter-template/wiki)
- **CI/CD Status**: [GitHub Actions](https://github.com/dhwani-rural/frappe-linter-template/actions)

## 🔄 Updates

This template is regularly updated with:
- Latest tool versions and security patches
- New best practices and standards
- Enhanced CI/CD pipeline features
- Improved documentation and guidelines
- Frappe framework compatibility updates

Check the [CHANGELOG.md](docs/CHANGELOG.md) for recent updates.

## 🎉 Benefits

Using this template ensures:

- **Consistency**: Every app follows the same structure and standards
- **Quality**: Automated checks maintain high code quality
- **Security**: Built-in security scanning and best practices
- **Maintainability**: Standardized patterns and documentation
- **Scalability**: Robust CI/CD pipeline supports team growth
- **Compliance**: Follows industry best practices and standards

---

**Made with ❤️ by [Dhwani Rural Information Systems](https://dhwani.org)**
