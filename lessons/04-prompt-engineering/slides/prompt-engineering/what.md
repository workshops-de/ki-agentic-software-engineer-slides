---
layout: sub-section
---

# Core Techniques

Five patterns that transform how you communicate with AI.

---
layout: two-cols-header
layoutClass: gap-4
---

# Role-Based Prompting

::left::

Give the AI a professional identity to shape its vocabulary and focus.

- Uses domain-specific terminology
- Frames responses at the right expertise level
- Keeps answers focused on the technical domain

::right::

<WindowMockup codeblock title="prompt.txt">

```text
You are a senior Vue.js architect
specializing in TypeScript.

Your task is to review this component
and explain your design decisions.
```

</WindowMockup>

---
layout: two-cols-header
layoutClass: gap-4
---

# Instruction Prompting

::left::

Provide complete, specific instructions with all requirements upfront.

- Reduces hallucinations through clear constraints
- Produces repeatable, deterministic results
- Covers all requirements without back-and-forth

::right::

<WindowMockup codeblock title="prompt.txt">

```text
Create a Vue component using Composition API:
- Use <script setup lang="ts">
- Define prop "user": { id: number; name: string }
- Add Vitest unit tests
- Return: (1) .vue file, (2) test file
```

</WindowMockup>

---
layout: two-cols-header
layoutClass: gap-4
---

# Chain-of-Thought

::left::

Ask the AI to reason step by step before providing a solution.

- Reveals where logic could break down
- Better results on complex, multi-step problems
- You understand the "why" behind the solution

::right::

<WindowMockup codeblock title="prompt.txt">

```text
Explain step by step how you would
validate props in a Vue component.

First think about the design,
then typing, then the test.
```

</WindowMockup>

---
layout: two-cols-header
layoutClass: gap-4
---

# Few-Shot Learning

::left::

Provide examples in the prompt to teach the AI your desired pattern or style.

- AI learns your conventions directly from examples
- Matches your team's style without lengthy descriptions
- Shows what "good" looks like concretely

::right::

<WindowMockup codeblock title="prompt.txt">

```vue
<!-- Example 1 -->
<script setup lang="ts">
const count = ref(0);
</script>

<!-- Now create a component that
     tracks selected items in a list,
     following this exact pattern. -->
```

</WindowMockup>

---
layout: two-cols-header
layoutClass: gap-4
---

# Iterative Prompting

::left::

Build complex results through multiple focused refinement steps.

- Higher quality through incremental improvements
- Easier to catch and fix errors per step
- Feels like pair programming with AI

::right::

<WindowMockup codeblock title="prompt.txt">

```text
Step 1: "Write a Vue login form component"
→ Basic component generated

Step 2: "Add TypeScript props and validation"
→ Typed and validated

Step 3: "Add Vitest unit tests"
→ Fully tested
```

</WindowMockup>
