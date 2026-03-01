---
layout: section
---

# What is Agentic Coding?

Concepts, Patterns and Architecture

---
layout: default
---

# Definition: Agentic Coding 🎯

<div class="text-lg mb-8">

**Agentic Coding** is a paradigm where autonomous **software agents** 
independently execute, analyze, and optimize code-related tasks.

</div>

## Core Characteristics

- **🧠 Autonomous**: Agents make independent decisions
- **🔄 Reactive**: Respond to events and changes  
- **🎯 Goal-oriented**: Work towards defined objectives
- **🔗 Collaborative**: Communicate with other agents
- **📊 Context-aware**: Fully understand code context

---
layout: two-cols-header
layoutClass: gap-16
---

# Agent vs. Tool 🆚

::left::

## 🛠️ Traditional Tool
```yaml
Input: "Fix this bug"
Process: Manual steps required
Output: Partial solution
Human: Reviews and completes
```

- Requires explicit instructions
- Limited context understanding
- Single-purpose functionality
- Human oversight needed

::right::

## 🤖 Agentic System
```yaml
Input: "Repository has issues"
Process: Agent analyzes automatically
Output: Complete solution + PR
Human: Reviews final result
```

- Interprets intent and context
- Multi-step problem solving
- Learns from patterns
- End-to-end automation


---
layout: default
---

# Agent Types in Development 🎭

<div class="grid grid-cols-2 gap-8">
<div>

## Code Agents
- **Code Generator**: Writes new code
- **Refactor Agent**: Optimizes existing code  
- **Test Agent**: Generates and runs tests
- **Security Agent**: Scans for vulnerabilities

</div>
<div>

## Process Agents  
- **PR Agent**: Creates and reviews Pull Requests
- **Issue Agent**: Classifies and resolves issues
- **Deploy Agent**: Automates deployments
- **Monitor Agent**: Monitors system health

</div>
</div>

---
layout: two-cols-header
layoutClass: gap-16
---

# Reactive vs. Proactive Agents

::left::

## ⚡ Reactive Agents
- React to **Events**
- GitHub Webhooks
- CI/CD Pipeline Failures
- Issue Creation
- PR Submissions

```typescript
// Event-driven
webhook.on('pull_request', async (event) => {
  await codeReviewAgent.analyze(event.data);
});
```

::right::

## 🔮 Proactive Agents
- **Scheduled** Analysis
- Code Quality Monitoring  
- Dependency Updates
- Performance Optimization
- Security Scanning

```typescript
// Schedule-driven
cron.schedule('0 2 * * *', async () => {
  await securityAgent.scanAllRepos();
});
```


---
layout: fact
---

# 5 Levels of Agentic Autonomy

<div class="flex flex-col items-center">

  <div class="text-1xl text-left max-w-xl">

  **Level 0**: Manual - Everything manual  
  **Level 1**: Assisted - Tool supports  
  **Level 2**: Partial - Agent executes sub-tasks  
  **Level 3**: Conditional - Agent decides in known cases  
  **Level 4**: High - Agent acts autonomously with human oversight  
  **Level 5**: Full - Fully autonomous agents  

  </div>

  <div class="mt-8 text-lg opacity-75 text-left max-w-xl">
    Today: Level 2-3 | Future: Level 4-5
  </div>

</div>