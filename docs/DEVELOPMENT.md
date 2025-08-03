# Development Setup Guide

This guide will help you set up your development environment for working with the Frappe Linter Template and projects created from it.

## 🛠️ Prerequisites

Before you begin, ensure you have the following installed:

### Required Software

- **Python 3.8+**: [Download Python](https://www.python.org/downloads/)
- **Node.js 16+**: [Download Node.js](https://nodejs.org/)
- **Git**: [Download Git](https://git-scm.com/)
- **VS Code** (recommended): [Download VS Code](https://code.visualstudio.com/)

### Verify Installation

```bash
# Check Python version
python --version
# or
python3 --version

# Check Node.js version
node --version

# Check npm version
npm --version

# Check Git version
git --version
```

## 🚀 Quick Setup

### 1. Clone the Repository

```bash
# Clone the template repository
git clone https://github.com/dhwani-rural/frappe-linter-template.git
cd frappe-linter-template

# Or if using as a template for a new project
gh repo create your-project-name --template dhwani-rural/frappe-linter-template
cd your-project-name
```

### 2. Set Up Python Environment

```bash
# Create virtual environment
python -m venv venv

# Activate virtual environment
# On Windows:
venv\Scripts\activate
# On macOS/Linux:
source venv/bin/activate

# Install dependencies
pip install -e ".[dev]"
```

### 3. Set Up Node.js Environment

```bash
# Install Node.js dependencies
npm install
```

### 4. Install Pre-commit Hooks

```bash
# Install pre-commit hooks
pre-commit install

# Run pre-commit on all files (optional)
pre-commit run --all-files
```

## 🔧 Development Tools

### VS Code Setup

The template includes VS Code settings and recommended extensions. To use them:

1. **Open the project in VS Code**
   ```bash
   code .
   ```

2. **Install recommended extensions**
   - VS Code will prompt you to install recommended extensions
   - Or manually install from `.vscode/extensions.json`

3. **Use the provided settings**
   - Settings are automatically applied from `.vscode/settings.json`

### Recommended Extensions

- **Python**: Microsoft Python extension
- **ESLint**: ESLint extension
- **Prettier**: Prettier extension
- **GitLens**: Git integration
- **GitHub Pull Requests**: GitHub integration

## 📝 Development Workflow

### 1. Making Changes

```bash
# Create a new branch
git checkout -b feature/your-feature-name

# Make your changes
# ... edit files ...

# Stage changes
git add .

# Commit with conventional commit format
git commit -m "feat: add new feature"
```

### 2. Running Quality Checks

```bash
# Run pre-commit hooks (automatic on commit)
pre-commit run

# Run Python linting
ruff check .

# Run Python formatting
ruff format .

# Run JavaScript linting
npm run lint

# Run JavaScript formatting
npm run format
```

### 3. Testing

```bash
# Run Python tests
pytest

# Run with coverage
pytest --cov=your_project_name

# Run JavaScript tests (if configured)
npm test
```

## 🎯 Project Customization

### 1. Update Project Information

Edit these files to customize for your project:

- `pyproject.toml`: Python project metadata
- `package.json`: Node.js project metadata
- `README.md`: Project documentation
- `.pre-commit-config.yaml`: Pre-commit hooks configuration

### 2. Configure Linting Rules

#### Python (Ruff)

Edit `pyproject.toml` under `[tool.ruff]`:

```toml
[tool.ruff]
select = [
    "E",  # pycodestyle errors
    "W",  # pycodestyle warnings
    "F",  # pyflakes
    "I",  # isort
    "B",  # flake8-bugbear
]
ignore = [
    "E501",  # line too long
]
```

#### JavaScript (ESLint)

Edit `package.json` under `eslintConfig`:

```json
{
  "eslintConfig": {
    "rules": {
      "no-console": "warn",
      "no-unused-vars": "error"
    }
  }
}
```

### 3. Add Project-Specific Files

Create additional files as needed:

```bash
# Create project structure
mkdir -p your_project_name
touch your_project_name/__init__.py

# Create tests directory
mkdir -p tests
touch tests/__init__.py
touch tests/test_your_project.py

# Create documentation
mkdir -p docs
touch docs/API.md
```

## 🔍 Troubleshooting

### Common Issues

#### Pre-commit Hooks Fail

```bash
# Update pre-commit hooks
pre-commit autoupdate

# Run specific hook
pre-commit run ruff --all-files
```

#### Python Import Issues

```bash
# Reinstall in development mode
pip install -e ".[dev]"

# Check Python path
python -c "import sys; print(sys.path)"
```

#### Node.js Dependency Issues

```bash
# Clear npm cache
npm cache clean --force

# Reinstall dependencies
rm -rf node_modules package-lock.json
npm install
```

#### VS Code Issues

1. **Extensions not working**: Reload VS Code window
2. **Settings not applied**: Check `.vscode/settings.json` syntax
3. **Python interpreter**: Select correct virtual environment

### Getting Help

- **GitHub Issues**: [Create an issue](https://github.com/dhwani-rural/frappe-linter-template/issues)
- **GitHub Discussions**: [Ask questions](https://github.com/dhwani-rural/frappe-linter-template/discussions)
- **Email**: info@dhwani.org

## 📚 Additional Resources

- [Pre-commit Documentation](https://pre-commit.com/)
- [Ruff Documentation](https://docs.astral.sh/ruff/)
- [ESLint Documentation](https://eslint.org/)
- [Prettier Documentation](https://prettier.io/)
- [Conventional Commits](https://www.conventionalcommits.org/)

## 🎉 Next Steps

After setting up your development environment:

1. **Read the documentation**: Start with `README.md` and `docs/`
2. **Explore the configuration**: Understand the linting and formatting rules
3. **Make your first commit**: Test the pre-commit hooks
4. **Customize for your project**: Update project-specific information
5. **Start developing**: Begin building your Frappe application!

---

Happy coding! 🚀
