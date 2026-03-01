---
layout: cover
transition: slide-left
---

# What is Prompt Engineering?

<div class="pt-12">
  <span @click="$slidev.nav.next" class="px-2 py-1 rounded cursor-pointer" hover="bg-white bg-opacity-10">
    Press Space for next page <carbon:arrow-right class="inline"/>
  </span>
</div>

---
layout: center
---

# Definition

<div class="text-2xl mb-8">
  <strong>Prompt Engineering</strong> is the systematic design and optimization of inputs to AI models to achieve desired outputs
</div>

<div class="grid grid-cols-2 gap-8 mt-8">
  <div class="p-6 bg-blue-50 rounded-lg">
    <h3 class="text-xl font-bold mb-4 text-blue-800">Art</h3>
    <p class="text-blue-700">Creative communication with AI systems</p>
  </div>
  <div class="p-6 bg-green-50 rounded-lg">
    <h3 class="text-xl font-bold mb-4 text-green-800">Science</h3>
    <p class="text-green-700">Systematic, repeatable techniques</p>
  </div>
</div>

---
layout: center
---

# The 9 Core Techniques

<div class="grid grid-cols-3 gap-4 mt-8 text-sm">
  <div class="p-4 bg-purple-100 rounded-lg">
    <div class="font-bold text-purple-800 mb-2">🎭 Role-based</div>
    <p class="text-purple-700">Define AI's identity</p>
  </div>
  <div class="p-4 bg-blue-100 rounded-lg">
    <div class="font-bold text-blue-800 mb-2">🧩 Instruction</div>
    <p class="text-blue-700">Clear, specific tasks</p>
  </div>
  <div class="p-4 bg-green-100 rounded-lg">
    <div class="font-bold text-green-800 mb-2">🧠 Chain-of-Thought</div>
    <p class="text-green-700">Explicit reasoning</p>
  </div>
  <div class="p-4 bg-yellow-100 rounded-lg">
    <div class="font-bold text-yellow-800 mb-2">🧪 Few-Shot</div>
    <p class="text-yellow-700">Learn from examples</p>
  </div>
  <div class="p-4 bg-red-100 rounded-lg">
    <div class="font-bold text-red-800 mb-2">🔁 Iterative</div>
    <p class="text-red-700">Refine step by step</p>
  </div>
  <div class="p-4 bg-indigo-100 rounded-lg">
    <div class="font-bold text-indigo-800 mb-2">🧱 Chunking</div>
    <p class="text-indigo-700">Break into parts</p>
  </div>
  <div class="p-4 bg-pink-100 rounded-lg">
    <div class="font-bold text-pink-800 mb-2">📑 Schema</div>
    <p class="text-pink-700">Structured output</p>
  </div>
  <div class="p-4 bg-teal-100 rounded-lg">
    <div class="font-bold text-teal-800 mb-2">🧮 Multi-Pass</div>
    <p class="text-teal-700">Compare variants</p>
  </div>
  <div class="p-4 bg-orange-100 rounded-lg">
    <div class="font-bold text-orange-800 mb-2">🧰 Tool-Augmented</div>
    <p class="text-orange-700">Use real tools</p>
  </div>
</div>

---
layout: default
---

# 🎭 Role-Based Prompting

## Concept
Give the AI a professional identity to change its behavior and expertise level.

## Key Benefits
- **Precise vocabulary** - Uses domain-specific terms
- **Reduces creativity** - Stays focused on technical accuracy
- **Consistent tone** - Maintains professional standards

---
layout: default
---

## Example
```text
You are an experienced frontend architect
specializing in Vue 3 and TypeScript.

Your task is to structure code according
to best practices and briefly explain
your design decisions.
```

<div class="mt-4 p-4 bg-blue-50 rounded-lg">
  <p class="text-sm text-blue-700">
    <strong>Effect:</strong> AI responds with architectural thinking, not just code generation
  </p>
</div>

---
layout: default
---

# 🧩 Instruction Prompting

## Concept
Provide clear, complete instructions with specific conditions and goals.

## Key Benefits
- **Reduces hallucinations** - Clear constraints prevent made-up information
- **Deterministic results** - Same input produces similar output
- **Complete solutions** - Covers all requirements upfront

---
layout: default
---

## Example
```text
Create a Vue component using Composition API:
- Use <script setup lang="ts">
- Define prop "user" of type { id: number; name: string }
- Add unit tests using Vitest
- Return: (1) .vue file, (2) test file
```

<div class="mt-4 p-4 bg-green-50 rounded-lg">
  <p class="text-sm text-green-700">
    <strong>Effect:</strong> AI produces exactly what you need, nothing more, nothing less
  </p>
</div>

---
layout: default
---

# 🧠 Chain-of-Thought (CoT)

## Concept
Make the AI's reasoning process explicit by asking it to "think out loud."

## Key Benefits
- **Logical coherence** - Shows step-by-step reasoning
- **Better debugging** - You can see where logic breaks down
- **Complex problem solving** - Handles multi-step tasks better

---
layout: default
---

## Example
```text
Explain step by step how you would validate
props in a Vue component.

First think about the design, then typing,
then the test.

### Reasoning
[AI shows its thinking process]

### Solution
[AI provides the final code]
```

<div class="mt-4 p-4 bg-purple-50 rounded-lg">
  <p class="text-sm text-purple-700">
    <strong>Effect:</strong> You understand the "why" behind the solution
  </p>
</div>

---
layout: default
---
# 🧪 Few-Shot Learning

## Concept
Provide examples in the prompt to teach the AI the desired pattern or style.

## Key Benefits
- **Pattern recognition** - AI learns from concrete examples
- **Style consistency** - Matches your coding standards
- **Context understanding** - Shows what "good" looks like

---
layout: default
---

## Example
```vue
<!-- Example 1 -->
<template><button @click="count++">{{ count }}</button></template>
<script setup lang="ts">const count = ref(0)</script>

<!-- Example 2 -->
<template><input v-model="name" /></template>
<script setup lang="ts">const name = ref('')</script>

Now create a component that renders a list
and counts clicked items.
```

<div class="mt-4 p-4 bg-yellow-50 rounded-lg">
  <p class="text-sm text-yellow-700">
    <strong>Effect:</strong> AI follows your exact patterns and conventions
  </p>
</div>

---
layout: default
---

# 🔁 Iterative Prompting

## Concept
Don't do everything in one prompt—improve results through multiple refinement steps.

## Key Benefits
- **Higher quality** - Each iteration improves the output
- **Fewer hallucinations** - Can catch and fix errors
- **Collaborative feel** - Like pair programming with AI

---
layout: default
---

## Example
```text
1. "Write a Vue component for a login form"
   → AI generates basic component

2. "Please add typed props and unit tests"
   → AI adds TypeScript and tests

3. "Add Storybook documentation"
   → AI adds comprehensive docs
```

<div class="mt-4 p-4 bg-red-50 rounded-lg">
  <p class="text-sm text-red-700">
    <strong>Effect:</strong> Builds complex solutions incrementally
  </p>
</div>

---
layout: default
---

# 🧱 Chunking & Context Management

## Concept
Break large inputs into smaller, logical parts to prevent context loss.

## Key Benefits
- **Focused attention** - AI processes one thing at a time
- **Prevents context loss** - Avoids "Lost in the Middle" problem
- **Better results** - Each chunk gets full attention

---
layout: default
---

## Example
```text
First analyze the imports and list dependencies.
Next, review the component definition for best practices.
Finally, write an optimized version.
```

<div class="mt-4 p-4 bg-indigo-50 rounded-lg">
  <p class="text-sm text-indigo-700">
    <strong>Effect:</strong> AI maintains focus throughout large codebases
  </p>
</div>

---
layout: default
---

# 📑 Schema & Format Prompting

## Concept
Force structured output using specific formats (JSON, Markdown, tables).

## Key Benefits
- **Automated processing** - Easy to parse and use programmatically
- **Consistent structure** - Same format every time
- **Tool integration** - Works well with MCP and other tools

---
layout: default
---

## Example
```json
{
  "component": "<script setup>...</script>",
  "tests": "...",
  "docs": "..."
}
```

<div class="mt-4 p-4 bg-pink-50 rounded-lg">
  <p class="text-sm text-pink-700">
    <strong>Effect:</strong> Output is ready for automated processing
  </p>
</div>

---
layout: default
---

# 🧮 Self-Consistency / Multi-Pass

## Concept
Generate multiple solutions and compare them to find the best approach.

## Key Benefits
- **Quality improvement** - Best solution emerges from comparison
- **Reduced review effort** - AI does the evaluation
- **Better reasoning** - Shows different approaches

---
layout: default
---

## Example
```text
Create 3 versions of the component using
different design patterns.

Explain which one is most maintainable
and why.
```

<div class="mt-4 p-4 bg-teal-50 rounded-lg">
  <p class="text-sm text-teal-700">
    <strong>Effect:</strong> AI provides multiple perspectives and chooses the best
  </p>
</div>

---
layout: default
---

# 🧰 Tool-Augmented Prompting

## Concept
Use real tools and APIs instead of relying on AI's knowledge alone.

## Key Benefits
- **Avoids hallucinations** - Uses real data and results
- **Accurate validation** - Real tool outputs, not guesses
- **Integration ready** - Works with existing toolchains

---
layout: default
---

## Example
```text
Check the following code with ESLint.
Then run Vitest and summarize the results.
```

<div class="mt-4 p-4 bg-orange-50 rounded-lg">
  <p class="text-sm text-orange-700">
    <strong>Effect:</strong> AI uses real tools for validation and testing
  </p>
</div>

---
layout: center
---

# The Prompt Engineering Mindset

<div class="grid grid-cols-2 gap-8 mt-8">
  <div class="p-6 bg-blue-50 rounded-lg">
    <h3 class="text-xl font-bold mb-4 text-blue-800">Think Like a Teacher</h3>
    <ul class="text-left space-y-2 text-blue-700">
      <li>Provide clear context</li>
      <li>Give concrete examples</li>
      <li>Explain the "why"</li>
      <li>Check for understanding</li>
    </ul>
  </div>
  <div class="p-6 bg-green-50 rounded-lg">
    <h3 class="text-xl font-bold mb-4 text-green-800">Think Like a Manager</h3>
    <ul class="text-left space-y-2 text-green-700">
      <li>Define clear objectives</li>
      <li>Set measurable criteria</li>
      <li>Provide feedback loops</li>
      <li>Iterate for improvement</li>
    </ul>
  </div>
</div>

<div class="mt-8 p-6 bg-gray-100 rounded-lg">
  <p class="text-lg font-semibold text-center">
    Prompt engineering is systematic communication with AI systems
  </p>
</div>
