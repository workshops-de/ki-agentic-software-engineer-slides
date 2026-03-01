---
layout: section
---

# How to implement Agentic Coding?

No-code automation with Claude Code GitHub Actions

---
layout: default
---

# The Agentic Development Stack 📚

<div class="grid grid-cols-3 gap-6">
<div>

## 🤖 AI Layer
- **Claude Code**: Advanced reasoning
- **GitHub Actions**: Event triggers
- **@claude mentions**: Simple activation
- **CLAUDE.md**: Behavior config

</div>
<div>

## 🔧 Integration Layer
- **GitHub API**: Repository access
- **Webhooks**: Real-time events
- **PR/Issue comments**: Communication
- **Workflow dispatch**: Manual triggers

</div>
<div>

## 🏗️ Platform Layer
- **GitHub**: Repository & Actions
- **Claude Code Action**: Pre-built automation
- **Anthropic API**: AI processing
- **No custom code**: Pure configuration

</div>
</div>

---
layout: two-cols-header
layoutClass: gap-16
---

# Pattern 1: Event-Driven Claude

::left::

## Issue → @claude → Solution

```yaml {*}{maxHeight:'200px'}
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
          # Responds to @claude mentions automatically
```

::right::

## What Claude Does
- **Analyzes** the issue context
- **Reads** relevant code files
- **Identifies** the root cause
- **Creates** a pull request with fix
- **Tests** the solution
- **Documents** the changes

*All triggered by a simple @claude mention!*

---
layout: two-cols-header
layoutClass: gap-16
---

# Pattern 2: Scheduled Automation 🔄

::left::

```yaml
name: Daily Code Review
on:
  schedule:
    - cron: "0 9 * * *"
jobs:
  daily-review:
    runs-on: ubuntu-latest
    steps:
      - uses: anthropics/claude-code-action@v1
        with:
          anthropic_api_key: ${{ secrets.ANTHROPIC_API_KEY }}
          prompt: |
            Review yesterday's commits and create a summary report.
            Identify any potential issues or improvements.
            Create an issue with your findings if needed.
          claude_args: "--max-turns 3"
```

::right::

## Proactive Agent Benefits
- **Daily code health checks**
- **Automated security scanning**
- **Documentation updates**
- **Dependency maintenance**
- **Performance monitoring**

---
layout: two-cols-header
layoutClass: gap-16
---

# Pattern 3: Multi-Stage Workflows 🤝

```yaml {*}{maxHeight:'450px'}
name: Feature Development Pipeline
on:
  issues:
    types: [opened, labeled]

jobs:
  analyze-requirement:
    if: contains(github.event.issue.labels.*.name, 'feature')
    runs-on: ubuntu-latest
    steps:
      - uses: anthropics/claude-code-action@v1
        with:
          anthropic_api_key: ${{ secrets.ANTHROPIC_API_KEY }}
          prompt: "Analyze feature request and create implementation plan"

  implement-feature:
    needs: analyze-requirement
    runs-on: ubuntu-latest
    steps:
      - uses: anthropics/claude-code-action@v1
        with:
          anthropic_api_key: ${{ secrets.ANTHROPIC_API_KEY }}
          prompt: "Implement feature with tests and documentation"
```

::right::

**Step 4: Configure Claude's Behavior**
```markdown
<!-- CLAUDE.md -->
# Claude Configuration

## Coding Standards
- Use TypeScript for all new code
- Follow ESLint configuration
- Write tests for new functions
- Update documentation

## Review Criteria
- Security: Check for vulnerabilities
- Performance: Identify bottlenecks
- Maintainability: Ensure clean code
- Testing: Verify test coverage

## Auto-fix Guidelines
- Fix lint errors automatically
- Update dependencies safely
- Regenerate documentation
- Create meaningful commit messages
```

---
layout: default
---

# Advanced Claude Prompting 🎯

## Effective Workflow Prompts

```yaml
- uses: anthropics/claude-code-action@v1
  with:
    anthropic_api_key: ${{ secrets.ANTHROPIC_API_KEY }}
    prompt: |
      ROLE: Senior Full-Stack Engineer

      CONTEXT: This is a React/Node.js e-commerce application

      TASK: Review this PR for:
      1. Security vulnerabilities
      2. Performance implications
      3. Code quality issues
      4. Test coverage gaps

      CONSTRAINTS:
      - Follow our CLAUDE.md guidelines
      - Ensure backward compatibility
      - Maintain existing API contracts

      OUTPUT: Detailed review comments with specific suggestions
    claude_args: "--max-turns 5 --model claude-3-5-sonnet-20241022"
```

---
layout: two-cols-header
layoutClass: gap-8
---

# Trigger Patterns 🎛️

::left::

**Issue-Based Automation**
```yaml
on:
  issues:
    types: [opened, labeled]
```

**PR-Based Reviews**
```yaml {*}{maxHeight:'120px'}
on:
  pull_request:
    types: [opened, synchronize]
```

::right::

**Manual Triggers**

```yaml
on:
  workflow_dispatch:
    inputs:
      task: [refactor, document, optimize]
```

**Triggers**: On-demand execution

**Use for**: Maintenance, optimization, documentation updates
**Agent action**: Perform specific tasks based on user selection


---
layout: default
---

# Error Handling & Fallbacks 🛡️

```yaml {*}{maxHeight:'450px'}
jobs:
  claude-with-fallback:
    runs-on: ubuntu-latest
    steps:
      - name: Try Claude Analysis
        id: claude
        continue-on-error: true
        uses: anthropics/claude-code-action@v1
        with:
          anthropic_api_key: ${{ secrets.ANTHROPIC_API_KEY }}
          claude_args: "--max-turns 3"

      - name: Fallback to Manual Review
        if: failure()
        uses: actions/github-script@v6
        with:
          script: |
            github.rest.issues.createComment({
              owner: context.repo.owner,
              repo: context.repo.repo,
              issue_number: context.issue.number,
              body: '⚠️ Claude analysis failed. Manual review requested.'
            })

      - name: Success Notification
        if: success()
        run: echo "✅ Claude analysis completed successfully"
```

---
layout: default
---

# 🎯 Quick Win: First Agent in 5 minutes

1. **Install Claude App** via `/install-github-app` (2 min)
2. **Add API Key** to repository secrets (1 min)
3. **Create basic workflow** file (1 min)
4. **Test with @claude** mention in an issue (1 min)

<div class="mt-8 p-4 bg-blue-100 rounded-lg text-center">
<strong>Result:</strong> Instant AI automation with zero custom code!
</div>

---
layout: center
class: text-center
---

# 🚀 Ready for Claude Code Specifics?

## Now let's dive deep into Claude Code features

<div class="text-sm mt-8 opacity-75">
From basic patterns to advanced workflows
</div>
