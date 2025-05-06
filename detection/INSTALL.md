# Installation Guide for LLM07 Detection Tools

This guide will help you set up the tools needed to run the LLM07 System Prompt Leakage detection pipeline.

## Prerequisites

- Python 3.8+
- pip (Python package manager)
- A UNIX-like environment (Linux or macOS) to run shell scripts

## Installation Steps

### 1. Install Python Dependencies

```bash
# Create a virtual environment (recommended)
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install requirements
pip install -r requirements.txt
```

### 2. Install Semgrep

[Semgrep](https://semgrep.dev/) is a lightweight static analysis tool used to find code patterns.

```bash
# Install via pip
pip install semgrep==1.36.0

# Verify installation
semgrep --version
```

### 3. Install Open Policy Agent (OPA)

[OPA](https://www.openpolicyagent.org/) is a policy engine for validating and filtering data.

#### macOS Installation

```bash
# Using Homebrew
brew install opa

# Verify installation
opa version
```

#### Linux Installation

```bash
curl -L -o opa https://openpolicyagent.org/downloads/latest/opa_linux_amd64
chmod 755 opa
sudo mv opa /usr/local/bin/opa

# Verify installation
opa version
```

#### Windows Installation

Download the latest release from the [OPA GitHub Releases page](https://github.com/open-policy-agent/opa/releases).

### 4. Verify Setup

Test that everything is working correctly:

```bash
# Make the detection script executable
chmod +x run_detection.sh

# Run a test scan on the vulnerable application
./run_detection.sh ../vulnerable-app
```

You should see output indicating that the scan is being performed, and a detection report will be generated.

## Troubleshooting

### Common Issues

1. **Semgrep not found**
   - Make sure you've activated your virtual environment
   - Reinstall with `pip install semgrep==1.36.0`

2. **OPA not found**
   - Make sure the OPA binary is in your PATH
   - On Linux/macOS, verify with `which opa`

3. **Permission denied when running script**
   - Make the script executable with `chmod +x run_detection.sh`

4. **Python AST conversion errors**
   - Make sure you're running Python 3.8 or higher
   - Install additional dependencies if needed with `pip install ast2json`

For any other issues, please check the detailed logs in the detection report or consult the documentation for the specific tool. 