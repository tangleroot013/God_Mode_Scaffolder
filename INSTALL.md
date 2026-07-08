# Installation Guide

## Quick Install (Recommended)

### 1. Download and Install

```bash
# Clone the repository
git clone https://github.com/tangleroot013/God_Mode_Scaffolder.git
cd God_Mode_Scaffolder

# Copy to a convenient location
cp hatch.py ~/.local/bin/
chmod +x ~/.local/bin/hatch.py
```

### 2. Add to PATH

Choose one method:

**Option A: Add ~/.local/bin to PATH (persistent)**
```bash
echo 'export PATH="$HOME/.local/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
```

**Option B: Create an alias**
```bash
echo "alias hatch='python3 ~/.local/bin/hatch.py'" >> ~/.bashrc
source ~/.bashrc
```

**Option C: Use with full path**
```bash
python3 ~/.local/bin/hatch.py my_project
```

### 3. Verify Installation

```bash
# Test with alias method
hatch my_test_project

# Or with full path
python3 ~/.local/bin/hatch.py my_test_project

# Verify structure
ls -la my_test_project/
```

## System-Wide Installation (Linux/macOS)

```bash
# Install to /usr/local/bin (may require sudo)
sudo cp hatch.py /usr/local/bin/hatch
sudo chmod +x /usr/local/bin/hatch

# Use globally
hatch my_project
```

## Windows Installation

1. Download `hatch.py` to your desired location
2. Use the full path with Python:
   ```cmd
   python C:\path\to\hatch.py my_project
   ```
3. Or create a batch file `hatch.bat`:
   ```batch
   @echo off
   python C:\path\to\hatch.py %*
   ```

## Docker Installation

```dockerfile
FROM python:3.11-slim

RUN mkdir -p /usr/local/bin
COPY hatch.py /usr/local/bin/hatch
RUN chmod +x /usr/local/bin/hatch

WORKDIR /workspace
ENTRYPOINT ["python3", "/usr/local/bin/hatch"]
```

Build and use:
```bash
docker build -t hatch .
docker run -v $(pwd):/workspace hatch my_project
```

## Development Installation

For contributing to the scaffolder:

```bash
# Clone the repo
git clone https://github.com/tangleroot013/God_Mode_Scaffolder.git
cd God_Mode_Scaffolder

# Create dev environment
python3 -m venv venv
source venv/bin/activate
pip install -r requirements-dev.txt

# Test changes
python3 hatch.py test_project
```

## Troubleshooting

### "command not found: hatch"
- Verify `~/.local/bin` is in your PATH: `echo $PATH`
- Add to PATH manually: `export PATH="$HOME/.local/bin:$PATH"`
- Use full path: `python3 ~/.local/bin/hatch.py my_project`

### Permission denied
- Make script executable: `chmod +x hatch.py`
- Or run explicitly: `python3 hatch.py my_project`

### Python not found
- Ensure Python 3.7+ is installed: `python3 --version`
- Adjust shebang if using different Python path

## Uninstall

```bash
# Remove from bin directory
rm ~/.local/bin/hatch.py

# Remove alias (if added to bashrc)
# Edit ~/.bashrc and remove the alias line
sed -i "/alias hatch=/d" ~/.bashrc

# Or system-wide
sudo rm /usr/local/bin/hatch
```

---

Happy scaffolding! 🦆
