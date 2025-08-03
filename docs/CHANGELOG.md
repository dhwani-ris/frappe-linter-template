# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

### Added
- Initial template repository setup
- Comprehensive pre-commit configuration
- Multi-language linting support (Python, JavaScript, Vue, SCSS)
- GitHub Actions CI/CD pipeline
- VS Code settings and extensions
- Documentation templates

### Changed
- N/A

### Deprecated
- N/A

### Removed
- N/A

### Fixed
- N/A

### Security
- N/A

## [0.1.0] - 2025-01-XX

### Added
- Initial release of Frappe Linter Template
- Pre-commit hooks configuration with:
  - trailing-whitespace removal
  - merge conflict detection
  - AST validation
  - JSON/TOML/YAML validation
  - debug statement removal
  - Ruff for Python linting and formatting
  - Prettier for code formatting
  - ESLint for JavaScript linting
- Python project configuration (pyproject.toml)
- Node.js project configuration (package.json)
- Comprehensive documentation structure
- Contributing guidelines
- Changelog template
- MIT License

---

## Version History

- **0.1.0**: Initial template release with basic linting and formatting tools

## Release Process

1. **Version Bump**: Update version in `pyproject.toml` and `package.json`
2. **Changelog**: Add new version section to this file
3. **Tag**: Create git tag with version number
4. **Release**: Create GitHub release with changelog notes

## Contributing to Changelog

When adding new features or fixes, please add entries to the [Unreleased] section:

- **Added**: New features
- **Changed**: Changes in existing functionality
- **Deprecated**: Soon-to-be removed features
- **Removed**: Removed features
- **Fixed**: Bug fixes
- **Security**: Vulnerability fixes

Use the following format:
```markdown
### Added
- New feature description

### Fixed
- Bug fix description
```
