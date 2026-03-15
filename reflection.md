# 💭 Reflection: Game Glitch Investigator

Answer each question in 3 to 5 sentences. Be specific and honest about what actually happened while you worked. This is about your process, not trying to sound perfect.

## 1. What was broken when you started?

- What did the game look like the first time you ran it?
- List at least two concrete bugs you noticed at the start  
  (for example: "the hints were backwards").

---

Bug 1 — Higher/Lower Hint is Reversed
Expected: When the guess is too low, it says "Go HIGHER," and when the guess is too high, it says "Go LOWER."
What happened: The hints were completely flipped — when the guess is too low it says "Go HIGHER" and when the guess is too high it says "Go LOWER."

Bug 2 - Sidebar and Game Info Are Out of Sync
Expected: The range and number of attempts shown in the sidebar and the banner right under Make a Guess should match.
What happened: The banner always shows "Guess a number between 1 and 100" regardless of difficulty, and the attempts left is already off by 1 at the start of the game.

Bug 3 - Score Increases on Wrong Guesses
Expected: Only correct guesses earn points; wrong guesses deduct points.
What happended: "Too High" guessses on even attempts added 5 points instead of subtracting, rewarding wrong answers.

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
