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

- Q1 Which AI tools did you use on this project (for example: ChatGPT, Gemini, Copilot)?
  A1: Claude

Q2 Give one example of an AI suggestion that was correct (including what the AI suggested and how you verified the result).
A2:AI suggestion: "The hint messages are swapped. When the guess is too high, the player should be told to go lower, and vice versa. The bug exists in both branches of check_guess. Fixing both:"
How I verified: I reviewed suggested edits in both branches of check_guess and confirmed the updated logic matched what I expected - when the guess is too low, it says "Go HIGHER," and when the guess is too high it returns "Go LOWER.". I then accepted the edits and replayed the game to confirm the hints were correct.

Q3 Give one example of an AI suggestion that was incorrect or misleading (including what the AI suggested and how you verified the result).
A3:During my first attempt at this project in class, I described the bug to AI in plain English without first adding a # FIXME comment or locating the exact problematic lines myself. Without precise context, AI made broader changes than necessary and accidentally broke the originally working session_state.history feature. I verified this by running the live game and noticing the guess history was no longer being tracked correctly. This taught me to always locate and mark the exact bug location first before asking AI to fix it, so the AI's changes are targeted and don't accidentally affect unrelated working code.

---

## 3. Debugging and testing your fixes

Q1: How did you decide whether a bug was really fixed?
A1: I verified each fix in two ways: first by running pytest to confirm the expected outputs matched, then by running the live game with streamlit run app.py and manually testing the same scenarios to confirm the behavior was correct in the actual UI.

Q2: Describe at least one test you ran (manual or using pytest) and what it showed you about your code.
A2: I ran check_guess(60, 50) which should return ("Too High", "📉 Go LOWER!"). Before the fix, the hint was reversed and would have returned "Go HIGHER." After the fix, the test passed, confirming that the hint logic in check_guess was correctly repaired. I also ran update_score(0, "Too High", 2) which confirmed it now returns -5 instead of +5, verifying that "Too High" guesses on even attempts no longer incorrectly reward points.

Q3: Did AI help you design or understand any tests? How?
A3: Yes — I specified the exact inputs and expected outputs for all 5 test cases based on my understanding of the bugs I fixed, then asked Claude in VS Code to generate the pytest code for them. Claude wrote the test functions in test_game_logic.py importing from logic_utils.py. I reviewed the generated code to confirm it matched my specifications, then ran pytest to verify all 5 tests passed.

---

## 4. What did you learn about Streamlit and state?

Q1: How would you explain Streamlit "reruns" and session state to a friend who has never used Streamlit?
A1: Every interaction (button clicks, text input, selectbox changes) triggers a full script re-run, but st.session_state (e.g. secret, attempts, score, status, history) persists across these — so you guard initial values with if "key" not in st.session_state to set them only once.

## 5. Looking ahead: your developer habits

Q1: What is one habit or strategy from this project that you want to reuse in future labs or projects?- This could be a testing habit, a prompting strategy, or a way you used Git.
A1: When refactoring across multiple files, I want to keep using Plan mode in VS Code with manual approval per file. By choosing "Yes, and manually approve edits" at the plan stage and then "Yes" (not "Yes, allow all edits this session") for each individual file write, I stay in full control of every change Claude makes — reviewing each file's diff before it gets written. This prevents Claude from making unexpected changes across files all at once, which could introduce new bugs that are hard to trace back.

Q2: What is one thing you would do differently next time you work with AI on a coding task?
A2: I would add # FIXME comments before asking AI for help, rather than describing the bug in plain text alone. Marking the exact location in the code first gives the AI more precise context and leads to more targeted fixes with fewer unnecessary changes to other parts of the code.

Q3 In one or two sentences, describe how this project changed the way you think about AI generated code.
A3: This project taught me to use AI as a tool to accelerate my work rather than blindly trust it — I provide the logical thinking (identifying where the bug is, defining the expected inputs and outputs), and AI handles the mechanical writing. I also learned to always carefully review and test AI-suggested changes before accepting them, since AI can produce code that looks correct but contains subtle logic errors. Additionally, AI proved to be a valuable tool for understanding complex codebases, helping me trace through unfamiliar logic step by step.
