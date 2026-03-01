## Overview

In this task you will directly observe the mechanics you just learned — tokenization, hallucination, context loss, and instruction interference — using real AI tools.

## Prerequisites

- Access to ChatGPT, Claude, or any chat-based LLM
- Access to the [OpenAI Tokenizer](https://platform.openai.com/tokenizer)

---

## Part 1: Tokenization Explorer (5 min)

Open the [OpenAI Tokenizer](https://platform.openai.com/tokenizer) and paste each of the following strings. Note the token count.

1. `Hello world`
2. `const sortedArray = array.sort((a, b) => a - b);`
3. A 50-word paragraph of plain English text
4. The same paragraph in another language (e.g. German or Japanese)

**Reflection questions:**

- Which input used the most tokens per character?
- What would this mean for your context budget when sending code to an LLM?

---

## Part 2: Trigger a Hallucination (5 min)

Ask your LLM assistant:

> "Show me how to use the `useReactiveQuery` function from Vue 3."

This function does not exist. Observe whether the model:

- Invents a plausible implementation
- Provides fake documentation links
- Admits it doesn't know

Then ask:

> "Please verify that `useReactiveQuery` is an official Vue 3 API."

**Reflection:** Did the model self-correct, double down, or hedge?

---

## Part 3: Recreate Lost in the Middle (5 min)

Paste a large block of code (200+ lines) into your LLM and add a specific constraint somewhere in the middle:

> "Important: The function must return `null` instead of throwing an error."

Then ask the model to refactor the code. Check whether it respected the constraint.

**Follow-up:** Move the constraint to the very start of the prompt. Does the model respect it now?

---

## Part 4: Instruction Interference (5 min)

1. Start a new conversation with this system prompt (or first message):

   > "You are a Vue 3 expert. Always use the Composition API with TypeScript."

2. Then send:

   > "Write a simple counter component in React."

**Observe:** Does the model follow the initial constraint or switch to React?

**Mitigation:** Repeat your constraint at the end of the message and try again.

---

## Success Criteria

- [ ] You identified a tokenization pattern that surprised you
- [ ] You triggered a hallucination and observed the model's behavior
- [ ] You reproduced the "lost in the middle" phenomenon at least once
- [ ] You observed instruction interference and successfully mitigated it with constraint repetition
