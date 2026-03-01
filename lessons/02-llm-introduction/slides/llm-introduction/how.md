---
layout: sub-section
---

# LLM Failure Modes

Understanding why AI goes wrong — and how to compensate

---
layout: default
---

# Five structural phenomena to know

- Time Capsule
- Lost in the Middle
- Hallucination
- Primacy/Recency Bias
- Instruction Interference

---
layout: two-cols-header
layoutClass: gap-4
---

# Time Capsule Problem

::left::

Models are **snapshots** of the world at training time. They cannot know new facts unless given explicit context.

**Example:**

Ask about the latest framework version → model describes an older release and extrapolates incorrectly.

::right::

**Mitigations**

<WindowMockup codeblock title="strategies.ts">

```typescript {1-3|5-7|9-11}
// 1. Retrieval-Augmented Generation
const docs = await fetchDocs('vue@3.5');
const answer = llm.generate(docs + prompt);

// 2. Date-aware prompting
prompt = `As of ${new Date().toISOString()},
          using Vue ${version}...`;
```

</WindowMockup>

::bottom::
<Callout type="warning">
Never assume an LLM knows current library APIs, recent deprecations, or newly released tools.
</Callout>

---
layout: two-cols-header
layoutClass: gap-4
---

# Hallucinations

::left::

The model doesn't lie — it **fills in missing information statistically**. If a plausible-sounding API name fits the pattern, it will produce it.

- Confidently invents package names
- Generates realistic but non-existent methods
- No built-in truth verification

<Callout type="warning">
Always verify imports and API names against real documentation before trusting generated code.
</Callout>

::right::

**Mitigations**

<WindowMockup codeblock title="prevention.ts">

```typescript {1-3|5-8|10-13}
// 1. Ask for documentation sources
"Provide docs links for any API you use"

// 2. Automated verification
await runTests(generatedCode)
await typeCheck(generatedCode)
await lintCode(generatedCode)

// 3. Explicit constraints
"Only use APIs from Vue 3.4 official docs.
 Do not invent new methods.
 Verify each import exists."
```

</WindowMockup>

---
layout: two-cols-header
layoutClass: gap-4
---

# Lost in the Middle

::left::

Attention is strongest at the **start and end** of the context window. Content in the middle receives less attention and may be effectively ignored.

**Example:** Give a 500-line file, ask about line 250 — the model may miss it entirely.

<Callout type="warning">
Place the most critical information at the beginning or end of your prompt — never bury it in the middle.
</Callout>

::right::

**Mitigations**

<WindowMockup codeblock title="chunking.ts">

```typescript {1-4|6-9|11-14}
// 1. Chunk and summarize
const chunks = splitIntoChunks(file, 100);
const summaries = chunks.map(summarize);
const answer = process(summaries);

// 2. Hierarchical prompting
const outline = extractOutline(content);
const section = getRelevantSection(outline);
const result = processWithContext(section);

// 3. Explicit anchors
prompt = `In section 3 (lines 200–300)
          you will find the auth logic.
          Focus only on that section.`;
```

</WindowMockup>

---
layout: two-cols-header
layoutClass: gap-x-sm
---

# Primacy/Recency Bias

::left::

**Problem**

The model pays most attention to the very start and very end of the context. Critical constraints buried in the middle get ignored.

<WindowMockup>

```typescript
// Critical constraint buried mid-context
Setup... setup... setup...
Critical constraint  ← lost
More setup... final instruction
```

</WindowMockup>

::right::

**Solution**

Repeat critical constraints at both the start and end of your prompt.

<WindowMockup>

```typescript
// Repeat constraints at start and end
CRITICAL: Main requirement
...context...
REMEMBER: Main requirement
```

</WindowMockup>

---
layout: two-cols-header
layoutClass: gap-x-sm
---

# Instruction Interference

::left::

**Problem**

Later instructions can override earlier constraints — even system-level ones.

<WindowMockup>

```typescript
// System: "You are a Vue 3 expert"
// User:   "Write React code"
// → Model switches to React
```

</WindowMockup>

::right::

**Solution**

Reinforce constraints explicitly around the user request.

<WindowMockup>

```typescript
const prompt = `
  Remember: Vue 3 Composition API only.
  ${userRequest}
  Use Vue 3 Composition API only.
`;
```

</WindowMockup>
