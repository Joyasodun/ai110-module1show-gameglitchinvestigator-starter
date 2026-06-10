# 💭 Reflection: Game Glitch Investigator

Answer each question in 3 to 5 sentences. Be specific and honest about what actually happened while you worked. This is about your process, not trying to sound perfect.

## 1. What was broken when you started?

The first time I ran the game it looked playable, but it broke as soon as I started interacting with it. The very first guess could crash the whole app with a Python error, the attempt counter never matched how many guesses I had actually made, the score went down even when I won, and once a game ended the "New Game" button refused to start a fresh round.

Concrete bugs I noticed at the start:

- **The game crashed on a guess.** I expected to see a "Go HIGHER/LOWER" hint, but instead the app threw a `TypeError` because the secret number was being compared against text on some attempts.
- **The attempts counter was off by one.** I expected "Attempts left" to drop to the correct number after each guess, but it always showed one more attempt than I really had.
- **The score punished me even when I won.** I expected winning to raise my score, but I kept ending games with a lower or negative score, and "too high" guesses sometimes added points and sometimes subtracted them.
- **New Game was broken.** I expected the "New Game" button to start a fresh round, but after winning or losing it would show the "game over" message instead of letting me play, and old guesses stayed in the history.

**Bug Reproduction Log**

Document at least 3 bugs you found. Add rows as needed.

| Input | Expected Behavior | Actual Behavior | Console Output / Error |
|-------|-------------------|-----------------|------------------------|
| Guess of `50` on the 2nd attempt (Normal difficulty) | A "Go HIGHER!" or "Go LOWER!" hint is shown | App crashed and stopped responding | `TypeError: '>' not supported between instances of 'int' and 'str'` (app.py line 36) |
| Submit one guess, then read "Attempts left" vs. the debug "Attempts" value | After 1 guess on Normal (limit 8), it should read "Attempts left: 7" | It read "Attempts left: 8" — one more than I actually had | none |
| Win the game on attempt 3 after a few wrong guesses | Final score should go up for winning | Final score ended low / negative even though I won | none |
| Win or lose a game, then click "New Game 🔁" | A fresh round starts so I can guess again | "You already won / Game over" message appeared and the input was blocked; old guesses still showed in History | none |

---

## 2. How did you use AI as a teammate?

- Which AI tools did you use on this project (for example: ChatGPT, Gemini, Copilot)?
- Give one example of an AI suggestion that was correct (including what the AI suggested and how you verified the result).
- Give one example of an AI suggestion that was incorrect or misleading (including what the AI suggested and how you verified the result).

---

## 3. Debugging and testing your fixes

- How did you decide whether a bug was really fixed?
- Describe at least one test you ran (manual or using pytest)  
  and what it showed you about your code.
- Did AI help you design or understand any tests? How?

---

## 4. What did you learn about Streamlit and state?

- How would you explain Streamlit "reruns" and session state to a friend who has never used Streamlit?

---

## 5. Looking ahead: your developer habits

- What is one habit or strategy from this project that you want to reuse in future labs or projects?
  - This could be a testing habit, a prompting strategy, or a way you used Git.
- What is one thing you would do differently next time you work with AI on a coding task?
- In one or two sentences, describe how this project changed the way you think about AI generated code.
