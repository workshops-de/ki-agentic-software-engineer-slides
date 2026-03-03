# requirement-context

When the user invokes this command, restore an existing requirement from a file or a GitHub issue so it can be used in context for development.

## Instructions

1. **Ask for source**
   Ask the user how they want to load the requirement:
   - From a file path (e.g. `docs/REQUIREMENT-*.md`)
   - From a GitHub issue (provide issue ID)

2. **GitHub issue ID**
   - If the user provides an issue ID (e.g. `#42` or `42`), fetch that issue using the GitHub CLI (`gh issue view <id>`) or API.
   - If no issue ID is provided, list open issues from the repository:
     - Run `gh issue list --state open` (or equivalent)
     - Show ID and title of each issue
     - Ask: *"Which issue should I load? Please provide the issue number."*

3. **Local file**
   If the user provides a file path, read the file and parse the requirement structure.

4. **Load and present**
   Once the requirement is found:
   - Read and summarize the requirement (user story, acceptance criteria, files to modify)
   - Provide it clearly in the conversation so it can be used by `/requirement-develop` or other commands
