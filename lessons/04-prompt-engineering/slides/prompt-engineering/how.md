---
layout: default
---

# A Repeatable 4-Step Process

Apply this structure to any AI request.

<div class="grid grid-cols-4 gap-4 mt-8">
  <div class="p-4 bg-blue-100 rounded-lg text-center">
    <div class="text-2xl font-bold text-blue-800 mb-2">1</div>
    <h3 class="font-bold text-blue-800">Define Role</h3>
    <p class="text-sm text-blue-700">Who should the AI be?</p>
  </div>
  <div class="p-4 bg-green-100 rounded-lg text-center">
    <div class="text-2xl font-bold text-green-800 mb-2">2</div>
    <h3 class="font-bold text-green-800">Set Context</h3>
    <p class="text-sm text-green-700">What does it need to know?</p>
  </div>
  <div class="p-4 bg-purple-100 rounded-lg text-center">
    <div class="text-2xl font-bold text-purple-800 mb-2">3</div>
    <h3 class="font-bold text-purple-800">Give Instructions</h3>
    <p class="text-sm text-purple-700">What should it do?</p>
  </div>
  <div class="p-4 bg-orange-100 rounded-lg text-center">
    <div class="text-2xl font-bold text-orange-800 mb-2">4</div>
    <h3 class="font-bold text-orange-800">Define Output</h3>
    <p class="text-sm text-orange-700">How should it respond?</p>
  </div>
</div>

---
layout: two-cols-header
layoutClass: gap-4
---

# Techniques in Practice

::left::

**Chain-of-Thought for Debugging**

_Problem: Component not re-rendering_

Prompt: _"Think step by step about Vue's reactivity system and why this component might not update when the prop changes."_

→ AI explains the issue and provides a targeted fix.

::right::

**Few-Shot for Refactoring**

_Problem: Convert Options API to Composition API_

Prompt: Show 2–3 example conversions, then: _"Now convert the following using the same pattern."_

→ AI follows your exact style and conventions.

---
layout: two-cols-header
layoutClass: gap-4
---

# Best Practices

::left::

**Do This**

- Be specific and detailed
- Provide context and examples
- Define the expected output format
- Combine multiple techniques
- Iterate and refine step by step

::right::

**Avoid This**

- Vague, single-sentence prompts
- No codebase context or background
- Accepting the first output as final
- Expecting AI to guess requirements
- One massive prompt for complex tasks

::bottom::

<Callout type="info">
Prompt engineering is systematic communication — the same clarity that makes good documentation makes great prompts.
</Callout>
