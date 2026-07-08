# Usage Guide

## Basic Usage

### Create a New Project

```bash
# Simple usage
hatch my_project

# Specify a base directory
hatch my_project ~/projects

# Current directory
hatch my_project .
```

### What Gets Created

```
my_project/
├── src/                          # Main source code directory
├── tests/                        # Unit & integration tests
├── docs/                         # Documentation
├── scripts/                      # Utility scripts
├── .github/
│   └── workflows/
│       └── ci.yml                # GitHub Actions CI/CD
├── .claudeignore                 # Token-optimized file exclusions
├── .gitmessage                   # Commit message template
├── README.md                     # Project README
├── requirements.txt              # Python dependencies
└── .git/                         # Git repository
    └── hooks/
        └── pre-commit            # Security pre-commit hook
```

## Initial Setup

After creating a project:

```bash
cd my_project

# Create virtual environment
python3 -m venv venv

# Activate it
source venv/bin/activate          # Linux/macOS
# or
venv\Scripts\activate             # Windows

# Install dependencies
pip install -r requirements.txt
```

## Development Workflow

### Running Tests

```bash
# Run all tests
python3 -m pytest tests/ -v

# Run with coverage
python3 -m pytest tests/ -v --cov=src/

# Run specific test file
python3 -m pytest tests/test_module.py -v
```

### Code Quality

```bash
# Format code with Black
black src/ tests/

# Lint with Flake8
flake8 src/ tests/

# Sort imports
isort src/ tests/
```

### Git Workflow

The project includes automated Git hooks:

```bash
# Make changes
echo "print('Hello')" > src/main.py

# Stage changes
git add src/main.py

# Pre-commit hook runs automatically:
# ✓ Checks for secrets
# ✓ Validates Python syntax
# ✓ Removes trailing whitespace

# Commit (uses message template)
git commit
```

#### Commit Message Template

The `.gitmessage` template provides conventional commit format:

```
# <type>(<scope>): <subject>
# 
# Example: feat(auth): add API key validation
#
# Types: feat, fix, docs, style, refactor, perf, test, chore, ci
```

## Using with Claude / AI

### Token Optimization

The `.claudeignore` file reduces token usage:

```bash
# DON'T do this (scans entire home directory)
cd ~
claude "Implement feature X"

# DO this (scans only project)
cd my_project
claude "Implement feature X"
```

### Recommended AI Workflow

```bash
cd my_project

# Ask Claude to understand structure
claude "What's in the src/ directory?"

# Get help with implementation
claude "Create a basic HTTP server in src/server.py"

# Test the code
python3 -m pytest tests/

# Ask for improvements
claude "Add error handling to src/server.py"
```

## CI/CD with GitHub Actions

The project includes a GitHub Actions workflow (`.github/workflows/ci.yml`):

```yaml
# Automatically runs on:
# - Push to main or develop
# - Pull requests to main

# Steps:
# 1. Checkout code
# 2. Setup Python (3.9, 3.10, 3.11, 3.12)
# 3. Install dependencies
# 4. Lint with flake8
# 5. Run tests with coverage
```

### Running Tests Locally

```bash
# Simulate GitHub Actions
python3 -m pytest tests/ -v --cov=src/

# View coverage report
coverage report -m
coverage html
open htmlcov/index.html
```

## Project Structure Best Practices

### src/ Directory

```python
# src/main.py - Entry point
# src/utils.py - Utility functions
# src/config.py - Configuration
# src/api/ - API modules
# src/db/ - Database modules
```

### tests/ Directory

```python
# tests/test_utils.py - Tests for utils.py
# tests/test_api.py - Tests for API
# tests/fixtures/ - Test fixtures
# tests/integration/ - Integration tests
```

### scripts/ Directory

```bash
# scripts/setup.sh - Setup script
# scripts/deploy.sh - Deployment
# scripts/test.sh - Test runner
```

## Security Features

### Pre-commit Hooks

The scaffolder includes security checks:

```bash
# Prevents committing:
✓ API keys (ANTHROPIC_API_KEY, github_token)
✓ Passwords and secrets
✓ Database URLs
✓ Broken Python syntax
✓ Trailing whitespace
```

### Bypass Hooks (Not Recommended)

```bash
# Skip pre-commit hooks (dangerous!)
git commit --no-verify

# Better: Fix the issue
git reset HEAD <file>
# Edit file to remove secret
git add <file>
git commit
```

## Troubleshooting

### Project Already Exists

```bash
# Error: Project 'my_project' already exists!

# Solution: Use different name
hatch my_other_project

# Or remove existing
rm -rf my_project
hatch my_project
```

### Invalid Project Name

```bash
# Error: Project name must be alphanumeric (hyphens/underscores OK)

# Valid: my_project, my-project, MyProject
# Invalid: my project, my.project, my@project

hatch my_valid_project
```

### Git Not Found

```bash
# Error: Could not initialize Git

# Solution: Install Git
apt-get install git        # Debian/Ubuntu
brew install git           # macOS
choco install git          # Windows
```

### Tests Not Running

```bash
# Error: pytest not found

# Solution: Install dev dependencies
pip install -r requirements.txt
pip install pytest pytest-cov

# Then run
python3 -m pytest tests/ -v
```

## Advanced Usage

### Custom Requirements

Edit `requirements.txt` after scaffolding:

```bash
cd my_project

# Add new dependency
echo "numpy>=1.21.0" >> requirements.txt

# Install it
pip install -r requirements.txt
```

### Custom Hooks

Edit `.git/hooks/pre-commit` to add additional checks:

```bash
# Add custom validation
echo "# Your custom checks" >> .git/hooks/pre-commit
chmod +x .git/hooks/pre-commit
```

### Custom Workflow

Edit `.github/workflows/ci.yml` for custom CI:

```yaml
- name: Custom step
  run: |
    python3 -m mypy src/
    python3 -m pylint src/
```

---

For more information, see:
- [Installation Guide](INSTALL.md)
- [Contributing Guide](CONTRIBUTING.md)
