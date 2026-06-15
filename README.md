# 🎮 Game Glitch Investigator: The Impossible Guesser

## 🚨 The Situation

You asked an AI to build a simple "Number Guessing Game" using Streamlit.
It wrote the code, ran away, and now the game is unplayable. 

- You can't win.
- The hints lie to you.
- The secret number seems to have commitment issues.

## 🛠️ Setup

1. Install dependencies: `pip install -r requirements.txt`
2. Run the broken app: `python -m streamlit run app.py`

## 🕵️‍♂️ Your Mission

1. **Play the game.** Open the "Developer Debug Info" tab in the app to see the secret number. Try to win.
2. **Find the State Bug.** Why does the secret number change every time you click "Submit"? Ask ChatGPT: *"How do I keep a variable from resetting in Streamlit when I click a button?"*
3. **Fix the Logic.** The hints ("Higher/Lower") are wrong. Fix them.
4. **Refactor & Test.** - Move the logic into `logic_utils.py`.
   - Run `pytest` in your terminal.
   - Keep fixing until all tests pass!

## 📝 Document Your Experience

- [X] Describe the game's purpose.
      The game is a number guessing game built with Streamlit. The player chooses a difficulty, guesses the secret number, and uses the game’s “Too High” or “Too Low” hints to narrow down the answer before running out of attempts.
- [X] Detail which bugs you found.
      I found that changing the difficulty did not always create a secret number in the correct range. The New Game button did not fully reset the game because some session state values, like score, were not cleared. The Submit Guess button also behaved strangely because the secret number was converted to a string on even-numbered attempts. The attempts display was also shown before the submit logic ran, so it looked like the click count was behind.
- [X] Explain what fixes you applied.
      I updated the game so the secret number is generated using the selected difficulty’s range. I added a shared reset function that resets attempts, secret number, score, status, and history for both New Game and difficulty changes. I removed the odd/even secret-number conversion so guesses are always compared against an integer. I also moved the attempts/debug display after the submit logic and kept the debug window expanded after each rerun.

## 📸 Demo Walkthrough

Describe your fixed game in numbered steps so a reader can follow along without watching a video:

1. User selects a difficulty, and the game creates a secret number in that difficulty’s range.
2. Score and attempts update correctly after each guess.
3. User continues guessing until they enter the correct number.
4. Game returns “Correct!” and shows the final score.
5. User clicks “New Game” to reset the secret number, attempts, score, and history.

**Screenshot** *(optional)*: <!-- Insert a screenshot of your fixed, winning game here -->

## 🧪 Test Results

```
# Paste your pytest output here, e.g.:
# pytest tests/
# ========================= X passed in 0.XXs =========================
```

## 🚀 Stretch Features

- [ ] [If you choose to complete Challenge 4, describe the Enhanced UI changes here — a screenshot is optional]
