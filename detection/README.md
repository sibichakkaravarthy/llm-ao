# LLM07 - System Prompt Leakage Detection

This directory contains tools and rules for detecting vulnerabilities related to system prompt leakage in LLM applications.

## Overview

System prompt leakage occurs when an LLM application inadvertently reveals internal instructions, constraints, or sensitive information embedded in system prompts. This detection mechanism helps identify common patterns that lead to such vulnerabilities.

## Tools Included

**Semgrep Rules**: Static analysis rules that identify dangerous code patterns

## Vulnerability Patterns Detected

- Direct string concatenation of system prompts with user inputs
- Lack of input validation for prompt injection attempts
- Missing response filtering for system information leakage
- Insecure prompt construction patterns
- Embedding sensitive information in system prompts

## Usage

### Prerequisites

- Semgrep (`pip install semgrep`)

### Individual Tool Usage

#### Semgrep Rules

```bash
cd detection
semgrep --config semgrep-rules/rules.yaml ../vulnerable-app
```

## Customizing Rules

- Add new Semgrep patterns in the `semgrep-rules` directory
- Modify the detection script to include additional checks

## Interpreting Results

The detection report will highlight:
- Code locations with potential vulnerabilities
- Severity levels for each finding
- Recommended remediation steps
- Explanation of the vulnerability pattern detected 