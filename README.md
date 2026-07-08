# God Mode Scaffolder 🦆

An AI-ready Python project bootstrapper that creates production-ready scaffolding with security hooks, CI/CD pipelines, and token-optimized structure for Claude integration.

## Features

✨ **Full Project Structure** — src, tests, docs, scripts, and .github workflows  
🔐 **Security Hooks** — Pre-commit checks for secrets, syntax, and whitespace  
📦 **Dependencies** — Sensible defaults with pinned versions  
🚀 **CI/CD Ready** — GitHub Actions workflow for Python testing  
🎯 **.claudeignore** — Token-optimized file exclusions  
📝 **Commit Templates** — Structured conventional commits  

## Installation

```bash
# Download the script
wget https://raw.githubusercontent.com/tangleroot013/God_Mode_Scaffolder/main/hatch.py
chmod +x hatch.py

# Install to PATH
sudo mv hatch.py /usr/local/bin/

# Or create an alias
alias hatch='python3 /path/to/hatch.py'
```

## Quick Start

```bash
# Create a new project
hatch my_project

# Enter and set up environment
cd my_project
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt

# Start coding
python3 -m pytest tests/ -v
```

## What Gets Created

```
my_project/
├── src/                    # Main source code
├── tests/                  # Unit & integration tests
├── docs/                   # Documentation
├── scripts/                # Utility scripts
├── .github/
│   └── workflows/
│       └── ci.yml          # GitHub Actions CI pipeline
├── .claudeignore           # Token-aware file exclusions
├── .gitmessage             # Commit message template
├── README.md               # Project README
└── requirements.txt        # Python dependencies
```

## Security Features

The scaffolder automatically installs pre-commit hooks that prevent:

- 🚫 **Secrets** — Detects API keys, tokens, passwords
- 🚫 **Syntax Errors** — Validates Python files before commit
- 🚫 **Whitespace Pollution** — Blocks trailing whitespace

## Files in This Repository

- **hatch.py** — Main scaffolder script
- **README.md** — This file
- **examples/** — Example scaffolded projects (optional)

## Development

```bash
# Test the scaffolder
python3 hatch.py test_project

# Verify structure
tree test_project/

# Clean up
rm -rf test_project/
```

## License

MIT — Create freely, share generously! 🦆

---

*Built with 🦆 by Carter the Duck Developer*
