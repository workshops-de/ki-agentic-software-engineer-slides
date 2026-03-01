---
layout: section
---

# How LLMs Work

A practical introduction for software developers

---
layout: why
---

# Why do LLMs fail us unexpectedly?

We use AI tools daily — yet they confidently produce wrong code, hallucinate APIs, and ignore context.

- Knowing the mechanics lets you write prompts that actually work
- Debugging AI output becomes systematic instead of guesswork
- Designing reliable AI workflows requires knowing the failure modes
- The gap between "magical" and "unreliable" is mechanical, not random

---
layout: two-cols-header
layoutClass: gap-4
---

# When AI fails: Real developer scenarios

::left::

**Hallucinated API**

<WindowMockup codeblock title="suggestion.ts">

```typescript
import { useAutoSave } from 'vue';
// This package doesn't exist
```

</WindowMockup>

**Outdated pattern**

<WindowMockup codeblock title="component.vue">

```vue
export default { data() { return { count: 0 } } } // Vue 3 Composition API ignored
```

</WindowMockup>

::right::

**Confident bug**

<WindowMockup codeblock title="sort.js">

```javascript
const sorted = arr.sort();
// Mutates the original array
```

</WindowMockup>

**Context loss**

<WindowMockup codeblock title="fetch.ts">

```typescript
// After 100 lines of conversation...
let user = getUserData();
// TypeScript types forgotten
```

</WindowMockup>

---
layout: little-what
---

# An LLM doesn't "understand" code — it predicts the next most probable token, one step at a time.

---
layout: default
---

# What you'll understand today

- **Tokenization** — how text becomes numbers the model can process
- **Embeddings** — how tokens carry meaning as geometry
- **Transformer architecture** — how attention connects tokens
- **Failure modes** — where and why LLMs go wrong
- **Practical mitigations** — how to work around known limitations
