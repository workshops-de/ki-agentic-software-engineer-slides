## Overview

Set up the foundational Claude Code GitHub Actions workflow that will serve as the basis for agentic automation. No custom code required — pure configuration.

## Prerequisites

- GitHub account
- Anthropic API key
- Claude Code CLI or access to Claude

---

## Steps

### 1. Create Test Repository

Create a new repository (e.g. `claude-automation-demo`) with basic structure:

```bash
mkdir src tests docs
echo "# Claude Automation Demo" > README.md
```

Add sample code for Claude to work with (e.g. a simple utility module).

### 2. Install Claude Code Integration

- Run `/install-github-app` in Claude Code
- Or manually: [Install Claude GitHub App](https://github.com/apps/claude)
- Add `ANTHROPIC_API_KEY` to repository secrets

### 3. Create Workflow File

Add `.github/workflows/claude.yml`:

```yaml
name: Claude Code
on:
  issue_comment:
    types: [created]
  pull_request_review_comment:
    types: [created]
jobs:
  claude:
    runs-on: ubuntu-latest
    steps:
      - uses: anthropics/claude-code-action@v1
        with:
          anthropic_api_key: ${{ secrets.ANTHROPIC_API_KEY }}
```

### 4. Configure CLAUDE.md (Optional)

Create `CLAUDE.md` to define coding standards, testing requirements, and review guidelines.

### 5. Test

Create an issue and mention `@claude` with a simple request. Verify the workflow runs and responds.

---

## Success Criteria

- [ ] Claude GitHub App installed and configured
- [ ] Basic workflow responding to @claude mentions
- [ ] Test issue or PR comment triggers the workflow
- [ ] CLAUDE.md in place (optional)
