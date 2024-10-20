# Wordle Python Recreation

This repository contains a Python implementation of the popular word-guessing game, Wordle. The game challenges players to guess a secret five-letter word within six attempts, providing feedback for each guess in the form of colored emojis.

## Features

- **User Input:** Players enter their guesses through the command line.
- **Feedback System:** The game provides visual feedback using emojis:
  - 🟩 (Green Box) for correct letters in the correct position.
  - 🟨 (Yellow Box) for correct letters in the wrong position.
  - ⬜ (White Box) for incorrect letters.
- **Input Validation:** Ensures that guesses are the correct length and contains valid characters.

## How to Run

1. Clone this repository to your local machine.
2. Make sure you have Python 3 installed.
3. Run the `wordle.py` script.

```bash
python wordle.py
```

4. Follow the prompts to play the game.

## Customization

- You can change the secret word by modifying the `main` function's `secret` parameter in `wordle.py`.

## Contributing

Feel free to fork the repository, submit issues, or create pull requests if you have suggestions or enhancements!
