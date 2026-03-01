<details>
<summary>💡 Hint 1: Triggering a hallucination</summary>

Ask about a function that sounds like it _should_ exist but doesn't. Combining a real framework name with a plausible-sounding feature name works well. The model is more likely to hallucinate when the question is highly specific.

</details>

<details>
<summary>💡 Hint 2: Lost in the Middle</summary>

Try placing a unique keyword (like `CONSTRAINT_MARKER`) in the middle of a long prompt, then ask the model to include it in its response. If it doesn't appear, the middle content was effectively ignored.

</details>

<details>
<summary>💡 Hint 3: Instruction Interference mitigation</summary>

Repeat the critical constraint both at the start _and_ end of your prompt. You can also use stronger phrasing like `"IMPORTANT: Do not use React under any circumstances."` and observe the difference.

</details>
