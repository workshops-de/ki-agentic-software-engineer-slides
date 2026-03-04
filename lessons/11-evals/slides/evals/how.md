---
layout: sub-section
---

# web-codegen-scorer

---
layout: center
---

# web-codegen-scorer

Evidence-based testing for your AI setup

- **CLI tool** — Checks how good your prompts perform
- **Generates apps** — 5 apps in parallel by default
- **Runs tests** — Axe and Lighthouse tests
- **Fixes errors** — 2 attempts to fix build errors
- **Generates reports** — Compare performance over time

---
layout: center
---

# Announced at the Angular AI event in October 2025.

<br>

<div style="display: flex; justify-content: center;">
  <Youtube id="uFdxw4Se-A8" />
</div>

---
layout: image
image: lessons/11-evals/slides/evals/assets/web-codegen-scorer.png
backgroundSize: 90%
---

---
layout: default
---

# Configuration

<WindowMockup codeblock title="config.mjs">

```js{*|4|5|6|7|1,8|9|10|*}
import { getBuiltInRatings } from 'web-codegen-scorer';

export default {
  displayName: 'agentic-coding-scorer',
  skipInstall: true,
  clientSideFramework: 'angular',
  sourceDirectory: 'project',
  ratings: [...getBuiltInRatings()],
  generationSystemPrompt: './<your-instructions>.md',
  executablePrompts: ['./example-prompts/**/*.md'],
};
```

</WindowMockup>

---
layout: default
---

# Execution

<WindowMockup codeblock title="Bash">

```bash{*|1|3|5|7|*}
export GEMINI_API_KEY="..🤖.."

web-codegen-scorer eval --env=angular-example

web-codegen-scorer report

web-codegen-scorer run --prompt=<generated-app> --env=<path>
```

</WindowMockup>

https://github.com/GregOnNet/web-codegen-scorer-playground.git

---
layout: image-right
backgroundSize: 100%
image: /lessons/11-evals/slides/evals/assets/eval-report-overview.png
---

# Report: Overall Score

- **Score band** — Excellent (98–100%), Great (85–97%), Good (71–84%), Poor (0–70%)
- **Dimensions** — Build, Tests, Runtime, Security, Accessibility with pass/fail counts
- **Usage** — Token usage and execution stats for each run

---
layout: image-right
backgroundSize: 100%
image: /lessons/11-evals/slides/evals/assets/eval-ai-summary.png
---

# Report: AI Summary

- **Common failures** — Highlights main gaps (e.g. missing UI controls, deprecated CSS)
- **Low-hanging fruit** — Concrete, easy improvements
- **Per-app score** — Score plus medium-impact breakdown (UI, valid CSS, etc.)

---
layout: image-right
backgroundSize: 100%
image: /lessons/11-evals/slides/evals/assets/eval-detailed-checks.png
---

# Report: Detailed Checks

- **Impact tiers** — High (build, safety, runtime), Medium (quality, UI, CSS), Low
- **LLM-rated checks** — Code quality and UI assessed by the model
- **Clear rationale** — Partial passes with explanations for deductions

---
layout: image-right
backgroundSize: 100%
image: /lessons/11-evals/slides/evals/assets/eval-lighthouse.png
---

# Report: Lighthouse Integration

- **Performance** — FCP, LCP, TBT, Speed Index, TTI
- **Best practices** — HTML doctype, charset, source maps
- **Unified view** — Lighthouse data inside the eval report
