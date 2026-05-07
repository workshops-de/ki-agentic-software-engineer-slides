## AGENTS.md

- **Add an `AGENTS.md`** at the root of your project.
  - Reuse the existing `ARCHITECTURE.md` to provide context.

---

- **Consider splitting** `AGENTS.md` into several files:
  - One under `src/` with shared technical details.
  - One in the book feature folder with guidance that applies only to that feature.

## Instruction

> Cursor loads `AGENTS.md` automatically. The following steps should be run only when you mention this instruction in the chat.

- **Given** we already had the AI implement a full feature.

---

- **The quality** may be okay, but you spot issues that will make the code hard to maintain, for example:
  - Lots of repetition
  - Side effects in constructors
  - Bloated templates

---

- **Review the AI output** and list the problematic parts.

---

- **Come up with better approaches**, such as:
  - Global error handling
  - Clear patterns for logic and templates

---

- **Capture your findings** in a `REFACTORING.md` file.

---

- **Instruct your coding agent** to apply the refactoring to the latest code you generated.

## Success criteria

- [ ] Root `AGENTS.md` exists and references or aligns with `ARCHITECTURE.md` (optional splits under `src/` and the book feature as needed).
- [ ] You documented concrete maintenance issues and target patterns in `REFACTORING.md`.
- [ ] You drove the agent from chat to apply the refactor and reviewed the resulting changes.
