---
layout: sub-section
---

# How to Implement

No-code automation with Claude Code GitHub Actions

---
layout: two-cols-header
layoutClass: gap-4
---

# Pattern 1: Event-Driven

::left::

**Issue → @claude → Solution**

Triggers on `issue_comment` or `pull_request_review_comment`. A simple @claude mention starts the agent.

::right::

<WindowMockup codeblock title=".github/workflows/claude.yml">

```yaml
name: Claude Code
on:
  issue_comment:
    types: [created]
jobs:
  claude:
    runs-on: ubuntu-latest
    steps:
      - uses: anthropics/claude-code-action@v1
        with:
          anthropic_api_key: ${{ secrets.ANTHROPIC_API_KEY }}
```

</WindowMockup>

---
layout: two-cols-header
layoutClass: gap-4
---

# Pattern 2: Scheduled Automation

::left::

**Proactive maintenance** — daily reviews, security scans, documentation updates.

::right::

<WindowMockup codeblock title=".github/workflows/daily.yml">

```yaml
name: Daily Code Review
on:
  schedule:
    - cron: '0 9 * * *'
jobs:
  daily-review:
    runs-on: ubuntu-latest
    steps:
      - uses: anthropics/claude-code-action@v1
        with:
          anthropic_api_key: ${{ secrets.ANTHROPIC_API_KEY }}
          prompt: |
            Review yesterday's commits.
            Create summary report and issues if needed.
```

</WindowMockup>

---
layout: two-cols-header
layoutClass: gap-4
---

# Pattern 3: Multi-Stage Workflows

::left::

**Chain jobs** — analyze requirement → implement feature. Each job can run Claude with a specific prompt.

::right::

<WindowMockup codeblock title=".github/workflows/pipeline.yml">

```yaml
jobs:
  analyze-requirement:
    if: contains(github.event.issue.labels.*.name, 'feature')
    steps:
      - uses: anthropics/claude-code-action@v1
        with:
          prompt: 'Analyze feature and create implementation plan'

  implement-feature:
    needs: analyze-requirement
    steps:
      - uses: anthropics/claude-code-action@v1
        with:
          prompt: 'Implement feature with tests'
```

</WindowMockup>

---
layout: default
---

# Quick Win: First Agent in 5 Minutes

1. **Install Claude App** via `/install-github-app` (2 min)
2. **Add API Key** to repository secrets (1 min)
3. **Create basic workflow** file (1 min)
4. **Test with @claude** mention in an issue (1 min)

<Callout type="important">
Zero custom code — pure configuration. CLAUDE.md defines behavior.
</Callout>
