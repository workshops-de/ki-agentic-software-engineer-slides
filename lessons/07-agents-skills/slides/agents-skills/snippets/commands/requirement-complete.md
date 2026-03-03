# requirement-complete

When the user invokes this command, finalize the current requirement implementation and prepare it for commit.

## Instructions

1. **Format check**
   Run Prettier format check on the codebase (e.g. `pnpm exec prettier --check .` or equivalent). Fix any formatting issues if the check fails.

2. **Commit**
   Create a commit with the staged/ready changes.

3. **Commit message**
   Use semantic commit messages:
   - **Format:** `<type>(<scope>): <subject>`
   - **Types:** `feat`, `fix`, `docs`, `style`, `refactor`, `test`, `chore`
   - **Scope:** Optional, e.g. component name or area (e.g. `footer`, `meta`)
   - **Subject:** Concise, lowercase start, no period at end
   - **Example:** `feat(footer): update conference dates to October 2026`

Keep the message concise and clean. Avoid redundant phrasing.
