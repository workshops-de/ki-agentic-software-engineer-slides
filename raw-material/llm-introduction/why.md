---
layout: cover
---

# 🧠 How a Large Language Model Works
## A practical introduction for software developers

---
layout: center
---

# 🎯 Goal of this session

<div class="text-xl">

- Understand **how LLMs process and generate text**
- Learn what "tokens," "attention," and "transformers" mean
- See where LLMs **fail and why**
- Build intuition for **working with AI effectively**

</div>

---
layout: default
---

# 💡 Why care about how LLMs work?

<div class="text-lg space-y-4">

We interact with them daily — but **they don't "think" like humans**

Knowing their mechanics helps you:
- Write better prompts that get results
- Debug weird or unexpected outputs
- Design realistic expectations for AI tools
- Understand when to trust (or not trust) AI suggestions
- Build better AI-powered applications

</div>

---
layout: two-cols
layoutClass: gap-16
---

# 🚀 The AI Revolution in Development

<div class="text-base space-y-3">

**What's changed:**
- Code generation at scale
- Natural language to code
- Intelligent debugging assistance
- Documentation automation
- Test generation

**What hasn't:**
- Need for human judgment
- Understanding business logic
- Creative problem solving
- System architecture decisions

</div>

::right::

<div class="flex items-center justify-center h-full">
<img src="https://images.unsplash.com/photo-1677442136019-21780ecad995?w=500" alt="AI Development" class="rounded-lg shadow-xl" />
</div>

---
layout: fact
---

# 70%
of developers use AI tools daily

<div class="text-base mt-4 opacity-75">
GitHub Copilot Study, 2024
</div>

---
layout: default
---

# 🎭 The Paradox of AI Tools

<div class="bg-blue-50 dark:bg-blue-900/20 p-6 rounded-lg mb-6">
<h3 class="text-xl font-bold mb-3">⚡ They seem magical...</h3>
<ul class="space-y-2">
<li>Generate complex code instantly</li>
<li>Answer technical questions fluently</li>
<li>Debug issues you've been stuck on</li>
</ul>
</div>

<div class="bg-red-50 dark:bg-red-900/20 p-6 rounded-lg">
<h3 class="text-xl font-bold mb-3">⚠️ But also fail mysteriously...</h3>
<ul class="space-y-2">
<li>Confidently write broken code</li>
<li>Invent APIs that don't exist</li>
<li>Miss obvious bugs</li>
</ul>
</div>

---
layout: two-cols
---

# 🔍 Real Developer Scenarios

**Scenario 1: The Hallucinated API**
```typescript
// AI suggests:
import { useAutoSave } from 'vue'
// This doesn't exist! 🚫
```

**Scenario 2: The Outdated Pattern**
```vue
// AI generates Vue 2 syntax
export default {
  data() { return { count: 0 } }
}
// When you need Vue 3 Composition API
```

::right::

**Scenario 3: The Confident Bug**
```javascript
// AI's "optimized" solution
const sorted = arr.sort()
// Mutates original array! 🐛
```

**Scenario 4: The Context Loss**
```typescript
// After 100 lines of context...
// AI forgets your TypeScript strictness
let user = getUserData()
// Missing type annotations
```

---
layout: center
---

# 🧩 The Core Insight

<div class="text-2xl font-bold text-center mb-8">
LLMs don't understand — they <span class="text-blue-500">predict patterns</span>
</div>

<div class="text-lg space-y-4">

- No true comprehension of code logic
- No ability to actually run or test code
- No understanding of cause and effect
- Just **extremely good pattern matching**

</div>

---
layout: default
---

# 💰 Why This Matters for Your Career

<div class="grid grid-cols-2 gap-6">

<div class="bg-green-50 dark:bg-green-900/20 p-5 rounded-lg">
<h3 class="font-bold text-lg mb-3">✅ Skills that increase in value</h3>
<ul class="text-sm space-y-2">
<li>Prompt engineering</li>
<li>AI tool integration</li>
<li>Understanding AI limitations</li>
<li>Human-AI collaboration</li>
</ul>
</div>

<div class="bg-yellow-50 dark:bg-yellow-900/20 p-5 rounded-lg">
<h3 class="font-bold text-lg mb-3">⚡ New opportunities</h3>
<ul class="text-sm space-y-2">
<li>AI-augmented development</li>
<li>Custom AI tool creation</li>
<li>AI safety and testing</li>
<li>Hybrid workflows design</li>
</ul>
</div>

</div>

---
layout: statement
---

# Understanding how LLMs work
## makes you a better developer
### in the AI age

---
layout: default
---

# 🎯 What You'll Master Today

<div class="space-y-6">

<div class="flex items-start gap-4">
<div class="text-3xl">🔤</div>
<div>
<h3 class="font-bold text-lg">Tokenization & Embeddings</h3>
<p class="text-gray-600 dark:text-gray-400">How text becomes numbers and meaning</p>
</div>
</div>

<div class="flex items-start gap-4">
<div class="text-3xl">⚙️</div>
<div>
<h3 class="font-bold text-lg">Transformer Architecture</h3>
<p class="text-gray-600 dark:text-gray-400">The attention mechanism that powers modern AI</p>
</div>
</div>

<div class="flex items-start gap-4">
<div class="text-3xl">⚠️</div>
<div>
<h3 class="font-bold text-lg">Failure Modes & Solutions</h3>
<p class="text-gray-600 dark:text-gray-400">Why AI fails and how to work around it</p>
</div>
</div>

<div class="flex items-start gap-4">
<div class="text-3xl">🛠️</div>
<div>
<h3 class="font-bold text-lg">Practical Applications</h3>
<p class="text-gray-600 dark:text-gray-400">Tools and techniques for real development</p>
</div>
</div>

</div>
