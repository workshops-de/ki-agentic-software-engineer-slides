## Preface

We are not looking for the cleanest solution in this task; the goal is to get familiar with Cursor as a tool. Improve your prompting and review generated results carefully.

## Ask for a prompt

- Before implementing a new feature, take a step back.
- You might know that vague prompts lead to strange results.
- Writing a detailed prompt can be challenging.
- Recent models can reason about good prompts themselves and do part of the groundwork for you.

- Open a new chat in Cursor:
  - `CMD` / `Windows`–`SHIFT`–`P`
  - Type `Open Chat`
  - Press `ENTER`
- Switch to Cursor’s **Ask** mode and ask for a prompt that should cause the **Agent** to implement the feature to display the details of a book.

![](https://cdn.workshops.de/system/images/60/medium.png?v=63924578065)

## Compare different models

- Try at least two different Claude models and compare the prompts.
- You can open a new chat tab to try another model.
- Decide which prompt you will use with the Agent.

![](https://cdn.workshops.de/system/images/62/medium.png?v=63924578396)

## Let the Agent handle your prompt

- In your chat, switch to **Agent** mode and let Cursor implement the feature.
- Look at the code changes.
- Review each change and accept, improve, or reject it.
- Verify the changes by running the app in the browser.

![](https://cdn.workshops.de/system/images/61/medium.png?v=63924578334)

## Success criteria

- [ ] You used Ask mode to obtain at least one strong implementation prompt for book details.
- [ ] You compared prompts from at least two Claude models and picked one for the Agent.
- [ ] You ran the Agent, reviewed diffs deliberately, and verified the feature in the browser.
