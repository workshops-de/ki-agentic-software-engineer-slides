---
layout: section
---

# 🛠️ Practical Application
## Understanding failure modes and solutions

---
layout: default
---

# ⚠️ Common Systemic Phenomena

<div class="overflow-x-auto">
<table class="w-full text-sm">
<thead>
<tr class="bg-gray-100 dark:bg-gray-800">
<th class="p-3 text-left">Phenomenon</th>
<th class="p-3 text-left">What happens</th>
<th class="p-3 text-left">Root cause</th>
</tr>
</thead>
<tbody>
<tr class="border-b">
<td class="p-3 font-semibold">Time Capsule Problem</td>
<td class="p-3">Knowledge frozen at training time</td>
<td class="p-3">Static training data</td>
</tr>
<tr class="border-b">
<td class="p-3 font-semibold">Lost in the Middle</td>
<td class="p-3">Forgets mid-context information</td>
<td class="p-3">Attention drop-off</td>
</tr>
<tr class="border-b">
<td class="p-3 font-semibold">Hallucination</td>
<td class="p-3">Makes up plausible but false info</td>
<td class="p-3">Probability fill-in</td>
</tr>
<tr class="border-b">
<td class="p-3 font-semibold">Primacy/Recency Bias</td>
<td class="p-3">Early or late info dominates</td>
<td class="p-3">Attention weighting</td>
</tr>
<tr>
<td class="p-3 font-semibold">Instruction Interference</td>
<td class="p-3">Later prompts override roles</td>
<td class="p-3">Context overwrite</td>
</tr>
</tbody>
</table>
</div>

---
layout: two-cols
---

# ⏳ The Time Capsule Problem

<div class="text-base space-y-3">

**Models are snapshots of the world at training time**

They can't "know" new facts unless:
- Retrained on new data
- Connected to external tools
- Given context explicitly

</div>

<div class="bg-red-50 dark:bg-red-900/20 p-4 rounded-lg mt-4">
<strong>Example:</strong><br/>
Ask about Vue 3.5 features<br/>
→ Model describes Vue 3.2<br/>
→ Extrapolates incorrectly
</div>

::right::

<div class="flex flex-col justify-center h-full">

**✅ Solutions:**

```typescript {1-3|5-7|9-11}
// 1. Retrieval-Augmented Generation
const context = await fetchDocs('Vue 3.5')
const response = llm.generate(context + prompt)

// 2. Tool/API lookups
const version = await getLatestVersion('vue')
const features = await getFeatures(version)

// 3. Date-aware prompting
prompt = `As of ${new Date()},
          using Vue ${version}...`
```

</div>

---
layout: default
---

# 🌀 Lost in the Middle

<div class="grid grid-cols-2 gap-6">

<div>
<h3 class="font-bold text-lg mb-3">The Problem:</h3>
<ul class="space-y-2">
<li>Strong attention to <strong>start and end</strong></li>
<li>Weak focus on <strong>middle sections</strong></li>
<li>Important details get lost</li>
</ul>

<div class="bg-yellow-50 dark:bg-yellow-900/20 p-4 rounded-lg mt-4">
<strong>Example:</strong><br/>
Give a 500-line file<br/>
→ Ask about line 250<br/>
→ Model might miss it entirely
</div>
</div>

<div>
<h3 class="font-bold text-lg mb-3">✅ Solutions:</h3>

```typescript {1-4|6-9|11-14}
// 1. Chunk and summarize
const chunks = splitIntoChunks(longFile, 100)
const summaries = chunks.map(summarize)
const response = process(summaries)

// 2. Hierarchical prompting
const outline = extractOutline(content)
const details = getRelevantSection(outline)
const result = processWithContext(details)

// 3. Clear anchors
prompt = `
In section 3 (lines 200-300),
you'll find the auth logic...`
```
</div>

</div>

---
layout: two-cols
layoutClass: gap-8
---

# 🎭 Hallucinations

<div class="text-base space-y-3">

**The model doesn't "lie"**
It **fills in missing info** statistically

- Confidently invents APIs
- Creates plausible libraries
- Generates realistic but wrong data
- No built-in "truth check"

</div>

<div class="bg-red-50 dark:bg-red-900/20 p-4 rounded-lg mt-4">
<strong>Real Example:</strong>
```javascript
// AI suggests:
import { useAsyncData } from '@vue/async'
// This package doesn't exist! 🚫
```
</div>

::right::

<div class="flex flex-col justify-center h-full">

**✅ Prevention Strategies:**

```typescript {1-3|5-8|10-13}
// 1. Ask for sources
"Provide documentation links
 for any APIs you use"

// 2. Verification tools
await runTests(generatedCode)
await typeCheck(generatedCode)
await lintCode(generatedCode)

// 3. Explicit constraints
"Only use APIs from Vue 3.4 docs.
 Do not invent new methods.
 Verify each import exists."
```

<div class="bg-green-50 dark:bg-green-900/20 p-4 rounded-lg mt-4">
💡 Always verify generated imports and APIs!
</div>

</div>

---
layout: default
---

# 🔄 Primacy & Recency Bias

<div class="bg-gradient-to-r from-blue-50 to-purple-50 dark:from-blue-900/20 dark:to-purple-900/20 p-6 rounded-xl mb-6">

**The model pays most attention to:**
1. 🎯 The very beginning (primacy)
2. 🎯 The very end (recency)
3. 😴 Less to the middle

</div>

<div class="grid grid-cols-2 gap-6">

<div>
<h4 class="font-bold mb-3">❌ Poor Structure:</h4>

```typescript
// Setup and context...
// Important config...
// Critical requirement ← Lost!
// More setup...
// Final instruction
```
</div>

<div>
<h4 class="font-bold mb-3">✅ Better Structure:</h4>

```typescript
// CRITICAL: Main requirement
// Supporting context...
// Details...
// REMEMBER: Main requirement
```
</div>

</div>

---
layout: two-cols
---

# 🎯 Instruction Interference

<div class="text-base space-y-3">

**Later prompts can override earlier context**

Common scenarios:
- System prompt gets ignored
- Role instructions forgotten
- Style guides overridden
- Constraints violated

</div>

<div class="bg-yellow-50 dark:bg-yellow-900/20 p-4 rounded-lg mt-4">
<strong>Example:</strong><br/>
System: "You are a Vue expert"<br/>
User: "Write React code"<br/>
→ Model switches to React
</div>

::right::

<div class="flex flex-col justify-center h-full">

**✅ Reinforcement Strategies:**

```typescript {1-4|6-10|12-15}
// 1. Repeat critical context
const prompt = `
Remember: Use Vue 3 Composition API
${userRequest}
Use Vue 3 Composition API only`

// 2. Structured prompts
const sections = {
  role: "Vue 3 developer",
  constraints: ["No React", "TypeScript"],
  task: userRequest
}

// 3. Validation checks
if (response.includes('React')) {
  regenerate(with_stronger_constraints)
}
```

</div>
