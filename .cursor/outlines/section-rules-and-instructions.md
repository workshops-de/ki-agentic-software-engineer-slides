# Section outline: Rules & Instructions

**Subtitle:** Fine grained task delegation

---

## 1. section

- Title: Rules & Instructions
- Subtitle: Fine grained task delegation

---

## 2. why

- Key message: Developers face the challenge of working with AI while ensuring quality; rules with the right structure make delegation easier and more effective.
- Bullet points / narrative:
  - Each developer faces the challenge to work with AI, but the quality needs to be ensured.
  - Developers must understand how to delegate tasks they normally do manually.
  - Rules are very easy and with the correct structure they can help a lot.

---

## 3. little-what

- One-sentence primer: An instruction provides reusable and precise context to a model to improve the quality of the LLM's output.

---

## 4. Content slides (in order)

_Note: `sub-section` = cover/divider slide only (topic title). Put all content on a separate slide with a content layout (default, two-cols, etc.)._

**Vendor-specific files**

- **sub-section**: Vendor-specific files (cover only).
- **default** or **two-cols**: Content — .cursor-rules, claude.md, Copilot instructions; same concept, differ in detail; messy to maintain if team uses different setups, but manageable especially with AI.

**AGENTS.md**

- **sub-section**: AGENTS.md (cover only).
- **default** or **two-cols**: Content — emerging standard (https://agents.md/); most vendors support it; sections: project overview, build and test commands, code style guidelines, testing instructions, security considerations; Claude: no native support yet, but CLAUDE.md can reference AGENTS.md.
- **default**: Nested AGENTS.md — multiple files in a project; agent reads the nearest file in the directory tree (closest takes precedence); example: OpenAI repo has 88 AGENTS.md files; each subproject can ship tailored instructions.
- **default** (possibly multiple slides): AGENTS.md examples for the topics above (overview, build/test, code style, testing, security) — split across slides to avoid overloading one.

**Scope of rules**

- **sub-section**: Scope of rules (cover only).
- **default** or **two-cols**: Content — can be loaded globally; can be mentioned in chat per file name (@filename); many vendors support Commands for concrete tasks (e.g. create PR, create commit, interview) — reference with `/your-command`; goal: fine-grained control and custom workflows.

**Beware generated rules**

- **sub-section**: Beware generated rules (cover only).
- **default**: Content — research: generated rules can decrease productivity (replicate existing, amplify it; no vision, no sense of what is already misused). Sources: tweet (https://x.com/elmd_/status/2025976479276806294); Cornell/arXiv (https://arxiv.org/abs/2601.20404) — AGENTS.md associated with lower median runtime (~28.64%) and reduced output tokens (~16.58%).

**Tip**

- **default**: Make rules your own; instruct agents to be very critical about the provided content; describe the best version of your project instead of taking existing things for granted; put yourself in the loop.

---

## 5. Visuals for visual learners

- **Visual 1 — File structure:** Project with domains (e.g. shipment, payment, …), each with its own AGENTS.md; show directory tree so “nearest AGENTS.md wins” is clear. Suggested layout: **default** (Mermaid or markdown-style tree) or **image-right**.
- **Visual 2 — Evolution:** From “god rule” (one big file with everything: coding guidelines, architecture) to task-oriented thinking and improving the development process. Suggested layout: **default** or **two-cols** (before vs after) or **image-left** / **image-right**.
- **Visual 3 — Workflow example:** Rule files/commands for: interview → develop → test → finalise; each file fulfils a step and puts the developer in the loop to review and tune the prompt. Suggested layout: **default** (list or Mermaid flow) or **image-right**.

---

## 6. Optional

- **task:** Task slide only — state that a **Demo follows** (no exercise content).
- **what-if:** (none)
- **ask-me-anything:** (none)
