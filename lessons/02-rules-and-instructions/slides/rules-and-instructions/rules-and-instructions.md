---
layout: section
---

# Rules & Instructions

## Fine grained task delegation

---
layout: why
---

# Why this topic matters

Developers face the challenge of working with AI while ensuring quality; rules with the right structure make delegation easier and more effective.

- Each developer faces the challenge to work with AI, but the quality needs to be ensured
- Developers must understand how to delegate tasks they normally do manually
- Rules are very easy and with the correct structure they can help a lot

---
layout: little-what
---

# What is it?

An instruction provides reusable and precise context to a model to improve the quality of the LLM's output.

---
layout: sub-section
---

# Vendor-specific files

---
layout: two-cols-header
layoutClass: gap-x-2
---

# Vendor-specific files

::left::

- **.cursorrules**, **claude.md**, Copilot instructions — same concept, differ in detail
- Messy to maintain if a team uses different setups
- Manageable especially with AI support

::right::

<WindowMockup codeblock title=".cursor/rules/ts-style.mdc" padding="2rem">

```md
---
description: Use TypeScript strict mode
globs: ['**/*.ts', '**/*.tsx']
---

Prefer explicit types over inference for public APIs.
Use functional patterns where possible.
```

</WindowMockup>

---
layout: sub-section
---

# AGENTS.md

---
layout: two-cols-header
layoutClass: gap-4
---

# Emerging standard: AGENTS.md

::left::

- Open format: [agents.md](https://agents.md/) — many vendors support it
- Typical sections: project overview, build and test commands, code style guidelines, testing instructions, security considerations

::right::

<WindowMockup codeblock title="AGENTS.md" padding="1rem">

```md
# AGENTS.md

## Setup commands

- Start dev: `pnpm dev`
- Run tests: `pnpm test`

## Code style

- TypeScript strict mode
- Single quotes, no semicolons
```

</WindowMockup>

::bottom::
<Callout type="warning">
Claude: no native support yet; <code>CLAUDE.md</code> can reference <code>AGENTS.md</code> to make it work.
</Callout>

---
layout: default
---

# AGENTS.md — what to put in

- **Project overview** — what the repo does, main entry points
- **Build and test commands** — how to install, run, test
- **Code style guidelines** — formatting, naming, patterns
- **Testing instructions** — how to run and extend tests
- **Security considerations** — secrets, permissions, deployment

---
layout: two-cols-header
layoutClass: gap-4
---

# Nested AGENTS.md

::left::

- Multiple AGENTS.md files can live in one project
- The agent reads the **nearest** file in the directory tree (closest takes precedence)
- Example: OpenAI repo has 88 AGENTS.md files; each subproject can ship tailored instructions

::right::

<WindowMockup codeblock title="project/" padding="1rem">

```text
project/
├── AGENTS.md           # Root: global context
├── shipment/
│   └── AGENTS.md       # Domain: shipment
├── payment/
│   └── AGENTS.md       # Domain: payment
└── inventory/
    └── AGENTS.md       # Domain: inventory
```

</WindowMockup>

::bottom::
<Callout type="info">
Nearest AGENTS.md to the edited file wins — each domain gets tailored instructions.
</Callout>

---
layout: sub-section
---

# Scope of rules

---
layout: default
---

# Where rules apply

- **Global** — loaded for the whole workspace (e.g. .cursor/rules)
- **Per chat** — mention a rule file by name (e.g. @filename) in the conversation
- **Commands** — many vendors support **Commands** (e.g. `/create-pr`, `/interview`, `/commit`): one instruction per concrete task
- Goal: fine-grained control and custom workflows

---
layout: default
---

# Evolution: from “god rule” to task-oriented

- **Before:** One big file with everything — coding guidelines, architecture, conventions
- **Now:** Think in **tasks** and steps; improve the development process with focused rules
- Use Commands for: **interview → develop → test → finalise** — each step has its own instruction and puts the developer in the loop to review and tune the prompt

---
layout: default
---

# Workflow - Dev-In-The-Loop

```mermaid
flowchart LR
  A[interview.md] --> Dev((👩‍💻 Developer))
  Dev --> B[develop.md]
  B --> Dev
  Dev --> C[test.md]
  C --> Dev
  Dev --> D[finalise.md]
  D --> Dev
```

<Callout type="tip" v-click>
Delegate repeating tasks. You are the expert. The agent offers opportunities. Some of them might be a surprise.
</Callout>

<!--
| Step      | Purpose                           |
| --------- | --------------------------------- |
| Interview | Gather requirements, clarify      |
| Develop   | Implement with clear instructions |
| Test      | Run checks, fix failures          |
| Finalise  | Commit, PR, review                |

Each rule file or command supports one step and keeps the developer in the loop.
-->

---
layout: sub-section
---

# ⚠️ Beware generated rules!

## You need to own the rules.

---
layout: two-cols-header
layoutClass: gap-2
---

# Two sides of the same coin

::left::

**Generated rules** — productivity impact

<div v-click>

1. **~28% longer** runtime (vs. repos with hand-crafted instructions)
2. **~17% more** output tokens (less focused, higher cost)
3. **REASON**: Replicate existing content and amplify it; **no vision**, no sense of what is already misused

</div>

::right::

**Your own rules** (e.g. AGENTS.md)

<div v-click>

- Research: agents **~28% faster**, **~17% fewer** output tokens
- Make rules your own; describe the **best version** of your project
- **Put yourself in the loop**

</div>

::bottom::

Sources: [arXiv:2601.20404](https://arxiv.org/abs/2601.20404) · [elmd\_](https://x.com/elmd_/status/2025976479276806294)

---
layout: default
---

# Tip

- Make rules **your own**
- Instruct agents to be **very critical** about the provided content
- Describe the **best version** of your project instead of taking existing things for granted
- **Put yourself in the loop**

<br><br>

<Callout type="important" v-click>
Rules are typically loaded once when the agent is initialized. If you edit a rule file, prompt the agent to read that file again (e.g. by @-mentioning it).
</Callout>

---
layout: task
---

# Demo follows
