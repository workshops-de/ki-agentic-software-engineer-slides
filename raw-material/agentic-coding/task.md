---
layout: cover
class: text-center
---

# 🎯 Workshop: Agentic Coding

No-code automation with Claude Code GitHub Actions

---
layout: default
---

# Workshop: Build Your First Agent 🛠️

## Goal
Set up **Claude Code GitHub Actions** to automatically handle Pull Requests, issues, and code reviews with simple @claude mentions.

<div class="mt-8 grid grid-cols-3 gap-4">
<div class="p-4 bg-blue-100 rounded-lg">
<strong>⏱️ Time:</strong> 30 minutes
</div>
<div class="p-4 bg-green-100 rounded-lg">
<strong>🎯 Level:</strong> Beginner
</div>
<div class="p-4 bg-purple-100 rounded-lg">
<strong>🛠️ Tools:</strong> GitHub, Claude Code
</div>
</div>

---
layout: two-cols-header
layoutClass: gap-16
---

# Step 1: Repository Setup

::left::

## Create Test Repository
1. Create new repository: `claude-automation-demo`
2. Initialize with README and sample code
3. Enable Issues and Pull Requests
4. Add some basic project files

```bash
# Initialize repository structure
mkdir src tests docs
echo "# Claude Automation Demo" > README.md

# Create sample code for Claude to work with
cat > src/utils.js << 'EOF'
function calculateTotal(items) {
    return items.reduce((sum, item) => sum + item.price, 0);
}

function formatCurrency(amount) {
    return '$' + amount.toFixed(2);
}

module.exports = { calculateTotal, formatCurrency };
EOF
```

::right::

## Configure Repository
1. **Settings** → **Actions** → Enable workflows
2. **Settings** → **Branches** → Add protection for `main`  
3. **Settings** → **General** → Allow auto-merge
4. **Issues** → Create issue template (optional)

```markdown
<!-- .github/ISSUE_TEMPLATE/bug_report.md -->
**Bug Description:**
Brief description of the issue

**Steps to Reproduce:**
1. Step one
2. Step two

**Expected vs Actual:**
What should happen vs what actually happens

@claude Please analyze and fix this issue
```

---
layout: default
---

# Step 2: Install Claude Code 

## Quick Installation with Claude CLI

```bash
# In your Claude Code terminal
/install-github-app

# Follow the prompts:
# 1. Select your repository
# 2. Install Claude GitHub App
# 3. Configure API key secret
# 4. Create workflow file
```

## Manual Setup Alternative

If CLI install doesn't work:

1. **Install Claude GitHub App**: Visit https://github.com/apps/claude
2. **Add API Secret**: Settings → Secrets → `ANTHROPIC_API_KEY` 
3. **Create workflow file**:

```yaml
# .github/workflows/claude.yml
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

---
layout: default
---

# Step 3: Configure Claude's Behavior

## Create CLAUDE.md Configuration

```markdown
<!-- CLAUDE.md -->
# Claude Configuration for Development

## Project Context
This is a JavaScript utility library for e-commerce calculations.

## Coding Standards
- Use ES6+ features where appropriate
- Include JSDoc comments for all functions
- Follow naming conventions: camelCase for functions/variables
- Add error handling for edge cases

## Testing Requirements
- Write Jest tests for all new functions
- Achieve minimum 80% code coverage
- Include both positive and negative test cases
- Test edge cases (empty arrays, null values, etc.)

## Code Review Guidelines
- Check for security vulnerabilities
- Verify performance implications
- Ensure backward compatibility
- Validate error handling

## Auto-fix Permissions
- Fix linting errors automatically
- Update outdated dependencies (patch versions only)
- Format code according to Prettier config
- Generate missing JSDoc comments

## Communication Style
- Be concise but thorough in PR comments
- Explain reasoning behind suggestions
- Provide code examples when helpful
- Use emojis sparingly but effectively
```

---
layout: default
---

# Step 4: Test Basic Automation 🧪

## Test 1: Issue Analysis
Create a new issue:

```markdown
**Title:** Bug: calculateTotal function doesn't handle empty arrays

**Description:** 
The calculateTotal function crashes when passed an empty array.
It should return 0 instead of throwing an error.

Steps to reproduce:
1. Call calculateTotal([])
2. Function throws TypeError

@claude Please analyze this issue and create a fix
```

## Test 2: Code Review  
Create a simple PR:

1. Create new branch: `feature/add-validation`
2. Make a small change to `src/utils.js`
3. Create PR with description: "@claude Please review this change"

## Test 3: Manual Trigger
Comment on any issue or PR:
```
@claude Generate comprehensive tests for the utils.js file
```

---
layout: default
---

# Step 5: Advanced Workflow Setup 📈

## Multi-Stage Automation

```yaml
name: Advanced Claude Workflow
on:
  issues:
    types: [opened, labeled]
  pull_request:
    types: [opened, synchronize]

jobs:
  issue-triage:
    if: github.event_name == 'issues'
    runs-on: ubuntu-latest
    steps:
      - uses: anthropics/claude-code-action@v1
        with:
          anthropic_api_key: ${{ secrets.ANTHROPIC_API_KEY }}
          prompt: |
            Analyze this issue and:
            1. Classify as bug/feature/question
            2. Estimate complexity (1-5 scale)  
            3. Suggest appropriate labels
            4. Create implementation plan if it's a feature
          claude_args: "--max-turns 3"
          
  pr-review:
    if: github.event_name == 'pull_request'
    runs-on: ubuntu-latest
    steps:
      - uses: anthropics/claude-code-action@v1
        with:
          anthropic_api_key: ${{ secrets.ANTHROPIC_API_KEY }}
          prompt: |
            Review this PR focusing on:
            - Code quality and best practices
            - Security implications
            - Performance considerations
            - Test coverage adequacy
          claude_args: "--max-turns 5"
```

---
layout: default
---

# Step 6: Specialized Prompts & Use Cases 🎯

<div class="grid grid-cols-2 gap-8">
<div>

## Security-Focused Review
```yaml
- uses: anthropics/claude-code-action@v1
  with:
    anthropic_api_key: ${{ secrets.ANTHROPIC_API_KEY }}
    prompt: |
      SECURITY REVIEW: Analyze for:
      - Input validation vulnerabilities
      - SQL injection possibilities
      - XSS attack vectors
      - Authentication bypasses
      - Data exposure risks
      
      Rate security level 1-10 and provide fixes.
```

</div>
<div>

## Documentation Generator
```yaml
- uses: anthropics/claude-code-action@v1
  with:
    anthropic_api_key: ${{ secrets.ANTHROPIC_API_KEY }}
    prompt: |
      Generate comprehensive documentation:
      - API reference for all public functions
      - Usage examples with code samples
      - Installation and setup instructions
      - Contributing guidelines
      - Update README.md accordingly
```

</div>
</div>

## Scheduled Maintenance
```yaml
on:
  schedule:
    - cron: "0 6 * * 1"  # Every Monday at 6 AM
jobs:
  weekly-maintenance:
    runs-on: ubuntu-latest
    steps:
      - uses: anthropics/claude-code-action@v1
        with:
          anthropic_api_key: ${{ secrets.ANTHROPIC_API_KEY }}
          prompt: |
            Weekly maintenance check:
            1. Review open issues and PRs
            2. Check for outdated dependencies
            3. Run security audit
            4. Generate status report
            5. Create maintenance tasks if needed
```

---
layout: default
---

# Validation & Results 📊

## Success Criteria ✅

After completing the workshop, you should have:

- [ ] **Claude GitHub App** installed and configured
- [ ] **Basic workflow** responding to @claude mentions  
- [ ] **CLAUDE.md** configuration customizing behavior
- [ ] **Test issue** automatically analyzed and fixed
- [ ] **Test PR** automatically reviewed with feedback
- [ ] **Advanced workflow** for different event types

## Expected Outcomes

<div class="grid grid-cols-2 gap-8">
<div>

### Immediate Benefits
- **Instant code reviews** on every PR
- **Automatic issue analysis** and solutions
- **Zero custom code** to maintain
- **Consistent quality** across all changes

</div>
<div>

### Advanced Capabilities  
- **Proactive maintenance** via scheduled runs
- **Security scanning** on every change
- **Documentation generation** automatically
- **Multi-stage approval** workflows

</div>
</div>

---
layout: fact
---

# 🎯 Achievement Unlocked!

<div class="text-xl">

✅ **No-Code Agent**: Built without writing custom code  
✅ **Event-Driven**: Responds to GitHub events automatically  
✅ **Customizable**: Behavior configured via CLAUDE.md  
✅ **Scalable**: Works for any repository size  
✅ **Secure**: Uses GitHub's built-in permissions  

</div>

<div class="text-center mt-8 p-4 bg-green-100 rounded-lg">
<strong>Result:</strong> Professional AI automation in 30 minutes! 🚀
</div>

---
layout: center
class: text-center
---

# 🎉 Your First Agent is Live!

## Ready to explore Claude Code's advanced features?

### Next Step: Deep dive into Claude Code capabilities

<div class="text-sm mt-8 opacity-75">
From basic automation to sophisticated workflows
</div>