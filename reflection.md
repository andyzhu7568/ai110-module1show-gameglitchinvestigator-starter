# 💭 Reflection: Game Glitch Investigator

Answer each question in 3 to 5 sentences. Be specific and honest about what actually happened while you worked. This is about your process, not trying to sound perfect.

## 1. What was broken when you started?

- What did the game look like the first time you ran it? Looks like deliberately making mistakes for us to find 
- List at least two concrete bugs you noticed at the start  
  (for example: "the hints were backwards").
  1. Reset button is broken. 2, Game mode (Easy/Medium/hard)is broken

**Bug Reproduction Log**

Document at least 3 bugs you found. Add rows as needed.

| Input      | Expected Behavior  | Actual Behavior | Console Output / Error |
|------------|-------------------------------------------------------------------------------|-----------------|------------------------|
|Select Easy/Hard |'Guess a number between 1 and 100' changes to 'Guess a number between 1 and 20' or 'Guess a number between 1 and 50'|Does not change. |
| Click Submit Guess Button| Each click count as 1 guess and log in History | Needs to click twice to log the input | |
| Click New Game Button | After previous Game over, click New Game button should reset the game| Does not reset the game | |

---

## 2. How did you use AI as a teammate?

- Which AI tools did you use on this project (for example: ChatGPT, Gemini, Copilot)? ChatGPT
- Give one example of an AI suggestion that was correct (including what the AI suggested and how you verified the result).
   after game over, clicking New Game can create a new secret and set status back to "playing", but the old score remains. That makes the game look partially stuck or not fully restarted.
   if new_game:
    st.session_state.attempts = 0
    st.session_state.secret = random.randint(low, high)
    st.session_state.score = 0
    st.session_state.status = "playing"
    st.session_state.history = []
    st.rerun()
   A cleaner version would be to create a helper function like reset_game() so difficulty changes and the New Game button use the exact same reset logic. That avoids future bugs where one reset path clears something and another forgets it.
- Give one example of an AI suggestion that was incorrect or misleading (including what the AI suggested and how you verified the result).
  N/A. AI Got them all right!

---

## 3. Debugging and testing your fixes

- How did you decide whether a bug was really fixed?
  Retest the process to verify if the same bug still exist.
- Describe at least one test you ran (manual or using pytest)  
  and what it showed you about your code.
  Test the New Game button after game over
- Did AI help you design or understand any tests? How?
  Yes, by explain the logic and provide with suggestions on how to modify it.

---

## 4. What did you learn about Streamlit and state?

- How would you explain Streamlit "reruns" and session state to a friend who has never used Streamlit?
  Streamlit reruns mean that every time the user clicks a button, types in an input, or changes a dropdown, Streamlit runs the whole Python file again from top to bottom. This can be surprising because normal variables get recreated during each rerun, so they do not automatically remember old values. st.session_state is Streamlit’s way to remember information between reruns, like the secret number, score, attempts, or whether the game is over. I would explain it like this: the script redraws the page every time something happens, but session_state is the notebook where Streamlit keeps the important game data from one redraw to the next.
---

## 5. Looking ahead: your developer habits

- What is one habit or strategy from this project that you want to reuse in future labs or projects?
  - This could be a testing habit, a prompting strategy, or a way you used Git.
- What is one thing you would do differently next time you work with AI on a coding task?
- In one or two sentences, describe how this project changed the way you think about AI generated code.
