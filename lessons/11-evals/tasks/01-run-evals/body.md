- **Start your eval-journey** by cloning the playground from GitHub
    ```bash
    git clone https://github.com/GregOnNet/web-codegen-scorer-playground.git
    cd web-codegen-scorer-playground
    npm install
    ```
---
- **Provide your API-Key** for Anthrophic's models
  ```bash
  export ANTHROPIC_API_KEY="sk-ant-..."
  ```
---
- **Run your 1st evaluation**
  ```bash
  npm run eval.opus
  ```
---
- *Study* the report carefully
  ```bash
  npm run report
  ```
---
- **Run more** evaluations
  1. Improve your `AGENTS.md` to score better results
  1. Improve the `goal-tracker`-prompt to score better results
  1. Remove the prompt-filter in `package.json > eval.opus` to execute multiple prompts in parallel
