## Trainer Notes

### Common Issues

- **Part 1:** Participants often expect code to have fewer tokens than prose. Point out that special characters (brackets, semicolons, arrows) each count as tokens and inflate the count significantly for code.

- **Part 2:** Some newer models (GPT-4o, Claude Sonnet) are better at refusing hallucinations. If the model self-corrects, that's a great teachable moment — discuss what improved and why.

- **Part 3:** Use a real-world codebase snippet for maximum effect. The longer the file, the more dramatic the result.

- **Part 4:** The instruction interference result varies by model. Claude tends to honor system-level constraints better than ChatGPT in some scenarios. If the model resists switching, celebrate it — it shows strong instruction following — and ask the group what architectural choices might make a model more or less susceptible.

### Discussion Points

- Why do you think the tokenizer splits `Vue.js` into 4 tokens instead of 1?
- What are the implications of hallucination for code review workflows when using AI assistance?
- How would you design a production prompt to minimize primacy/recency bias?

### Time Estimates

- Fast participants: 15 min
- Average: 20 min
- With group discussion: 30–40 min
